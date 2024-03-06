---
title: Python パッケージ中の main モジュール
date: 2022-12-11T14:48:24+09:00
categories: ["ja"]
tags: ["Python"]
---
## `__main__.py`

パーケージを呼び出す時に、
`-m` オプションを追加することで、
パッケージ中の `__main__.py` モジュールが執行されます。

```shell
python3 -m bandclass
```

```text
bandclass
  ├── __init__.py
  ├── __main__.py
  └── student.py
```

## 参考

https://docs.python.org/3/library/__main__.html#main-py-in-python-packages
