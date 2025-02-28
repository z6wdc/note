---
title: Python int()
date: 2021-05-07T01:02:43+09:00
tags: ["Python"]
---
Python Built-in Function 的 [int()](https://docs.python.org/3/library/functions.html#int)

## Example 1

可以把 `str` 轉換成 `int`

```python
int('29')
```

Output

```bash
29
```

## Example 2

可以把 `float` 轉換成 `int`
轉換的時候，會直接捨去小數點後的部分

```python
int(3.14)
```

```python
int(7.0)
```

Output

```bash
3
```

```bash
7
```
