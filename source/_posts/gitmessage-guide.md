---
title: gitmessage guide
date: 2025-05-05 20:38:53
tags: ["git"]
---
`.gitmessage` 是一個純文字檔案，用來定義 Git commit 訊息的預設格式。

透過這個機制，可以統一開發流程中的 commit 格式，提升可讀性與一致性。


## 如何設定 commit template

1. **建立 commit template 檔案**
    
```bash
touch ~/.gitmessage
```

2. **編輯內容（範例見下方）**

```bash
nano ~/.gitmessage
```

3. **設定 git 使用該檔案**

```bash
git config --global commit.template .gitmessage
```

4. **確認設定**

```bash
git config --global --get commit.template
```


## .gitmessage 範例格式

```md
# 類型: 簡短描述
# 空一行
# 詳細描述（選填）
# - 說明動機
# - 涉及模組
# - 後續影響

# issue 連結（選填）
# ref: #123

# ------- 範例 -------
feat: 加入使用者登入功能

- 新增 JWT 驗證流程
- 調整 login controller 的錯誤處理
- 對應 issue #42

ref: #42
```


## 常見的 Commit 類型（Conventional Commits）

| 類型     | 說明                       |
|----------|----------------------------|
| feat     | 新功能                     |
| fix      | 錯誤修正                   |
| docs     | 文件變更                   |
| style    | 格式（不影響程式邏輯）     |
| refactor | 重構（非功能變更）         |
| test     | 增加測試                   |
| chore    | 其他更新（建置、工具等）   |


## 使用建議與好處

- 確保團隊成員使用一致的 commit message
- 提升專案可維護性與回溯紀錄


## 取消 template 設定

若不再使用：

```bash
git config --global --unset commit.template
```

## 參考

- [Conventional Commits](https://www.conventionalcommits.org/zh-hant/v1.0.0/)
