---
title: BigQuery SELECT * EXCEPT
date: 2021-07-06T10:48:47+09:00
categories: ["zh-Hant-TW"]
tags: ["Google Cloud Platform","Big Query"]
---
[SELECT * EXCEPT](https://cloud.google.com/bigquery/docs/reference/standard-sql/query-syntax#select_except)

`SELECT * EXCEPT` 可以在 select 全部的時候

指定要除去哪一個特定的 column

```sql
WITH orders AS
  (SELECT 5 as order_id,
  "sprocket" as item_name,
  200 as quantity)
SELECT * EXCEPT (order_id)
FROM orders;

+-----------+----------+
| item_name | quantity |
+-----------+----------+
| sprocket  | 200      |
+-----------+----------+
```
