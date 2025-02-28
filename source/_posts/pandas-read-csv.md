---
title: pandas read_csv
date: 2021-07-23T21:39:10+09:00
tags: ["pandas"]
---
[read_csv()](https://pandas.pydata.org/docs/reference/api/pandas.read_csv.html)

通常會是使用 `pandas` 的第一行

最簡單的使用方式

```python
pd.read_csv('data/movie.csv')
```

不過讀進來的時候

還有很多參數可以設定

## index_col

```python
pd.read_csv('data/movie.csv', index_col='movie_title')
```

指定 col 當作 index
