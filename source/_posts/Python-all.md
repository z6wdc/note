---
title: Python all
date: 2021-07-26T21:43:05+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
Python Built-in Function 的 [all()](https://docs.python.org/3/library/functions.html#all)

確認所有的值是不是都為 `True`

不是的話就是 `False`

```python
print(all([True, True, True]))
# True

print(all([True, False, True]))
# False
```
