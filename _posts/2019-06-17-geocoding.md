---
layout: post
title: 住所から緯度経度を取得する
tags: [berry, linux, geocoder]
---

住所から緯度経度を取得する方法。

## rubyのgeocoderを使う

```
# gem install geocoder
require 'geocoder'
# 日本語ロケールに設定
Geocoder.configure(:language=>:ja, :units=>:km)
r =Geocoder.address("東京タワー")
# => "日本, 〒105-0011 東京都港区芝公園４丁目４−２−８ 東京タワー"
puts r

r =Geocoder.search("東京タワー")
puts r
puts r.first.coordinates
```

## 参照

- http://kamoland.com/wiki/wiki.cgi?SQLite%A4%C7%B4%CA%B0%D7%A5%EA%A5%D0%A1%BC%A5%B9%A5%B8%A5%AA%A5%B3%A1%BC%A5%C0
- http://demouth.hatenablog.com/entry/2014/02/03/073304
- https://atyks.hateblo.jp/entry/2016/07/01/000000
