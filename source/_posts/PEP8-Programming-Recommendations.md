---
title: PEP8 Programming Recommendations
date: 2021-08-18T20:43:12+09:00
tags: ["Python"]
---
[Programming Recommendations](https://www.python.org/dev/peps/pep-0008/#programming-recommendations)

## if x

```python
if x:
    # do something
```

```python
if x is not None:
    # do something
```

在某些情況下

上面兩個 condition 不會有一樣的結果

譬如說下面的例子中

```python
x = False
x = ''
x = 0
x = 0.0
x = []
x = ()
x = {}
x = set()
```

`if x` 的結果會是 `Flase`

但 `if x is not None` 會是 `True`
