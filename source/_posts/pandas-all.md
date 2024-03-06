---
title: pandas all
date: 2021-07-23T23:35:26+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---
[all()](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.all.html)

確認所有的值是不是都為 `True`

不是的話就是 `False`

```python
pd.Series([True, True]).all()
# True

pd.Series([True, False]).all()
# False
```
