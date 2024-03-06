---
title: Python str.strip
date: 2021-07-15T08:19:03+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[strip()](https://docs.python.org/3/library/stdtypes.html?#str.strip)

strip() 可以用來刪除字串前後的字元

```python
'www.example.com'.strip('cmowz.')
# 'example'
```

也可以用來刪除空白或是換行記號

預設值是刪除空白所以不用輸入參數

```python
' example '.strip()
# 'example'
```

```python
'\nexample\n'.strip('\n')
# 'example'
```

## lstrip()

[lstrip()](https://docs.python.org/3/library/stdtypes.html?#str.lstrip)

`lstrip()` 只會刪除左邊的字元

```python
'www.example.com'.lstrip('cmowz.')
# 'example.com'
```

## rstrip()

[rstrip()](https://docs.python.org/3/library/stdtypes.html?#str.lstrip)

`rstrip()` 只會刪除右邊的字元

```python
'mississippi'.rstrip('ipz')
# 'mississ'
```
