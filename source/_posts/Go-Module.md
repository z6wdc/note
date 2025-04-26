---
title: Go Module
date: 2025-04-26 23:46:34
tags: ["Go"]
---
## `go mod init`

- `go mod init` 是建立 Go Module 的指令。
- Go Module 是 Go 語言用來管理套件依賴的系統（從 Go 1.11 引入）。
- 執行後會建立 `go.mod` 檔案，記錄：
  - 模組名稱（通常是 GitHub Repo 路徑或自訂名）
  - Go 語言版本
  - 專案依賴的套件與版本

## 常用指令整理

### 1. `go mod init`

```bash
go mod init 模組名稱
```

- 建立 `go.mod` 檔案
- 初始化專案的 Module 環境

### 2. `go get`

```bash
go get 套件路徑[@版本]
```

- 下載外部套件並加入 `go.mod`
- 可以指定套件版本
- 從 Go 1.17 起，建議用 `go install` 取代安裝 CLI 工具的用途

### 3. `go mod tidy`

```bash
go mod tidy
```

- 清理 `go.mod` 和 `go.sum`
- 加回漏掉的必要依賴
- 刪除不再使用的依賴

### 4. `go mod download`

```bash
go mod download
```

- 依據 `go.mod` 下載所有需要的依賴到本地 cache
- 但不會自動更新 `go.mod`

### 5. `go mod verify`

```bash
go mod verify
```

- 驗證本地下載的 module 是否與 `go.sum` 中的 hash 紀錄一致
- 用來確保依賴沒有被篡改

### 6. `go mod graph`

```bash
go mod graph
```

- 顯示 module 之間的依賴關係圖（文字版）
- 有助於了解套件之間的關聯性

### 7. `go mod vendor`

```bash
go mod vendor
```

- 把所有依賴複製到 `vendor/` 資料夾
- 一些公司內部開發或 build server 禁止外部下載時很有用

## 開發常見流程（推薦）

1. 在專案目錄下初始化 module：

```bash
go mod init github.com/yourname/yourproject
```

2. 引入需要的套件：

```bash
go get github.com/gin-gonic/gin
```

3. 程式開發中有刪除/新增 import 時，整理依賴：

```bash
go mod tidy
```

4. 完成開發，驗證 modules 完整性：

```bash
go mod verify
```

## 小提醒

- 每個專案只要跑一次 `go mod init` 就好。
- `go.mod` 和 `go.sum` 都應該一起 commit 到 Git，確保團隊開發一致性。
- 如果只是 clone 別人的專案，通常只需要 `go mod tidy` 就可以跑起來，不必自己 `go get`。

## 參考

https://go.dev/doc/tutorial/create-module
