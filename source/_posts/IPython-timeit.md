---
title: "IPython timeit"
date: 2022-10-31T11:41:14+09:00
categories: ["zh-Hant-TW"]
tags: ["IPython"]
---
[%timeit](https://ipython.readthedocs.io/en/stable/interactive/magics.html#magic-timeit)

可以利用 `%timeit` 來看 line 的執行時間

```python
%timeit college.loc[cn, 'UGDS_WHITE']
```

如果要看 cell 的執行時間可以利用 `%%timeit`

```python
%%timeit
row_num = college.index.get_loc(cn)
col_num = college.columns.get_loc('UGDS_WHITE')
row_num, col_num
```

還可以利用 `-r` 跟 `-n` 來決定 repeat 次數跟 number 大小
