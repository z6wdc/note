---
title: NumPy log1p
date: 2021-07-23T11:52:40+09:00
tags: ["NumPy"]
---
[lop1p](https://numpy.org/doc/stable/reference/generated/numpy.log1p.html)

去除偏態的時候

可以利用的函數 `log1p`

```python
df['Fare'] = np.log1p(df['Fare'])
```

必須注意的是代入的值必須大於等於 0
