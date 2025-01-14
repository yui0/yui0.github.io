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

2. **独自SSL (無料) を設定**
  * 🛡️ URLのSSL化は忘れずに。

3. **MySQL データベースを作成**
  * ⚡ MySQLを使用するなら、ロリポップの管理画面で、データベースを作成する。
    * ユーザ名、パスワード、データベース名、サーバー名を記録しておく。

4. **ZIP ファイルを展開**
  * 📂 ロリポップのフォルダに先程のZIPファイルをアップロードして展開します。
  * 例: `web/[URL]/` 以下に展開。

5. **ブラウザでセットアップ**
  * 🌐 例えば、web/[URL]/なら`https://[URL]/nextcloud` にアクセスしてインストールを進める。

## 💡 トラブルシューティング Tips

### 🛠️ ファイルエントリーの再構築 (MySQL 操作)
* ストレージ内のファイルエントリーを再構築したい。(mysql)
データベースの `oc_filecache` テーブルを削除して再構築する:
```sql
DELETE FROM oc_filecache;
```

### 🔄 ファイルが認識されない場合
次のコマンドでスキャン＆クリーンアップ:
```bash
cd web/[URL]/nextcloud
php8.2 occ files:scan --all
php8.2 occ files:cleanup
```

## 📚 参考リンク

* 📖 [Nextcloud 警告についての記事](https://www.digitalboo.net/post/6601/xserver-nextcloud-warning)

これでNextcloudをスムーズにインストールできるはずです！ 🚀
