---
title: pandas get_dummies
date: 2021-07-23T18:56:04+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---
[get_dummies()](https://pandas.pydata.org/docs/reference/api/pandas.get_dummies.html)

處理類別型的資料時

如果想要做 One Hot Encoding 的處理

可以利用 `get_dummies()`

```python
s = pd.Series(list('abca'))
pd.get_dummies(s)

"""
   a  b  c
0  1  0  0
1  0  1  0
2  0  0  1
3  1  0  0
"""
```
