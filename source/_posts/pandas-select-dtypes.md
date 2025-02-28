---
title: pandas select_dtypes
date: 2021-09-12T23:04:13+09:00
tags: ["pandas"]
---
[select_dtypes](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.select_dtypes.html) 可以對你的 column 做 filter

包含 `float64` 類別

```python
df.select_dtypes(include=['float64'])
```

排除 `int64` 類別

```python
df.select_dtypes(exclude=['int64'])
```
