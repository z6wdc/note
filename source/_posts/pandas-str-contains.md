---
title: pandas str.contains
date: 2021-07-19T11:54:59+09:00
tags: ["pandas"]
---
[str.contains](https://pandas.pydata.org/docs/reference/api/pandas.Series.str.contains.html)

檢查 `Series` 裡面有沒有包含特定字串

```python
s.str.contains('text')
```

想要忽略大小寫的時候

可以把 `case` 設定成 `False` 預設為 `True`

```python
s.str.contains('og', case=False)
```
