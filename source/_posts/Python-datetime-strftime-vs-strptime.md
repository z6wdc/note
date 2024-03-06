---
title: Python datetime strftime vs strptime
date: 2021-09-17T11:05:55+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
## strftime

[strftime](https://docs.python.org/3/library/datetime.html#datetime.datetime.strftime)

`strftime` 可以把 `datetime` object 透過指定的 format

轉換成 string

```python
from datetime import datetime

now = datetime.now()

year = now.strftime("%Y")
print("year:", year)
```

## strptime

[strptime](https://docs.python.org/3/library/datetime.html#datetime.datetime.strptime)

`strptime` 可以把字串轉換成 date object

使用時必須指定字串的 format

```python
from datetime import datetime

date_string = "25 July, 2021"

date_object = datetime.strptime(date_string, "%d %B, %Y")
```

## strftime() and strptime() Behavior

[behavior](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-behavior)

兩者主要的差異

一個從 object 轉成 string

一個從 string 轉成 object

## format

關於 format 要怎麼指定

可以參考官方的 [Format Codes](https://docs.python.org/3/library/datetime.html#strftime-and-strptime-format-codes)
