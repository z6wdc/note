---
title: go install vs go get
date: 2025-04-26 23:33:15
tags: ["Go"]
---
## 基本比較表

| 比較項目 | `go get` | `go install` |
|:---|:---|:---|
| 主要用途 | 下載套件＋修改 `go.mod` | 編譯並安裝可執行檔（build & install） |
| 會改到 `go.mod` 嗎？ | ✅ 會（管理 dependencies） | ❌ 不會（只是 build 安裝） |
| 會編譯嗎？ | 不一定（主要是抓套件） | ✅ 會 build 成 binary（執行檔） |
| 常見用途 | - 加套件到專案 <br> - 指定或更新版本 | - 安裝 CLI 工具 <br> - 安裝別人的應用程式 |
| 適合場合 | 開發自己專案時加依賴 | 安裝 CLI 工具、直接使用的應用程式 |

## 更具體的例子

### 使用 `go get` （管理專案依賴）

```bash
go get github.com/spf13/cobra
```

- 下載並安裝套件
- 修改 `go.mod` 加入依賴
- 修改 `go.sum` 保證套件正確性
- 專案未來 build/run 可以用到這個套件

### 使用 `go install` （安裝工具）

```bash
go install github.com/golangci/golangci-lint/cmd/golangci-lint@latest
```

- 下載原始碼並編譯
- 產生可執行檔（binary）
- 安裝到 `$GOPATH/bin` 或 `$HOME/go/bin`
- **不會**修改 `go.mod` 或 `go.sum`

## 技術性補充

- `go get` 主要是**專案內的套件管理工具**
- `go install` 是**個人開發環境用的安裝指令**

從 Go 1.17 開始，**安裝 CLI 工具應該使用 `go install`**，不再建議用 `go get`。

## 小總結

|  | `go get` | `go install` |
|:---|:---|:---|
| 管理套件？ | ✅ | ❌ |
| 安裝工具？ | ❌（1.17後不推薦） | ✅ |
| 主要目的 | 增加專案依賴 | 安裝執行檔到本機 |
| 會改 `go.mod`？ | ✅ | ❌ |

## 參考

https://go.dev/doc/go-get-install-deprecation