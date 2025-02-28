---
title: pandas groupby
date: 2021-06-30T00:22:58+09:00
tags: ["pandas"]
---
[groupby](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.groupby.html)

`groupby` 用來對資料做集結

```python
df.groupby('column1').sum()
```

也可對複數個 column 做集結

```python
df.groupby(['column1','column2']).sum()
```

集結後也可以指定對哪個 column 做處理

```python
df.groupby('column1').sum()['column2']
```

也可以指定複數個 column

```python
df.groupby('column1').sum()[['column2','column3']]
```

不指定的話，就是對 column1 以外的 column 做處理

關於處理，也可以同時指定多個

例如同時使用 `count` `sum` `max` `min`

```python
df.groupby('column1').agg(['count','sum','max','min'])['column2']
```
