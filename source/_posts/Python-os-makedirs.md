---
title: Python os makedirs
date: 2021-09-11T01:40:29+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[os.makedirs](https://docs.python.org/3/library/os.html#os.makedirs)

可以用來建立新的 directory

```python
os.makedirs('path/dir')
```

如果指定的 path 上面 directory 已經存在的話

會跳出 `FileExistsError`

但可以指定 `exist_ok` 為 `True`

```python
os.makedirs('path/dir', exist_ok=True)
```
