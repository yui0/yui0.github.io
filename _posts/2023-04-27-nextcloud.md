---
layout: post
title: 🌐 レンタルサーバーにNextcloudをインストールする方法
tags: [lolipop,server,nextcloud]
---

ロリポップのレンタルサーバーでNextcloudを導入する手順を解説します！

- 💡 **注意**
  - Nextcloudを26にしたところ、あちこちで不具合が発生し、使い物にならなくなりました。
  - 24に戻したところ使えるようになったので、この記事では24を使用します。
  - ※その後クライアントアプリがなぜか使えなくなりました。
  - Nextcloud27とPHP8.2モジュールに変更したところ復活しました。

## 🖥️ ダウンロード

* **Nextcloud 24 をダウンロード**
  * 📥 [Download Nextcloud 24.0.12](https://download.nextcloud.com/server/releases/nextcloud-24.0.12.zip)  
  * 📄 [公式の変更履歴はこちら](https://nextcloud.com/changelog-unsupported/)

## ⚙️ インストール手順

1. **WAF (Web Application Firewall) を無効化**(重要!)
  * 🔒 *セキュリティ設定を見直して有効化も検討してください。*

* 使うURLの独自SSL（無料）を設定しておく。
* MySQLを使用するなら、ロリポップの管理画面で、データベースを作成する。
  * ユーザ名、パスワード、データベース名、サーバー名を記録しておく。
* ロリポップのフォルダに先程のZIPファイルを展開する。
  * 例えば、web/[URL]/以下に展開。
* ブラウザからアクセスする。
  * 例えば、web/[URL]/ならhttps://[URL]/nextcloud

## Tips

* ストレージ内のファイルエントリーを再構築したい。(mysql)
```
DELETE FROM oc_filecache;
```

* ファイルが認識しなくなった。
```
cd web/[URL]/nextcloud
php8.2 occ files:scan --all
php8.2 occ files:cleanup
```

## ref.

* https://www.digitalboo.net/post/6601/xserver-nextcloud-warning
