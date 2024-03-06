---
title: pandas shape
date: 2021-06-24T17:41:34+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---
想知道 `DataFrame` 有幾個 row 跟 columns 的時候

可以使用 `shape`

```python
df.shape
```

如果只想知道 row 或是 column 分別個數時

後頭加上 index 0 或 1

就可以分別取得 row 跟 column 的個數

## row

```python
df.shape[0]
```

## column

```python
df.shape[1]
```
