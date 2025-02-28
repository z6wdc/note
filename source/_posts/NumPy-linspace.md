---
title: NumPy linspace
date: 2021-07-21T10:19:25+09:00
tags: ["NumPy"]
---
[linspace](https://numpy.org/doc/stable/reference/generated/numpy.linspace.html)

可以利用 `linspace` 來做等距離的 list

```python
np.linspace(2.0, 3.0, num=5)
# array([2.  , 2.25, 2.5 , 2.75, 3.  ])
```

可以利用 `endpoint` 來設定要不要包含尾端值

預設為 `True`

```python
np.linspace(2.0, 3.0, num=5, endpoint=False)
# array([2. ,  2.2,  2.4,  2.6,  2.8])
```
