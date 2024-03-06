---
title: pandas qcut
date: 2021-07-20T16:20:36+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---
[qcut](https://pandas.pydata.org/docs/reference/api/pandas.qcut.html)

`qcut` 可以用 quantile 來把資料分成 n 組區間

做 Decile rank 的時候很方便

```python
df['Decile_rank'] = pd.qcut(df['Score'], 10)
```
