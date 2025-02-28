---
title: pandas index
date: 2021-07-21T16:14:02+09:00
tags: ["pandas"]
---
[index](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.Index.html)

`index` 有下列的 subclass

- RangeIndex

- CategoricalIndex

- MultiIndex

- IntervalIndex

- DatetimeIndex

- TimedeltaIndex

- PeriodIndex

- Int64Index

- UInt64Index

- Float64Index

## values

`values` 會回傳 `NumPy` n-dimensional array（ndarray）

```python
index.values
# array([   0,    1,    2, ..., 4913, 4914, 4915])
```
