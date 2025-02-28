---
title: Python mutable immutable
date: 2021-05-22T08:49:09+09:00
tags: ["Python"]
---
Python 的 [object](https://docs.python.org/3/reference/datamodel.html#objects-values-and-types) 有分成

mutable 跟 immutable 兩種

mutable object 是指

object 的值可以被更改

immutable 則反之

當 object 被 create 之後，值就不能被更改

## mutable example

例如：list, dictionary

### list example

```python
numbers = [1, 2, 3]
numbers[2] = 4
print(numbers)
```

Output

```bash
[1, 2, 4]
```

## immutable example

例如：[numbers](https://docs.python.org/3/library/numbers.html), string, tuple

但 immutable object 還需要注意

值不能被更改的意思

### numbers example

```python
a = 3
print(id(a))
a = 4
print(a)
print(id(a))
```

Output

```bash
4
```

可以看到 a 的值被更改了

但如果用 [id()](https://docs.python.org/3/library/functions.html?highlight=id#id) 把 a 的 address 印出來的話

就會發現 a 的 address 已經改變了

因為 a 是 immutable object

所以對 a 指定新的值的時候

就會被指去新的 address

雖然值更換了，但也不是原本的 object 了

### tuple example

還有另外一個關於 tuple 的例子

雖然 tuple 是 immutable object

但如果 tuple 裡面包含 mutable object

譬如說 list

那在 tuple 裡面的 list 是可以更改值的

```python

t = (1, [1, 2, 3])
t[1][2] = 4
print(t)
```

Output

```bash
(1, [1, 2, 4])
```

但如果想把 tuple 裡面的 list 變成 numbers 的話

```python
t = (1, [1, 2, 3])
t[1] = 2
```

就會跳出下面的 error

`TypeError: 'tuple' object does not support item assignment`
