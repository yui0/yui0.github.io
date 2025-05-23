---
layout: post
title: Firefox 52以降でALSAを使う
tags: [berry, linux]
---

## apulseを使う

- [https://github.com/i-rinat/apulse](https://github.com/i-rinat/apulse) からダウンロードし、インストールする。
  - [https://github.com/yui0/apulse/releases/](https://github.com/yui0/apulse/releases/) にBerry Linux 64 bit (Fedora 25)のRPMがある。
  - それだけでFirefoxがALSAに対応する。
  - pulseaudioを通さなくなるので、音がよくなる。

## Firefox 54以降の注意点

- 54以降で[サンドボックスのエラー](https://github.com/i-rinat/apulse/issues/54)が出る。
  - 対策は、下記の通り。
  - open("/dev/snd/controlC0", O_RDWR) is blocked by sandbox. workaround: set security.sandbox.content.write_path_whitelist to /dev/snd/controlC0,/dev/snd/pcmC0D0p.
  - Firefoxの「about:config」に「security.sandbox.content.write_path_whitelist」を作成し「/dev/snd/controlC0,/dev/snd/pcmC0D0p」を追加。

## Firefox 57以降の注意点

- 57以降で[サンドボックスのエラー](https://artixlinux.org/forum/index.php?topic=87.0)が再び出る。
  - Firefoxの「about:config」に「security.sandbox.content.write_path_whitelist」を作成し「/dev/snd/」を追加。(最後の/が大事)

## Firefox 58以降の注意点

- 58以降で[サンドボックスのエラー](https://github.com/i-rinat/apulse/commit/d86760b225cc44d07fa12662519f4d8bbcdb3679)が再び出る。
  - Firefoxの「about:config」に「security.sandbox.content.syscall_whitelist」を作成し「16」を追加。(64bit版の場合。32bitやARMは54)
