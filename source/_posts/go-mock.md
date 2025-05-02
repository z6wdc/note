---
title: go mock
date: 2025-05-02 16:31:52
tags: ["Go"]
---
[`uber-go/mock`](https://github.com/uber-go/mock) 是 Uber fork 並維護的 mock 工具

提供自動產生 interface 的 mock 實作與 `gomock` 測試支援，方便我們在單元測試中進行隔離測試與驗證行為。

## 為什麼要用 Mock？

在單元測試中，我們常需要將測試主體與其依賴的資源（如資料庫、API）隔離。使用 mock 有以下好處：

- ✅ 隔離依賴：模擬資料庫、API 等外部系統
- ✅ 驗證行為：確認方法是否被呼叫、呼叫次數與參數
- ✅ 測試例外情況：模擬錯誤回傳以測試錯誤處理邏輯
- ✅ 加速測試：無需啟動真實伺服器或資料庫

## 安裝方式

### 安裝 gomock API（加入 `go.mod`）

```bash
go get go.uber.org/mock@latest
```

這會把 `go.uber.org/mock/gomock` 加入專案依賴中，方便在測試中使用。

### 安裝 mockgen CLI 工具（Go 1.16+）

從 Go 1.16 開始，不再使用 `go get` 安裝 CLI 工具，請使用：

```bash
go install go.uber.org/mock/mockgen@latest
```

安裝後 `mockgen` 會出現在 `$GOBIN`（預設是 `$HOME/go/bin`）目錄下，請確認該路徑已加入 `PATH`。

## 使用範例

### 1. 定義 interface

```go
// internal/domain/user/repository.go
package user

type User struct {
    ID   int
    Name string
}

type UserRepository interface {
    GetByID(id int) (*User, error)
}
```

### 2. 產生 mock（手動）

```bash
mockgen -source=internal/domain/user/repository.go \
  -destination=internal/mocks/user_repository_mock.go \
  -package=mocks
```

#### `-package=mocks` 是什麼？

這個選項指定產生出來的 mock 檔案要屬於哪個 Go 套件。例如：

```go
package mocks
```

這樣你就可以在測試中這樣使用：

```go
import "github.com/your-project/internal/mocks"

mock := mocks.NewMockUserRepository(ctrl)
```

這個 package name 應該與你 mock 檔案放置的目錄一致（如 `internal/mocks/`），否則會導致 import 錯誤。

### 3. 使用 go generate（推薦）

在 interface 定義的檔案上方加註：

```go
//go:generate mockgen -source=repository.go -destination=../../mocks/user_repository_mock.go -package=mocks
```

然後執行：

```bash
go generate ./...
```

這樣日後只要執行一次 `go generate` 就能統一更新所有 mock。

### 4. 測試中使用 mock

```go
// internal/usecase/user_usecase_test.go
package usecase_test

import (
    "testing"

    "go.uber.org/mock/gomock"
    "github.com/your-project/internal/domain/user"
    "github.com/your-project/internal/mocks"
)

func TestGetUserByID(t *testing.T) {
    ctrl := gomock.NewController(t)
    defer ctrl.Finish()

    mockRepo := mocks.NewMockUserRepository(ctrl)
    mockUser := &user.User{ID: 1, Name: "Alice"}

    mockRepo.EXPECT().
        GetByID(1).
        Return(mockUser, nil)

    uc := YourUserUsecase{UserRepo: mockRepo}

    result, err := uc.GetUserByID(1)
    if err != nil {
        t.Fatalf("unexpected error: %v", err)
    }
    if result.Name != "Alice" {
        t.Errorf("expected Alice, got %v", result.Name)
    }
}
```

## 注意事項與常見問題

### gomock 的來源？

Uber 已經 fork 並接手維護原本的 `golang/mock` 專案，並整合為 `go.uber.org/mock`。你可以直接：

```go
import "go.uber.org/mock/gomock"
```

不再需要使用已經 archived 的 `github.com/golang/mock/gomock`。

## 參考連結

- repo: https://github.com/uber-go/mock
- doc: https://pkg.go.dev/go.uber.org/mock
