---
layout: post
title: 住所から緯度経度を取得する
tags: [berry, linux, geocoder]
---

住所から緯度経度を取得する方法。

## WebAPIを使う(Python)

```geocoding.py
# pip3 install requests bs4 tqdm lxml

import requests
from bs4 import BeautifulSoup
import time
from tqdm import tqdm

def get_lat_lon_from_address(address_l):
    """
    address_lにlistの形で住所を入れてあげると、latlonsという入れ子上のリストで緯度経度のリストを返す関数。
    >>>>get_lat_lon_from_address(['東京都文京区本郷7-3-1','東京都文京区湯島３丁目３０−１'])
    [['35.712056', '139.762775'], ['35.707771', '139.768205']]
    """
    url = 'http://www.geocoding.jp/api/'
    latlons = []
    for address in tqdm(address_l):
        payload = {'q': address}
        r = requests.get(url, params=payload)
        ret = BeautifulSoup(r.content,'lxml')
        if ret.find('error'):
            raise ValueError(f"Invalid address submitted. {address}")
        else:
            lat = ret.find('lat').string
            lon = ret.find('lng').string
            latlons.append([lat,lon])
            time.sleep(10)
    return latlons

latlons = get_lat_lon_from_address(['東京都文京区本郷7-3-1','東京都文京区湯島３丁目３０−１']);
print(latlons);
```

## WebAPIを使う(Ruby)

```geocoding.rb
require 'net/http'
require 'uri'
require 'json'

## gem install nokogiri
#require 'nokogiri'
require "rexml/document"

#require "csv"

def get_json(location,limit=10)

    raise ArgumentError, 'too many HTTP redirects' if limit == 0
    uri = URI.parse(location)
    begin
        response = Net::HTTP.start(uri.host,uri.port,use_ssl:uri.scheme=='https') do |http|
            http.open_timeout = 5
            http.read_timeout = 10
            http.get(uri.request_uri)
        end
        case response
        when Net::HTTPSuccess
            json = response.body
            JSON.parse(json)
        when Net::Redirection
            location = response['loaction']
            warn "Redirected to #{location}"
            get_json(location,limit-1)
        else
            puts [uri.to_s,response.value].join(':')
        end
    rescue => e
        puts [uri.to_s,e.class,e]
    end
end

def get_xml(location,limit=10)

    raise ArgumentError, 'too many HTTP redirects' if limit == 0
    uri = URI.parse(location)
    begin
        response = Net::HTTP.start(uri.host,uri.port,use_ssl:uri.scheme=='https') do |http|
            http.open_timeout = 5
            http.read_timeout = 10
            http.get(uri.request_uri)
        end
        case response
        when Net::HTTPSuccess
            xml = response.body
            #Nokogiri::XML(xml)
            doc = REXML::Document.new(xml)
        when Net::Redirection
            location = response['loaction']
            warn "Redirected to #{location}"
            get_xml(location,limit-1)
        else
            puts [uri.to_s,response.value].join(':')
        end
    rescue => e
        puts [uri.to_s,e.class,e]
    end
end

puts get_xml(URI.encode('http://newspat.csis.u-tokyo.ac.jp/cgi-bin/simple_geocode.cgi?addr=東京都港区芝公園４丁目４−２−８'))

doc = get_xml(URI.encode('http://newspat.csis.u-tokyo.ac.jp/cgi-bin/simple_geocode.cgi?addr=東京都港区芝公園４丁目４−２−８'))
puts doc.elements["/results/candidate/longitude"].text
```

## rubyのgeocoderを使う

```
# gem install geocoder
require 'geocoder'
# 日本語ロケールに設定
Geocoder.configure(:language=>:ja, :units=>:km)
#Geocoder.configure(:language  => :ja,  :units => :km, :lookup => :google)
r =Geocoder.address("東京タワー")
# => "日本, 〒105-0011 東京都港区芝公園４丁目４−２−８ 東京タワー"
puts r

r =Geocoder.search("東京タワー")
puts r
puts r.first.coordinates
```

## 参照

- [住所（市区町村番地）から緯度経度を取得する](https://qiita.com/laqiiz/items/842fe2a32e80bac92364)
- http://kamoland.com/wiki/wiki.cgi?SQLite%A4%C7%B4%CA%B0%D7%A5%EA%A5%D0%A1%BC%A5%B9%A5%B8%A5%AA%A5%B3%A1%BC%A5%C0
- http://demouth.hatenablog.com/entry/2014/02/03/073304
- https://atyks.hateblo.jp/entry/2016/07/01/000000
