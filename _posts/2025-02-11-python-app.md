---
layout: post
title: 🐍 PythonでAndroid & iOSアプリを作成する📱
tags: [python,android,ios,app,berry,linux,fedora]
---

### 🛠 必要なもの
✅ **Java**

✅ **Android SDK**

✅ **Android NDK**

### 🔧 インストール手順
以下のコマンドを実行して必要なツールをインストールします💡

```sh
pip install kivy cython python-for-android
pip install git+https://github.com/kivy/buildozer.git
pip install --upgrade buildozer python-for-android
dnf install java-17-openjdk-devel
```

⚠ **注意点**
🚨 **Javaのバージョン**が最新だとエラーになる可能性があります。

⚠ **Cython**も特定のバージョンを指定しないとエラーが発生することがあります。

### 📝 テストプログラム

#### 1️⃣ **Buildozerの初期化**
```sh
buildozer init
```

#### 2️⃣ **アプリのPythonコード (`main.py`)**
```python
import kivy

from kivy.app import App
from kivy.uix.label import Label

class MyApp(App):
    def build(self):
        return Label(text='🐱 Rcat APP!')

if __name__ == '__main__':
    MyApp().run()
```

#### 3️⃣ **セットアップファイル (`setup.py`)**
```python
from setuptools import setup

setup(
    name='myapp',
    version='0.1',
    install_requires=[
        'kivy',
        'other_dependencies'
    ],
)
```

### 🚀 実行 & デバッグ
```sh
buildozer -v android debug
buildozer android debug deploy run logcat
```

これで**PythonでAndroidアプリを作成＆実行**できます！💪🔥
