---
title: Python dict
date: 2021-08-06T15:00:25+09:00
categories: ["zh-Hant-TW"]
tags: ["Python"]
---
[dict](https://docs.python.org/3/library/stdtypes.html#dict)

## items()

會顯示 (key, value)

## keys()

顯示 key

## values()

顯示 value

## get(key[, default])

取得 key 對應的 value

當 key 不在 `dict` 裡面的時候

則回傳 deafult 值

default 值預設為 `None`

所以使用 `get()` 不會發生 `KeyError`

## setdefault(key[, default])

當 key 已經存在 `dict` 裡面

會回傳 key 對應的 value 的值

如果不存在就對 key 設定 default 值

default 值沒設定的話，就會設定成 `None`

所以用來設定值的時候

不會覆蓋原本就已經存在的值

## update([other])

可以更新字典裡面的內容

如果 key/value 已經存在的話

會對已經存在的值做覆寫

`update()` 的參數

可以代入另一個 `dictionary`

或是 `iterable` of `key/value pairs`
