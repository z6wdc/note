---
title: sklearn LabelEncoder
date: 2021-07-23T14:33:30+09:00
tags: ["sklearn"]
---
[LabelEncoder](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.LabelEncoder.html)

處理類別型的資料時

可以用的方法

```python
from sklearn.preprocessing import LabelEncoder

df[c] = LabelEncoder().fit_transform(df[c])
```
