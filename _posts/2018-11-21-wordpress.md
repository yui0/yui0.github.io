---
layout: post
title: WordPressを使う
tags: [wordpress,blog]
---

WordPressを使えるようにする。

## 必要なもの

- サーバー
  - PHP
  - MySQL(SQliteでも代用できるが、将来性を考えると用意した方がよい)
  - ドメイン(あった方がよい)

## WordPressのインストール

- WordPressのホームページからファイルをダウンロードする。
  - [https://ja.wordpress.org/download/](https://ja.wordpress.org/download/)
  - ダウンロードしたら展開し、サーバーにファイルをそのまま置く。
- もしくはレンタルサーバーの簡単インストールを使う。
- WordPressを置いたURLにブラウザーからアクセスし、初期設定をする。

## オススメのテーマ

- 外観→テーマ→新規 でZIPファイルのままインストールする。
- [Cocoon](https://wp-cocoon.com/downloads/)
  - 子テーマもダウンロードする。
- [Luxeritas](https://thk.kanzae.net/wp/dl/)
  - 子テーマもダウンロードする。

## Markdown記法で投稿できるようにする

- WordPressにプラグインを入れる。
1. プラグイン＞新規追加からプラグインを検索。(markdownとかで検索)
2. 「Markdown Editer」をみつけてインストール。
3. インストールが完了したら有効化する。
