---
title: pandas count
date: 2021-07-21T22:45:46+09:00
tags: ["pandas"]
---
[count](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.count.html)

用來計算 non-missing values 的個數

```python
s = pd.Series([0.0, 1.0, np.nan])
s.count()
# 2
```

np.nan 不會被 `count` 計算進去
