---
title: go table-driven test
date: 2025-05-17 05:45:38
tags: ["Go"]
---
Go 語言中，`table-driven test`（表格驅動測試）是一種非常常見且被推薦的測試寫法。

這種風格強調「資料與邏輯分離」，能讓測試碼更簡潔、可維護性更高，特別適合處理多組輸入/輸出測試案例。

## 為什麼要使用 Table-Driven Test？

當你要針對同一個函式測試多種情境時，若每個情境都手動撰寫重複的 `t.Run(...)`，程式碼會變得冗長、難以維護。使用 table-driven 測試可以：

- 集中維護測試案例
- 自動迴圈跑測試，避免重複程式碼
- 提高可讀性與一致性

## 起源與推廣者

Table-driven test 並不是某個單一開發者發明的設計模式，而是由 Go 核心開發者 **Andrew Gerrand** 在多次演講與部落格中推廣的實踐方式。

> "In Go, we often use table-driven tests. They are a good way to test multiple scenarios without duplicating code."  
> — Andrew Gerrand, Go Developer Advocate

這種風格也出現在 Go 官方標準函式庫的測試檔案中，例如 `strings`, `strconv`, `time` 等，成為 idiomatic Go 的一部分。

## 實作範例：檢查通知類型是否有效

以下是一個簡單的例子：驗證輸入的通知類型是否為 `email`、`push` 或 `sms`。

### 被測試的程式碼（`notification.go`）

```
package notification

func IsValidNotificationType(t string) bool {
    switch t {
    case "email", "push", "sms":
        return true
    default:
        return false
    }
}
```

### 測試檔案（`notification_test.go`）

```
package notification

import "testing"

func TestIsValidNotificationType(t *testing.T) {
    tests := []struct {
        name     string
        input    string
        expected bool
    }{
        {"valid_email", "email", true},
        {"valid_push", "push", true},
        {"valid_sms", "sms", true},
        {"invalid_type", "fax", false},
        {"empty_string", "", false},
    }

    for _, tt := range tests {
        t.Run(tt.name, func(t *testing.T) {
            actual := IsValidNotificationType(tt.input)
            if actual != tt.expected {
                t.Errorf("IsValidNotificationType(%q) = %v; want %v", tt.input, actual, tt.expected)
            }
        })
    }
}
```

## 解說重點

- `tests := []struct{...}`：定義多筆測試資料
- `t.Run(tt.name, ...)`：獨立執行每筆測試並標記名稱（更容易查錯）
- 如果測試失敗，`t.Errorf` 會印出詳細資訊

## 延伸應用

Table-driven 測試也適用於：

- 多種輸入條件組合測試（如邊界值測試）
- 多個子函式共用邏輯測試
- 單元測試與整合測試中的資料組合處理

## 結語

Go 的 table-driven 測試風格簡單易讀、方便維護，是撰寫單元測試的最佳實踐之一。當你在寫測試時遇到需要覆蓋多種條件的情境，請優先考慮這種寫法。

## 參考來源

- Go Wiki - ["Table-Driven Tests"](https://go.dev/wiki/TableDrivenTests)
- Andrew Gerrand, ["Go testing techniques"](https://talks.golang.org/2014/testing.slide)
