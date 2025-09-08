---
title: Escape Analysis
date: 2025-09-07 00:12:30
tags: ['Go']
---
## 什麼是 Escape Analysis
Escape Analysis（逃逸分析）是 Go 編譯器在 **編譯時期** 的最佳化判斷

用來決定變數要配置在 **stack** 還是 **heap**

- **stack**：生命週期隨函式結束自動釋放，效能好，不需要 GC
- **heap**：需要垃圾回收（GC），成本較高，但可以讓物件跨函式或 goroutine 存活

編譯器會在編譯時期就決定變數的位置，不會「先放 stack，執行中再搬去 heap」

## 什麼情況會逃逸到 Heap

**返回區域變數的指標**
```go
   func foo() *int {
       x := 10
       return &x // x 會逃逸
   }
```

## 如何檢查 Escape Analysis
使用編譯選項：
```bash
go build -gcflags -m=2
```

## 範例
https://github.com/z6wdc/go-escape-analysis
