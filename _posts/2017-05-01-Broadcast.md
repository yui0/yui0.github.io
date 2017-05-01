---
layout: post
title: 自宅ネットワークのIPアドレス一覧を確認
---

## pingとarpを使う

```bash
$ ping 192.168.1.255 (ブロードキャストアドレス)
PING 192.168.1.255 (192.168.1.255): 56 data bytes
64 bytes from 192.168.0.1: seq=0 ttl=64 time=2.973 ms
64 bytes from 192.168.0.10: seq=1 ttl=64 time=27.522 ms
^C
--- 192.168.1.255 ping statistics ---

$ arp -a
? (192.168.0.10) at 00:00:00:00:00:00 [ether] on wlan0
local.gateway (192.168.0.1) at 00:00:00:00:00:00 [ether] on wlan0
? (192.168.0.255) at <incomplete> on wlan0
```
