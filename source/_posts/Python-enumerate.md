---
title: Python enumerate
date: 2021-08-19T00:38:58+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[enumerate](https://docs.python.org/3/library/functions.html#enumerate)

## enumerate(iterable, start=0)

對 list 做迴圈時

可以用 `enumerate` 來獲取 index 值

還可以用 `start` 來指定 index 起始值

```python
seasons = ['Spring', 'Summer', 'Fall', 'Winter']

for index, season in enumerate(seasons):
    print(index, season)

for index, season in enumerate(seasons, start=1):
    print(index, season)
```
