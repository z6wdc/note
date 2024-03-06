---
title: Python re search vs match
date: 2021-07-14T01:00:37+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[`search` vs `match`](https://docs.python.org/3/library/re.html#search-vs-match)

在 Python 中

`re.search()` 會找目標文字中第一個出現的字串

`re.match()` 只會找目標文字中最初出現的字串

```python
import re

re.match("c", "abcdef") # No match
re.search("c", "abcdef") # Match
```
