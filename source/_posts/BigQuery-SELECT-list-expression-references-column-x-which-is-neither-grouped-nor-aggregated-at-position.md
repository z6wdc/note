---
title: Big Query SELECT list expression references column x which is neither grouped nor aggregated at [position]
date: 2021-05-05T19:05:52+09:00
tags: ["Google Cloud Platform","Big Query"]
---
當我們使用 `GROUP BY` 的時候  
就有機會看到這 error message
SELECT list expression references column x which is neither grouped nor aggregated at [position]

原因之一是 `SELECT` 到沒有 `GROUP BY` 的 column

### normal case

```sql
SELECT product_id, SUM(quantity)
FROM pruduct
GROUP BY product_id
```

### error case 1

```sql
SELECT product_id, is_sale, SUM(quantity)
FROM pruduct
GROUP BY product_id
```

error case 1 中  
`SELECT` 了 `is_sale` 這個 column  
但並沒有對 `is_sale` 做 `GROUP BY`  
就會顯示 error message  
SELECT list expression references column `is_sale` which is neither grouped nor  aggregated at [position]

### error case 2

```sql
SELECT product_id, quantity
FROM pruduct
GROUP BY product_id
```

error case 2 中  
雖然是忘記對 `quantity` 使用 `SUM`  
但 error message 一樣只會顯示  
沒有對 `quantity` 做 `GROUP BY`  
SELECT list expression references column `quantity` which is neither grouped nor  aggregated at [position]
