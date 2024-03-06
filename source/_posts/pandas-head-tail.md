---
title: pandas head tail
date: 2021-06-29T22:34:25+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---
[head](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.head.html)

[tail](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.tail.html)

`pandas` 可以利用 `head` 跟 `tail` 來取出前幾筆跟後幾筆的資料

如果直接使用，預設會取出前 5 筆跟後 5 筆的資料

```python
df.head()
```

```python
df.tail()
```

也可以指定要取出幾筆資料

例如取出前十筆資料

```python
df.head(10)
```

`head` 跟 `tail` 也可以合併使用

譬如說

```python
df.head(20).tail(10)
```

這樣就會取出前二十筆中最後十筆的資料
