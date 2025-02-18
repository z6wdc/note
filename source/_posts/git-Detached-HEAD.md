---
title: "Detached HEAD"
date: 2022-12-11T15:11:21+09:00
categories: ["zh-Hant-TW"]
tags: ["git"]
---
## 什麼是 Detached HEAD？
**Detached HEAD** 狀態表示你的 `HEAD` 並未指向任何分支，而是直接指向了一個特定的 commit。

## 何時會進入 Detached HEAD？

- 使用特定 commit：

```bash
git checkout <commit-id>
```

- 切換到 tag：

```bash
git checkout <tag-name>
```

## Detached HEAD 的影響
- **你所做的任何 commit 不會被分支保留**：
  
  - 若切換到其他分支，這些 commit 會「遺失」（實際上還存在於 `reflog` 中）。
  
  - **解決方法**：在 Detached HEAD 下完成工作後，創建一個新分支保留：

    ```bash
    git checkout -b new-branch
    ```

## 如何離開 Detached HEAD？

- 切回原本的分支：

```bash
git checkout main
```

## 如何找回 Detached HEAD 下的 commit？

使用 `git reflog` 來查看並找回遺失的 commit：

```bash
git reflog
```

### 範例

```plaintext
abcd123 HEAD@{0}: commit: 修正
efgh456 HEAD@{1}: checkout: moving from main to abcd123
```

- 找到你在 Detached HEAD 下的 commit 後，使用以下指令建立新分支：

```bash
git checkout -b new-branch abcd123
```

## 注意事項

- Detached HEAD 狀態適合「**查看**」歷史 commit 或 tag，不適合直接進行修改，除非確定要創建分支保存。

- **`git reflog`** 可以找回已遺失的 commit，但 Git 最終會清理掉沒有被任何分支或 tag 指向的 commit（約30天內）。
