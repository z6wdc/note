---
title: Python re Match Objects
date: 2021-08-06T08:18:06+09:00
tags: ["Python"]
---
[Match Objects](https://docs.python.org/3/library/re.html#match-objects)

## Match.group

可以利用 `group()` 來列印出匹配的值

index 預設為零

```python
m = re.match(r"(\w+) (\w+)", "Isaac Newton, physicist")

m.group()
# The entire match
# 'Isaac Newton'

m.group(0)
# The entire match
# 'Isaac Newton'

m.group(1)
# The first parenthesized subgroup.
# 'Isaac'

m.group(2)
# The second parenthesized subgroup.
# 'Newton'

m.group(1, 2)
# Multiple arguments give us a tuple.
# ('Isaac', 'Newton')
```

如果正規表達式有設定 `(?P<name>...)` 的 syntax

可以利用 `name` 來指定匹配到的值

```python
m = re.match(r"(?P<first_name>\w+) (?P<last_name>\w+)", "Malcolm Reynolds")

m.group('first_name')
# 'Malcolm'

m.group('last_name')
# 'Reynolds'
```

沒有匹配到的話，就會回傳 `None`

## Match.lastindex

使用 `group()` 的時候

如果代入負數或是大於匹配的結果

會發生 `IndexError`

可以利用 `lastindex` 先找出最大的 index

```python
m = re.match(r"(\w+) (\w+)", "Isaac Newton, physicist")

m.lastindex
# 2
```

## Match.lastgroup

如果正規表達式有設定  `(?P<name>...)` 的 syntax

可以用 `lastgroup` 來找最後一筆匹配的值的 name

## Match.groups

可以利用 `groups()` 來一次列印出匹配的值

```python
m = re.match(r"(\w+) (\w+)", "Isaac Newton, physicist")

m.groups
# ('Isaac', 'Newton')
```

如果沒有成功匹配就會印出 `None`

```python
m = re.match(r"(\d+)\.?(\d+)?", "24")
m.groups()
# Second group defaults to None.
# ('24', None)

m.groups('0')
# Now, the second group defaults to '0'.
# ('24', 0)
```

## Match.groupdict

可以一次列印出設定的 name 與對應的值

```python
m = re.match(r"(?P<first_name>\w+) (?P<last_name>\w+)", "Malcolm Reynolds")

m.groupdict()
# {'first_name': 'Malcolm', 'last_name': 'Reynolds'}
```

如果沒有成功匹配就會印出 `None`

一樣可以設定預設值

```python
m = re.match(r"(?P<first_name>\w+) (?P<last_name>\W+)?", "Malcolm Reynolds")

m.groupdict()
# {'first_name': 'Malcolm', 'last_name': None}

m.groupdict('')
# {'first_name': 'Malcolm', 'last_name': ''}
```
