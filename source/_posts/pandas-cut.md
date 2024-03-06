---
title: pandas cut
date: 2021-07-18T08:40:47+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---
[cut](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.cut.html)

把資料分成 n 組區間

n 用 `bins` 來指定

```python
pd.cut(age_data['YEARS_BIRTH'], bins=10)
```

也可以自己指定區間的上下界

```python
cut_rule = [-np.inf, 0, 2, 5, np.inf]

app_train['CNT_CHILDREN_GROUP'] = pd.cut(app_train['CNT_CHILDREN'], cut_rule)
```
