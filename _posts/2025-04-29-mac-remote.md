---
layout: post
title: 🚀 Macをリモートで起動＆画面共有するPythonスクリプト！
tags: [mac.remote,python]
---

このスクリプトは
✅ **リモートでMacを起動（Wake on LAN）**
✅ **起動後に画面共有を開始（VNC接続）** 
するためのものです！

## 📦 必要なライブラリ
```python
import socket  # ネットワーク通信に使う
import struct  # バイナリデータ操作用（今回は使ってないけどよくセットで書かれる）
import os      # Macのアプリを動かすのに使う
```

## ✨ Magic Packetを作成する関数
```python
def make_magic_packet(mac_address):
    mac_bytes = bytes.fromhex(mac_address.replace(':', ''))
    return b'\xff' * 6 + mac_bytes * 16
```
🔹 MACアドレス（例: `00:11:22:33:44:55`）から「**Magic Packet**」を作るよ！
🔹 `\xff` を6回、そのあとMACアドレスを16回繰り返す構成になってるよ。

## 📡 Magic Packetを送信する関数
```python
def send_magic_packet(mac_address, broadcast_ip='255.255.255.255', port=9):
    packet = make_magic_packet(mac_address)
    with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as sock:
        sock.setsockopt(socket.SOL_SOCKET, socket.SO_BROADCAST, 1)
        sock.sendto(packet, (broadcast_ip, port))
    print(f'Magic packet sent to {mac_address}')
```
🔹 UDPでLAN内にMagic Packetをブロードキャスト送信！
🔹 送信先はデフォルトで `255.255.255.255:9`（Wake-on-LANの標準ポート）✨

## 🖥️ 画面共有アプリを起動する関数（Mac専用）
```python
def start_screen_sharing(hostname):
    applescript = f'''
    tell application "Screen Sharing"
        activate
        open location "vnc://{hostname}"
    end tell
    '''
    os.system(f'osascript -e \'{applescript}\'')
```
🔹 Mac標準の「**画面共有**」アプリを起動して、指定のホスト名にVNC接続するよ！
🔹 `hostname`にはMacの名前やIPアドレスを入れるだけ！

## 🛠️ 実際に使ってみよう！

```python
mac_address = '00:11:22:33:44:55'  # 起動したいMacのMACアドレス
hostname = '192.168.1.100'         # または "MacPro" といったホスト名

# ① Magic Packetを送ってMacを起動！
send_magic_packet(mac_address)

# ② 起動後に画面共有で接続！
start_screen_sharing("MacPro")
```

## 🛠️ コード全て

```python
import socket
import struct
import os

def make_magic_packet(mac_address):
    mac_bytes = bytes.fromhex(mac_address.replace(':', ''))
    return b'\xff' * 6 + mac_bytes * 16

def send_magic_packet(mac_address, broadcast_ip='255.255.255.255', port=9):
    packet = make_magic_packet(mac_address)
    with socket.socket(socket.AF_INET, socket.SOCK_DGRAM) as sock:
        sock.setsockopt(socket.SOL_SOCKET, socket.SO_BROADCAST, 1)
        sock.sendto(packet, (broadcast_ip, port))
    print(f'Magic packet sent to {mac_address}')

def start_screen_sharing(hostname):
    applescript = f'''
    tell application "Screen Sharing"
        activate
        open location "vnc://{hostname}"
    end tell
    '''
    os.system(f'osascript -e \'{applescript}\'')

# 使用例
mac_address = '00:11:22:33:44:55'  # 対象のMACアドレス
hostname = '192.168.1.100'  # 対象のMacのIPアドレス

send_magic_packet(mac_address)
#start_screen_sharing(hostname)
start_screen_sharing("MacPro")
```

# 🎯まとめ
- まずMagic Packetを送って💨
- そのあと画面共有で接続🖥️

超シンプルに、リモートからMac操作ができちゃいます！👏
