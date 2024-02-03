---
layout: post
title: ラズパイ4でandroidを使う
tags: [android,raspberry,pi]
---

ラズパイ4でandroidを使えるようにしてみる。
※試した環境が悪いのか、重くて実用的ではなかった。3D系は全く期待できない。

## 必要な物

1. Raspberry Pi 4 Model B
2. OSインストール用のSDカード or USBメモリ(https://gadgetrip.jp/2021/05/raspberry_pi4_usb_boot/)
3. Android13のカスタムROM (https://konstakang.com/devices/rpi4/AOSP13/)
  AOSP13-20220907-KonstaKANG-rpi4.zip
4. GooglePlayストア (https://nikgapps.com/downloads)
  Home / Realeases / NikGapps-T / core
5. Device ID (「このデバイスはGoogleによって認定されていません」修正用)
  https://www.apkmirror.com/apk/evozi/device-id/device-id-1-3-2-release/
6. AnyDesk (リモート操作用)

## OSの書き込み

Raspberry Pi Imager などを使って、SDカードなどに書き込む。

## パーティションの拡張

/dev/sd?4 の userdata パーティションを拡張しておくとよい。

## GooglePlayストアのインストール

Open the “Settings” app.
Go to “System” > “Advanced settings”.
Enable the first option “Reboot to recovery”:

In theory, F5 should work to display this screen, but it doesn’t work anymore once the reboot to recovery is enabled.

Install Google Apps

Click on “Mount”.
This is where you can choose which partition to mount (= making the USB drive accessible).
We need to mount the USB key, so check the USB item in the list.
Then, back on the main menu, click on “Install”.
Click on “Select Storage” and choose the USB key.
Finally, your files appear.
Click on the NikGapps file to install it:

Sign in to the Play Store

GSFコード
https://www.google.com/android/uncertified/

## キーアサイン

F1	F2	F3	F4	F5	F11	F12
ホーム	戻る	マルチタスク	メニュー	電源	音量DOWN	音量UP
