---
title: pandas value_counts
date: 2021-06-25T00:39:13+09:00
tags: ["pandas"]
---
[value_counts](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Series.value_counts.html)

用來計數 `Series` 裡面值出現的次數

```python
s.value_counts()
```

## normalize

`normalize` 設成 True 就會回傳值出現次數佔的比例

```python
s.value_counts(normalize=True)
```

## dropna

`dropna` 設成 False 就會回傳 `NaN` 出現的次數

```python
s.value_counts(dropna=False)
```

## sort

`value_counts` 預設會對出現的次數做排序

可以利用 `sort` 設定成不要排序

```python
s.value_counts(sort=False)
```

## ascending

`value_counts` 預設會對出現的次數做排序

而排序的方式是預設從大排到小

如果想反過來可以設定 `ascending` 為 `True`

```python
s.value_counts(ascending=True)
```
