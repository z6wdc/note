---
title: pandas clip
date: 2021-07-04T15:23:42+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---
[clip()](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.clip.html)

`clip()` 可以對資料重新設定上下界

超過上下界的值

就會各自被設定成上下界的值

```python
df.clip(-4, 6)
```
