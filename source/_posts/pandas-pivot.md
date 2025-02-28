---
title: pandas pivot
date: 2021-07-20T17:08:05+09:00
tags: ["pandas"]
---
[pivot](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.pivot.html)

可以拿來做樞紐轉換

使用時會指定下列的值

`index`

`columns`

`values`

```python
df.pivot(index='foo', columns='bar', values='baz')
```
