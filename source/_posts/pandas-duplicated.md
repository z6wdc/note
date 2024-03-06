---
title: pandas duplicated
date: 2021-07-20T16:26:06+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---
[duplicated()](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.duplicated.html)

可以用來找重複值

```python
df.duplicated()
```

重複的資料中

第一筆為 False 重複的第二筆開始都會是 True
