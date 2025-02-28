---
title: Python xmltodict
date: 2021-08-01T10:39:39+09:00
tags: ["Python"]
---
[xmltodict](https://github.com/martinblech/xmltodict#readme)

這是一個可以把 xml 轉成 dict 的 module

`xmltodict.parse` 的 [return value](https://github.com/martinblech/xmltodict/blob/ae19c452ca000bf243bfc16274c060bf3bf7cf51/xmltodict.py#L198) 會是 `OrderedDict`

```python
import xmltodict

with open('sample.xml') as fd:
    doc = xmltodict.parse(fd.read())
```
