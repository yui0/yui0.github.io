---
layout: post
title: Teamviewerの不具合対処方法
---

## 動作環境
 - LinuxのTeamviewer9

## 「Only LAN Connections Possible Problem」
 - メニューの「Extras」→「Options」を選択。
 - 「Network settings」の「Incoming LAN connections」を「accept exclusively」に変更し、「OK」を押す。
 - 再び「Network settings」の「Incoming LAN connections」を「accept」に変更し、「OK」を押す。
 - 何故かTeamviewerのサーバーに認証される。

## 「Connection to...」で止まった場合
 - ps auxで「/opt/teamviewer9/tv_bin/teamviewerd -d」のpidを調べる。
 - kill -KILL pidを実行する。

## Teamviewer 11 on Linuxで「Not Ready...」
 - 原因: rootで実行。
 - 対処: root以外で実行する。
 - su [user] -c teamviewer

		[Desktop Entry]
		Comment[ja]=
		Comment=
		Exec=su berry -c teamviewer
		GenericName[ja]=
		GenericName=
		Icon=web-duolingo
		MimeType=
		Name[ja]=Teamviewer
		Name=Teamviewer
		Path=
		StartupNotify=true
		Terminal=false
		TerminalOptions=
		Type=Application
		X-DBUS-ServiceName=
		X-DBUS-StartupType=
		X-KDE-SubstituteUID=false
		X-KDE-Username=
		Name[ja_JP]=Teamviewer11

## Teamviewer on Linuxがなかなか起動しない
 - 原因: ネット環境の変化に対応できていない。
 - 対処: systemctl restart teamviewerd を実行。
