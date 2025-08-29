---
title: Go variable declaration
date: 2025-08-28 23:21:00
tags: ['Go']
---
# Go 變數宣告

## 1. 基本宣告（指定型別，不給值）
```go
var x int     // x = 0
var s string  // s = ""
var b bool    // b = false
```

## 2. 自動推斷型別（給值，不指定型別）
```go
var x = 10        // int
var s = "hello"   // string
```

## 3. 同時指定型別與初始值
```go
var x int = 10
var s string = "hi"
```

## 4. 短變數宣告（函式內專用）
```go
x := 10
s := "world"
b := true
```

## 5. 多重變數宣告
```go
var a, b, c int           // 全部 int，初始值 0
var x, y = 1, "hello"     // 自動推斷型別
m, n := 10, false         // 短變數宣告
```

## 6. 分組宣告（常用於多個變數）
```go
var (
    a int
    b = "string"
    c bool
)
```
---

# 使用建議：var vs :=
- **用 `var` 的情境：**
  - 需要宣告在函式外（package 層級）
  - 需要指定型別但暫時不賦值
  - 需要保持程式碼一致性（例如團隊規範）

- **用 `:=` 的情境：**
  - 在函式內，想快速宣告並初始化
  - 讓編譯器自動推斷型別即可
  - 更簡潔，Go 程式碼中最常見
