---
title: pandas dtypes
date: 2021-07-13T12:08:45+09:00
tags: ["pandas"]
---
[dtypes](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.dtypes.html)

`DataFrame` 有 `dtypes` 這個 property

可以用來檢查各個 columns 的型別

```python
df.dtypes
```

而在 `pandas` 有下列的型別

|Common data type name|NumPy/pandas object|Pandas string name|Notes
|--|--|--|--|
|Boolean|np.bool|bool|Stored as a single byte|
|Integer|np.int|int|Defaulted to 64 bits. Unsigned ints are also available - np.uint.|
|Float|np.float|float|Defaulted to 64 bits.|
|Complex|np.complex|complex|Rarely seen in data analysis.|
|Object|np.object|O, object|Typically strings but is a ctach-all for columns with multiple different types or other Python objects(tuples, lists, dicts, and so on).|
|Datetime|np.datetime64, pd.Timestamp|datetime64|Specific moment in time with nanosecond precision.|
|Timedelta|np.timedelta64, pd.Timedelta|timedelta64|An amount of time, from days to nanoseconds.|
|Categorical|pd.Categorical|category|Specific only to pandas. Useful for object columns with relatively few unique values.|
