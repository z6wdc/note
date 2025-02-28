---
title: pip install
date: 2021-06-28T22:09:40+09:00
tags: ["Python"]
---
[pip install](https://pip.pypa.io/en/stable/cli/pip_install/#)

這個可以說是最常用的指令之一

在一些 command 中可以看到一些加上 option 的用法

其實最簡單查詢每個 option 的方法就是利用 `-h`

## -h

```bash
pip install -h
```

就會把 option 都列出來給你看了

而之中常用的有

## -r

-r, --requirement <file> 

Install from the given requirements file. 

This option can be used multiple times.

關於 requirements file 的格式

可以參考[這裡](https://pip.pypa.io/en/stable/cli/pip_install/#example-requirements-file)

## -U

-U, --upgrade

Upgrade all specified packages to the newest available version.

The handling of dependencies depends on the upgrade-strategy used.
