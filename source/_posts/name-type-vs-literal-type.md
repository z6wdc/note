---
title: name type vs literal type
date: 2025-08-30 01:22:16
tags: ['Go']
---
## 1. Name type
- 編譯器會將其視為**獨立且唯一的型別**。  
- 即使底層結構（struct）相同，若名稱不同，也不能直接賦值。  
- 這樣的限制可以避免不同語意的資料被錯誤混用。  

## 2. Literal type
- 編譯器會直接檢查結構內容。  
- 只要兩個型別的結構完全相同且相容，就允許賦值。  
- 沒有嚴格的名稱限制，因此更靈活，但語意安全性較低。  

## 結論
- **Name type** 強調**語意安全（semantic safety）** → 保護程式邏輯正確性。  
- **Literal type** 強調**結構相容性（structural compatibility）** → 提供更多彈性。  

## Go 範例程式碼

```go
package main

import "fmt"

// Name type 定義
type Person struct {
    Name string
    Age  int
}

type Employee struct {
    Name string
    Age  int
}

func main() {
    // 兩個不同的 name type，即使結構相同，也不能直接賦值
    var p Person
    var e Employee
    // p = e // 編譯錯誤: cannot use e (variable of type Employee) as Person value

    // Literal type (匿名 struct)
    var n struct {
        Name string
        Age  int
    }
    var m struct {
        Name string
        Age  int
    }

    // 兩個 literal type，結構相同，所以可以直接賦值
    n = m
    fmt.Println(n, m)
}
```
