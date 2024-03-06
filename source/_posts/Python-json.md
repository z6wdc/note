---
title: Python json
date: 2021-08-02T18:07:51+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[json](https://docs.python.org/3/library/json.html)

Python 中拿來處理 `json` 的 module

## dump

Serialize obj as a JSON formatted stream to fp

## dumps

Serialize obj to a JSON formatted `str`

```python
import json

json.dumps(['foo', {'bar': ('baz', None, 1.0, 2)}])

# '["foo", {"bar": ["baz", null, 1.0, 2]}]'
```

### ensure_ascii=True

使用 `dump` 跟 `dumps` 的時候

必須注意 `ensure_ascii` 的預設值為 `True`

有時沒有注意這設定的話，會造成亂碼

## load

Deserialize fp to a Python object

## loads

Deserialize `s` to a Python object

```python
import json

json.loads('["foo", {"bar":["baz", null, 1.0, 2]}]')

# ['foo', {'bar': ['baz', None, 1.0, 2]}]
```
