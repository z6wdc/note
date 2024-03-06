---
title: SciPy stats boxcox
date: 2021-07-23T11:26:42+09:00
categories: ["zh-Hant-TW"]
tags: ["SciPy"]
---
[boxcox](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.boxcox.html)

去除資料偏態的時候

可以利用的函數 `boxcox`

```python
from scipy import stats
df_fixed['Fare'] = stats.boxcox(df_fixed['Fare'] + 1e-6, lmbda=0.15)
```

使用要必須注意的是

代入 `boxcox` 函數的值不可小於或等於零

在上面例子中加上了一個微小的數字 `1e-6`

目的就是為了不讓值等於 0

## lmbda value

當 `lmbda` 值為特定的數字是

就會是下列的函數

|lmbda|Y|Note|
|:--|:--:|:--|
|-2|1/(Y**2)||
|-1|1/Y|inverse transformation|
|-0.5|1/sqrt(Y)||
|0|logY|logarithmic transformation|
|0.5|sqrt(Y)|square root transformation|
|1|Y|no transformation|
|2|Y**2|quadratic transformation|
