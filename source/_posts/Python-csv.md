---
title: Python csv
date: 2021-08-01T10:08:10+09:00
tags: ["Python"]
---
[csv](https://docs.python.org/3/library/csv.html?highlight=csv#module-csv)

可以用 `csv` 這個 module 來讀取跟寫入

## csv.reader

讀取範例

```python
import csv
with open('some.csv', newline='') as f:
    reader = csv.reader(f)
    for row in reader:
        print(row)
```

指定 `newline=''` 會比較安全

這樣 `csv` 就會處理每個平台上的 newline

## csv.writer

```python
import csv
with open('some.csv', 'w', newline='') as f:
    writer = csv.writer(f)
    writer.writerows(someiterable)
```

## Dialects and Formatting Parameters

可以透過參數來讀取不同類型的 csv file

```python
import csv
with open('passwd', newline='') as f:
    reader = csv.reader(f, delimiter=':', quoting=csv.QUOTE_NONE)
    for row in reader:
        print(row)
```
