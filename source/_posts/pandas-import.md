---
title: pandas import
date: 2021-06-05T13:01:27+09:00
categories: ["zh-Hant-TW"]
tags: ["pandas"]
---

## import

```python
import pandas as pd
```

在 import `pandas` 的時候

幾乎都會使用 `pd` 這個縮寫

另外因為 `Series` `DataFrame` 很常用

如果覺得每次使用都要用 `pd` 去呼叫很麻煩的話

```python
pd.Series()
pd.DataFrame()
```

可以直接 import 進來

就可以直接使用了

```python
from pandas import Series, DataFrame
```
