---
title: Python Operator precedence
date: 2021-07-25T19:12:48+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[Operator precedence](https://docs.python.org/3/reference/expressions.html#operator-precedence)

Python 中運算子的優先順序

通常為了閱讀方便

都會加上 () 讓人方便理解

不過有些順序還是可以記起來比較方便

## Boolean precedence

|Operator|Description|
|--|--|
|not `x`|Boolean NOT|
|and|Boolean AND|
|or|Boolean OR|

## Comparisons precedence

然後

`Comparisons` 都比 `Boolean` 優先

|Operator|Description|
|--|--|
|in, not in, is, is not, <, <=, >, >=, !=, ==|Comparisons, including membership tests and identity tests|
|not `x`|Boolean NOT|
