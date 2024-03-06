---
title: pandas isnull
date: 2021-07-01T00:32:27+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---
[isnull()](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.isnull.html)

可以用 `isnull()` 來找出 `NaN` 的值

也可以寫成 `isna()`

```python
df.isnull()
```

也可以和 `any()` 跟 `sum()` 搭配使用

## sum()

可以計算每一個 column 各有幾個 `NaN`

```python
df.isnull().sum()
```

也可以計算每一個 row 各有幾個 `NaN`

```python
df.isnull().sum(axis=1)
```

## any()

用 `any()` 來判斷每一個 column 有沒有 `NaN` 值

```python
df.isnull().any()
```

想要看那一個 row 缺值的話

```python
query = df.isnull().any(axis=1)
df[query].head()
```
