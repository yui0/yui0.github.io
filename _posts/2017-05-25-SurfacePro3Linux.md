---
layout: post
title: Surface Pro 3でLinux
tags: [berry, linux]
---

## カーネルの対応が必要 (4.13.10の時点での説明)

- パッチをあてる (Type Cover)
  - [ms-sp3-multitouch.patch](ms-sp3-multitouch.patch)
  - [ms-sp3-touchscreen_multitouch_fixes1.patch](ms-sp3-touchscreen_multitouch_fixes1.patch)
  - [ms-sp3-touchscreen_multitouch_fixes2.patch](ms-sp3-touchscreen_multitouch_fixes2.patch)
- 必要なコンフィグ
  - CONFIG_HID_MULTITOUCH (Type Cover)
  - CONFIG_SURFACE_PRO3_BUTTON
  - CONFIG_TOUCHSCREEN_SURFACE3_SPI (タッチスクリーン)
    - CONFIG_TOUCHSCREEN_SUR40 (Pro 2の場合)
  - CONFIG_SURFACE3_WMI
  - CONFIG_I2C_DESIGNWARE_CORE (?)
  - CONFIG_I2C_DESIGNWARE_PLATFORM (?)
  - CONFIG_I2C_HID (?)
- ファームウェア (無線LAN)
  - [mrvl](https://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git/commit/)

```bash
$ git clone git://git.marvell.com/mwifiex-firmware.git
# mkdir -p /lib/firmware/mrvl/
# cp mwifiex-firmware/mrvl/* /lib/firmware/mrvl/
```

## Xorgの設定

- /etc/X11/xorg.conf.d/00-surfacepro3-libinput.conf

```/etc/X11/xorg.conf.d/00-surfacepro3-libinput.conf
Section "InputClass"
	Identifier "SP3-keyboard"
	MatchIsKeyboard "on"
	Driver "libinput"
	#Option "XkbLayout" "us,ca"
	Option "XkbOptions" "grp:alt_shift_toggle"
EndSection

Section "InputClass"
	Identifier "SP3-touchpad"
	MatchIsTouchpad "on"
	Driver "libinput"
	Option "Tapping" "on"
EndSection
```
