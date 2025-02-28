---
title: pandas dataframe from_dict
date: 2021-08-29T23:13:12+09:00
tags: ["pandas"]
---
[from_dict](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.from_dict.html)

可以利用 `from_dict` 把 `dictionary` 做成 `dataframe`

```python
data = {'col_1': [3, 2, 1, 0], 'col_2': ['a', 'b', 'c', 'd']}
pd.DataFrame.from_dict(data)
```

而 `dictionary` 的 key 可以當作 column 或是 row 的 name

預設會當做 column 的 name

指定為 row 的方法是指定參數 `orient`

```python
data = {'row_1': [3, 2, 1, 0], 'row_2': ['a', 'b', 'c', 'd']}
pd.DataFrame.from_dict(data, orient='index')
```
