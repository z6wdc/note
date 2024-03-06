---
title: Python collections defaultdict
date: 2021-07-06T00:01:37+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[defaultdict](https://docs.python.org/3/library/collections.html#defaultdict-objects)

可以用來生成 dictionary

而且還可以設定 value 的預設值

```python
from collections import defaultdict

d = defaultdict(int)
```

上面的例子代入了 `int`

所以 key 預設的值會使用 `int()`

而 `int()` 的結果就會是 0

## lambda

當然也可以不用預設值一定要是 0

用 `lambda` 可以更靈活的設定預設值

```python
from collections import defaultdict

d = defaultdict(lambda: 3)
```
