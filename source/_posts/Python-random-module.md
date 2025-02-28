---
title: Python random module
date: 2021-05-18T22:36:49+09:00
tags: ["Python"]
---
Python 有 random 這個 module  
除了可以產生亂數外，還可以隨機挑選資料  

## How to import

```python
import random
```

## Functions for integers  

### randint

```python
random.randint(0, 100)
```

randint 會隨機從 0 <= n <= 100 的數字隨機挑選一個整數

## Functions for sequences  

### choices

```python
numbers = [1, 2, 3, 4, 5]
random.choices(numbers, k=3)
```

`choices` 會隨機從指定的 list 中重複取出你要的數目

要注意的是指定數目的時候需要寫出 keyword `k`

像是例子中 k=3 就會取出三個

不指定 k 的話，預設值為 1

### sample

```python
numbers = [1, 2, 3, 4, 5]
random.sample(numbers, 3)
```

`sample` 會隨機從指定的 list 中取出你要的數目

而且數字不重複

但要取出的數目不能大於 list 的 length

不然就會發生下面的

`ValueError: Sample larger than population or is negative`
