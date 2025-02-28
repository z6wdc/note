---
title: pandas options
date: 2021-07-18T09:36:07+09:00
tags: ["pandas"]
---
[options](https://pandas.pydata.org/pandas-docs/stable/user_guide/options.html)

`pandas` 的 `DataFrame` 顯示有預設值

要顯示更多時，可以用 `options` 去調整

## set

```python
pd.options.display.max_columns = 30
pd.options.display.max_rows = 100
```

## get

```python
pd.options.display.max_columns
pd.options.display.max_rows
```
