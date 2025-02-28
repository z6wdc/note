---
title: pandas any
date: 2021-07-23T23:42:33+09:00
tags: ["pandas"]
---
[any()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.any.html)

檢查是否有任何一個值為 `True`

全部都是 `False` 的話就為 `False`

```python
pd.Series([False, False]).any()
# False

pd.Series([True, False]).any()
# True
```
