---
title: pandas sort_values
date: 2021-06-28T22:24:52+09:00
tags: ["pandas"]
---
[sort_values()](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.sort_values.html)

想對資料做排序的時候，可以利用 `sort_values()`

## Sort by column

```python
df.sort_values(by='column_name')
```

只要指出要對哪個 column 做排列就可以

要注意的是 `sort_values()`

會回傳一個排序好的 `DataFrame`

而不會去改變原本的排序

## Sort by multiple columns

也可以同時對複數個 column 做排序

```python
df.sort_values(by=['column1', 'column2'])
```

## Sort Descending

另外也可以指定是昇序或是降序

預設會是昇序，所以需要降序的時候再設定就好

```python
df.sort_values(by='column_name', ascending=False)
```

對複數個 column 做排序的時候

也可以分別指定昇序，或是降序

```python
df.sort_values(by=['column1', 'column2'], ascending=[True, False])
```
