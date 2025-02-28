---
title: sklearn train_test_split
date: 2021-07-27T18:54:10+09:00
tags: ["sklearn"]
---
[sklearn.model_selection.train_test_split](https://scikit-learn.org/stable/modules/generated/sklearn.model_selection.train_test_split.html)

`train_test_split` 可以拿來切分訓練集跟測試集

```python
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.33, random_state=42)
```
