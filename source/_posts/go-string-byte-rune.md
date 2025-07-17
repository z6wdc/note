---
title: Go 語言中的 string、byte、rune 與 UTF-8 編碼關係整理
date: 2025-07-17 17:48:31
tags: ['Go']
---
在 Go 語言中，字串（`string`）的底層實作是 **UTF-8 編碼的 `[]byte`**。

這帶來了一些重要的性質與操作上的細節。

## 1. string 的底層是 []byte

```go
s := "hello"
b := []byte(s)    // string 轉 []byte
s2 := string(b)   // []byte 轉 string
```

字串可以轉成 byte slice，這對於處理 I/O、檔案、JSON 等操作非常重要。

## 2. UTF-8 是可變長度編碼格式

UTF-8 的設計讓：

- 英文字母（ASCII）只需要 **1 個 byte**
- 常見中文字通常需要 **3 個 byte**
- 有些特殊符號會用到 **4 個 byte**

因此，雖然字串是以 `[]byte` 存的，但「一個字元佔幾個 byte」是不固定的。

## 3. rune 是用來表示「一個 Unicode 字元」

Go 提供了 `rune`（實際上是 int32）來對應 **一個 Unicode code point**，例如：

```go
s := "世界"
runes := []rune(s) // 將每個 Unicode 字元取出
fmt.Println(len(s))     // byte 數量：6（每個中文字是 3 bytes）
fmt.Println(len(runes)) // 字元數量：2（兩個 rune）
```

這解釋了為什麼：

- `len(string)` 得到的是 byte 數量
- `len([]rune(string))` 才是實際的「字數」

## 4. 為什麼要用 rune 存取字元？

因為 UTF-8 是變長編碼，如果你單純用 `[]byte` 存取字串，會遇到「亂碼」或「中斷在半個字」的問題：

```go
s := "世"
fmt.Println(s[0]) // byte 值 228（不是完整字元）
```

所以如果你要處理「一個個字元」，正確的方式是轉成 `[]rune` 再操作。

## 5. 總結

- Go 中的 `string` 是 UTF-8 編碼的 `[]byte`
- 每個 Unicode 字元長度不同，因此不能用 `[]byte[i]` 來當作一個「字」
- `rune` 是對應「一個字元」的單位（int32）
- 如果要逐字處理，應該轉成 `[]rune`
