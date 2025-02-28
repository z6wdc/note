---
title: SQL LIKE
date: 2021-07-20T15:48:47+09:00
tags: ["SQL"]
---
[LIKE](https://dev.mysql.com/doc/refman/8.0/en/pattern-matching.html)

`SQL` 中可以利用 `LIKE` 來對字串做模糊查詢

`%` 表示 0 或任意多個字元

`_` 表示任意一個字元

查詢時預設不會分辨大小寫

```sql
SELECT * FROM pet WHERE name LIKE 'b%'
```

```sql
SELECT * FROM pet WHERE name LIKE '_____'
```

想找指定字串以外的時候

可以用 `NOT LIKE`

```sql
SELECT * FROM pet WHERE name NOT LIKE '_____'
```
