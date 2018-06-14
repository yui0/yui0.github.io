---
layout: post
title: SQLiteで日付の平均を出す
tags: [berry, linux, fedora, sqlite, avg, date]
---

SQLiteで日付の平均を出す方法。

## 「julianday」関数を使う

- avgを使うだけでは日付の平均を出すことはできない。
- それで日付と時刻をユリウス日として取得するjulianday関数を使用する。

```
select id, avg(julianday(edit_date))-min(julianday(edit_date)) from tbl group by id;
```
