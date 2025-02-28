---
title: Python List Comprehension
date: 2021-05-06T20:18:13+09:00
tags: ["Python"]
---
在 Python 中有 [List Comprehension](https://docs.python.org/3/tutorial/datastructures.html?#list-comprehensions) 這個簡潔的 syntax

## The Syntax

```python
newlist = [expression for item in iterable if condition == True]
```

### Example 1

列出從 1 - 10 的偶數

```python
numbers = range(10)
even = [x for x in numbers if x % 2 == 0]

print(even)
```
