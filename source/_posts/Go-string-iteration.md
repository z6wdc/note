---
title: Go string iteration
date: 2025-02-27 18:19:55
tags: ["Go"]
---
在 Golang 中，`text[i]` 和 `for _, v := range text` 會以不同方式處理 `string`，特別是在處理 Unicode 字元時

## 1. `text[i]` 取得 `byte`
- **類型**：`byte`（`uint8`）
- **適用於**：ASCII 字元（英文、數字）
- **問題**：對於 Unicode 字元（如中文、日文），`text[i]` 只會取得 **單一 byte**，可能導致錯誤

### **範例**
```go
package main

import "fmt"

func main() {
    text := "你好"
    fmt.Printf("text[0] 的類型: %T, 值: %v\n", text[0], text[0])
}
```

### **輸出**
```
text[0] 的類型: uint8, 值: 228
```

這是因為「你」的 UTF-8 編碼是 **三個 byte**（228, 189, 160），但 `text[0]` 只取第一個 byte（`228`），導致錯誤

## 2. `for _, v := range text` 遍歷 `rune`
- **類型**：`rune`（`int32`）
- **適用於**：任何字元（包括 ASCII 和 Unicode）
- **優勢**：完整取得 Unicode 字元，不會拆開多 byte 的字符

### **範例**
```go
package main

import "fmt"

func main() {
    text := "你好"
    for _, v := range text {
        fmt.Printf("值: %v, 類型: %T, 對應字元: %c\n", v, v, v)
    }
}
```

### **輸出**
```
值: 20320, 類型: int32, 對應字元: 你
值: 22909, 類型: int32, 對應字元: 好
```

這裡 `20320` 和 `22909` 是 Unicode code point，對應「你」和「好」

## 3. 總結

如果確定是 ASCII 字元（如 `abc`），`text[i]` 可用

如果字串包含 Unicode（如「你好」），使用 `for range` 來確保正確解析

當不確定字串內容時，使用 `for range` 來處理 `rune`，以避免編碼問題
