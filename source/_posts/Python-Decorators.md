---
title: Python Decorators
date: 2021-07-16T08:19:13+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[Decorators](https://www.python.org/dev/peps/pep-0318/#examples)

可以用來修飾 `class` 跟 `function`

`function` 的範例如下

```python
def decorator_sample(func):
    def inner1(*args, **kwargs):
          
        print("before Execution")          
        returned_value = func(*args, **kwargs)
        print("after Execution")
          
        return returned_value
          
    return inner1
    
@decorator_sample
def sum_two_numbers(a, b):
    print("Inside the function")
    return a + b
  
print("Sum =", sum_two_numbers(1, 2))


"""
before Execution
Inside the function
after Execution
Sum = 3
"""
```
