---
title: Python any
date: 2021-07-26T21:39:36+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
Python Built-in Function 的 [any()](https://docs.python.org/3/library/functions.html#any)

檢查是否有任何一個值為 `True`

全部都是 `False` 的話就為 `False`

```python
print(any([True, False, False]))
# True

print(any([False, False, False]))
# False
```
