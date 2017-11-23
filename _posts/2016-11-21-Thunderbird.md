---
layout: post
title: LinuxとWindowsでThunderbirdを同期する
tags: [berry, linux, windows]
---

## Dropboxを使う
  - LinuxのThunderbirdの保存フォルダをDropboxに移動する。
    - 具体的には ~/.thunderbird を ~/Dropbox/.thunderbird に移動。
    - それから ln -s ~/Dropbox/.thunderbird ~/.thunderbird を実行。
  - WindowsのC:\Users\[ユーザー名]\AppData\Roaming\Thunderbirdのprofiles.iniを編集。

        [General]
        StartWithLastProfile=1

        [Profile0]
        Name=default
        IsRelative=0
        Path=C:\Users\[ユーザー名]\Dropbox\.thunderbird\[xxxx].default
        Default=1
