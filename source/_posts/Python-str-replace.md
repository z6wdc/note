---
title: Python str.replace
date: 2021-07-10T01:41:40+09:00
tags: ["Python"]
---
[str.replace()](https://docs.python.org/3/library/stdtypes.html#str.replace)

可用來對字串中的字做替換

```python
'target'.replace('t', 'T')
```

沒有指定 `count` 的話，就會對所有字做替換

有指定 `count` 的話

```python
'target'.replace('t', 'T', 1)
```

就只會替換前面 `count` 次的字

另外如果 `count` 設定一個超過目標次數的數值

也不會出現錯誤

```python
'target'.replace('t', 'T', 10)
```
