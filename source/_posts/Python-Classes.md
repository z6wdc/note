---
title: Python Classes
date: 2021-08-18T15:56:26+09:00
tags: ["Python"]
---
[Classes](https://docs.python.org/3/tutorial/classes.html)

## Class and Instance Variables

[Class and Instance Variables](https://docs.python.org/3/tutorial/classes.html#class-and-instance-variables)

### instance variables

每個 `instance` 都會有自己的值

### class variables

會被所有 `class` 的 `instances` 給共有

```python
class Dog:

    kind = 'canine' # class variable shared by all instances

    def __init__(self, name):
        self.name = name # instance variable unique to each instance

d = Dog('Fido')
e = Dog('Buddy')

d.kind # shared by all dogs
# 'canine'

e.kind # shared by all dogs
# 'canine'

d.name # unique to d
#'Fido'

e.name # unique to e
#'Buddy'
```
