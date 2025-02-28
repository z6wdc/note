---
title: Python docstring
date: 2021-06-25T12:05:57+09:00
tags: ["Python"]
---
[docstring](https://www.python.org/dev/peps/pep-0257/#what-is-a-docstring)

Python 的 module, function, class, method 首行加入註解的話

這註解就會是 `docstring`

```python
def example():
    """
    A docstring sample
    """
    return 1

```

在寫 `docstring` 的時候，也有許多 style 可以參考

`pandas` 的 [例子](https://pandas.pydata.org/pandas-docs/stable/development/contributing_docstring.html)
