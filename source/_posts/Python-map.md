---
title: Python map()
date: 2021-05-22T07:09:40+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
我們可以利用

Python Built-in Function 的 [map()](https://docs.python.org/3/library/functions.html#map)

來對 iterable object 做想要的處理

## map()

`map(function, iterable, ...)`

function 就是要對 iterable 使用的函式

回傳值為 map object

### Example 1

```python
list(map(int, ['1', '2', '3']))
```

這個例子中

`map()` 會把 `['1', '2', '3']` 這個 list 裡面的字串當作參數

去使用 `int()` 這個 function

因為 `map()` 回傳值為 map object

最後對回傳值使用 `list()` 可以方便檢查結果

### Example 2

```python
def add(x, y):
    return x + y

list1 = [1, 2, 3]
list2 = [3, 4]

list(map(add, list1, list2))
```

Output

```bash
[4, 6]
```

`map()` 也可以使用自己定義的 function

如果自定義的 function 有兩個參數

後面就必須帶入相對應數量的 iterable

這個例子中為兩個 list

另外當 list 不一樣長的時候

最短的 list 處理完時就會停止

### Example 3

```python
list(map(int, ['10']*10, range(2, 11)))
```

Output

```bash
[2, 3, 4, 5, 6, 7, 8, 9, 10]
```

這個例子中還是使用 `int()`

這次對 `int()` 輸入兩個參數

第一個為要轉換的數字，使用了字串 10

第二個是要轉換的進制

因為是 `range(2, 11)`

所以結果會印出 10 這個數

在 2 進位到 10 進位下的數值
