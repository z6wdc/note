---
title: Python reduce()
date: 2021-10-20T11:30:05+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[reduce](https://docs.python.org/3/library/functools.html#functools.reduce)

`reduce` 也是對 list 每個元素作操作

但 `reduce` 會一次處理前後兩個相鄰的元素

所以 `reduce` 的參數 `function` 必須要有兩個參數

```python
from functools import reduce

print(reduce(lambda x, y: x + y, range(6)))
# 15
```
