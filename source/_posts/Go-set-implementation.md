---
title: Go set implementation
date: 2025-02-27 09:21:33
tags: ["Go"]
---
Golang 沒有內建的 `set`，但可以使用 `map` 來模擬 `set`，
通常使用 `map[T]struct{}` 來實現，因為 `struct{}` 不會佔用額外的記憶體。

```go
package main

import "fmt"

func main() {
    // 使用 map[T]struct{} 模擬 Set
    set := make(map[string]struct{})

    // 新增元素
    set["apple"] = struct{}{}
    set["banana"] = struct{}{}
    set["orange"] = struct{}{}

    // 檢查元素是否存在
    if _, exists := set["banana"]; exists {
        fmt.Println("香蕉存在於 set 中")
    }

    // 刪除元素
    delete(set, "banana")

    // 遍歷 Set
    fmt.Println("Set 的內容：")
    for item := range set {
        fmt.Println(item)
    }
}
```
