---
layout: post
title: レンタルサーバーにNextcloudをインストール
tags: [lolipop,server,nextcloud]
---

レンタルサーバーのロリポップにNextcloudをインストールする方法。

Nextcloudを26にしたところ、あちこちで不具合が発生そし、使い物にならなくなりました。
24に戻したところ使えるようになったので、この記事では24を使用します。

※その後クライアントアプリがなぜか使えなくなりました。
Nextcloud27とPHP8.2モジュールに変更したところ復活しました。

## ダウンロード

* ここから24をダウンロードする。(https://download.nextcloud.com/server/releases/nextcloud-24.0.12.zip)
  * https://nextcloud.com/changelog-unsupported/

## インストール

* 使うURLの独自SSL（無料）を設定しておく。
* MySQLを使用するなら、ロリポップの管理画面で、データベースを作成する。
  * ユーザ名、パスワード、データベース名、サーバー名を記録しておく。
* ロリポップのフォルダに先程のZIPファイルを展開する。
  * 例えば、web/[URL]/以下に展開。
* ブラウザからアクセスする。
  * 例えば、web/[URL]/ならhttps://[URL]/nextcloud

## Tips

* ストレージ内のファイルエントリーを再構築したい。
```
DELETE FROM oc_filecache;
```

* ファイルが認識しなくなった。
```
cd web/[URL]/nextcloud
php8.1 occ files:scan --all
php8.1 occ files:cleanup
```

## ref.

* https://www.digitalboo.net/post/6601/xserver-nextcloud-warning
