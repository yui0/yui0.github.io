---
layout: post
title: Cloudflareで常時HTTPS化
tags: [server, ssl, https, free, cloudflare]
---

Cloudflareを使うと無料でSSLに対応できる。
カスタムドメインなGitHub Pagesサイトも可。
SSL非対応のサーバーでも可。

## 1. Cloudflareのアカウント作成

[Cloudflare](https://www.cloudflare.com/)のサイトに行って「Sign Up」からメアドとパスワードを入力してアカウントを作成。
アカウント作成後に開くページに従い、次のステップをこなす。

## 2. Cloudflareに自分のサイトを登録

サブドメインを除いた自分のドメインを入力して「Begin Scan」をクリック。

## 3. CloudflareのDNSの設定

自分のドメインのDNS設定が自動で読み取られているので、問題がないか確認しDNSの登録を完了する。

## 4. プランの選択

サービスプランは無料のFree Websiteを選択。

## 5. レジストラのネームサーバの変更

最後にレジストラのサイトに行ってネームサーバを変更する。
