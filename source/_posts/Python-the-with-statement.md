---
title: Python the with statement
date: 2021-07-31T13:35:20+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[The with statement](https://docs.python.org/3/reference/compound_stmts.html#the-with-statement)

通常開檔案的時候

會用下列的語法

```python
f = open('sample.txt')
print(type(f))
f.close()
```

但這樣會有一個風險是

如果 `exception` 發生的時候

可能 `f.close()` 就不會執行

比較好的方法是用 `try - except - finally` 來做保護

而使用 `The with statement` 的話就可以直接達到這樣的效果

```python
with open(path) as f:
    print(type(f))
```
