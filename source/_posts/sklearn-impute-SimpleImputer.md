---
title: sklearn impute SimpleImputer
date: 2021-08-10T14:06:21+09:00
tags: ["sklearn"]
---
[sklearn.impute.SimpleImputer](https://scikit-learn.org/stable/modules/generated/sklearn.impute.SimpleImputer.html)

當 data 中有 missing value 的時候

可以利用 `SimpleImputer` 來填補值

```python
imputer = SimpleImputer()
imputed_X_train = pd.DataFrame(imputer.fit_transform(X_train))
```

## Parameters

### strategy

填補值的時候可以選用你想要的方法

```python
imputer = SimpleImputer(strategy='mean')
```

除了 `mean` 以外

還有下面三種

`median`

`most_frequent`

`constant`
