---
title: Python sorting
date: 2021-08-06T14:58:56+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[Sorting HOW TO](https://docs.python.org/3/howto/sorting.html)

## Sorting Basics

要排序時

有 `list.sort()` method 跟 `sorted()` function

`list.sort()` 會直接對 list 做排列，並回傳 `None`

`sorted()` 則是會回傳一個排列好的 `list`

```python
a = [5, 2, 3, 1, 4]
a.sort()
```

```python
sorted([5, 2, 3, 1, 4])
```

另外 `list.sort()` 只能對 `list` 使用

但 `sorted()` 則是可以對 `iterable` 使用

## Key Functions

 `list.sort()` 跟 `sorted()` 都有 key parameter 讓你輸入 function

 做 sort 前，便會用每個 element 去 call 這個 function

```python
student_tuples = [
    ('john', 'A', 15),
    ('jane', 'B', 12),
    ('dave', 'B', 10),
]

sorted(student_tuples, key=lambda student: student[2])
# sort by age
```
