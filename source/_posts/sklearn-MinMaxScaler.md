---
title: sklearn MinMaxScaler
date: 2021-07-25T18:23:58+09:00
tags: ["sklearn"]
---
[MinMaxScaler](https://scikit-learn.org/stable/modules/generated/sklearn.preprocessing.MinMaxScaler.html)

假定數值為均勻分布

適合用最大最小化平衡特徵

因為最大最小化容易受到極端值影響

所以如果資料沒有極端值或是已經去極端值

就適合使用

```python
from sklearn.preprocessing import MinMaxScaler

scaler = MinMaxScaler()
scaler.fit_transform(data)
```
