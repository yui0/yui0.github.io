---
layout: post
title: Fedoraをアップグレードする
tags: [berry, linux, fedora]
---

※必ずバックアップを取って行うこと!
※失敗するとシステムを破壊する可能性あり!

## dnf system-upgradeを使う

- dnf-plugin-system-upgradeをインストール

```bash
# dnf install dnf-plugin-system-upgrade
```

- /etc/yum.repos.d/fedora.repoをアップグレードするリポジトリに変更
- system-upgradeを実行

```bash
# dnf system-upgrade download --releasever=25 --best
```

- /var/lib/dnf/system-upgrade以下にファイルが保存される

## dnfを使う

- /etc/yum.repos.d/fedora.repoをアップグレードするリポジトリに変更

```bash
# dnf update
```

- ダウンロードしたファイルで更新。※毎回かなりの変更があるので、パッケージを注意してすべて入れないとシステムが起動しなくなる
