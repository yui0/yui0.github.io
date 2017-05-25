---
layout: post
title: Surface Pro 3でLinux
---

## カーネルの対応が必要 (4.11.2の時点での説明)

- パッチをあてる (Type Cover)
  - ms-sp3-multitouch.patch
  - ms-sp3-touchscreen_multitouch_fixes1.patch
  - ms-sp3-touchscreen_multitouch_fixes2.patch
- 必要なコンフィグ
  - CONFIG_HID_MULTITOUCH (Type Cover)
  - CONFIG_SURFACE_PRO3_BUTTON
  - CONFIG_TOUCHSCREEN_SURFACE3_SPI (タッチスクリーン)
    - CONFIG_TOUCHSCREEN_SUR40 (Pro 2の場合)
  - CONFIG_SURFACE3_WMI
  - CONFIG_I2C_DESIGNWARE_CORE (?)
  - CONFIG_I2C_DESIGNWARE_PLATFORM (?)
  - CONFIG_I2C_HID (?)
