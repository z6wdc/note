---
title: git merge vs rebase
date: 2025-07-09 07:31:06
tags: ["git"]
---
多人協作開發中，merge 與 rebase 是最常見的兩種分支整合策略

## 多人 merge 流程

以下是兩位開發者共同開發 `feature/main`，使用 merge 進行同步與整合的完整流程：

1.
從 `feature/main` 切出各自的開發分支
例如 `feature/user1-work` 與 `feature/user2-work`

2.
各自進行開發工作
user1 完成 commit B，user2 完成 commit C

3.
`feature/main` 有了新的進度 F
可能來自其他成員的 merge 或修正

4.
雙方將最新主線進度 merge 回自己的分支
user1 執行 git merge feature/main → 產生 commit D（merge commit）
user2 也執行相同操作 → 產生 commit E（merge commit）

5.
user1 完成開發後，將分支 merge 回 `feature/main`
→ 產生 merge commit M1

6.
user2 在合併前，再次與最新的 `feature/main` 同步
→ 將 M1（user1 的改動）merge 回自己的分支，解決衝突並確認測試通過
→ 然後將自己的分支 merge 回 `feature/main`，產生 M2

## 多人 rebase 流程

以下是兩位開發者共同開發 `feature/main`，使用 rebase 進行同步與整合的完整流程：

1.
從 `feature/main` 切出各自的開發分支
例如 `feature/user1-work` 與 `feature/user2-work`

2.
各自進行開發工作
user1 完成 commit B，user2 完成 commit C

3.
`feature/main` 有了新的進度 F
可能來自其他成員的 merge 或修正

4.
雙方將自己的 commit 以 rebase 方式接在 F 後面
user1 執行 git rebase feature/main → 得到 B'
user2 執行 git rebase feature/main → 得到 C'

5.
user1 將自己的變更合併回 feature/main
→ 形成 commit M1

6.
user2 在合併前，
將自己的 commit 再次以 rebase 方式接在 M1 後面 → 得到 C''

7.
user2 再將自己的 C'' 合併回 feature/main
→ 形成 commit M2

## 比較

| 比較項目 | `git merge` | `git rebase` |
|---------|-------------|--------------|
| 歷史結構 | 保留分支與合併脈絡，可能出現多叉歷史 | 線性歷史，結構整齊清楚 |
| 是否產生新 commit| 會產生一個新的 merge commit | 將原本 commit 重新建立在新基礎上（產生新hash）|
| commit 順序 | 保留原始順序 | 會根據 rebase 順序重排 |
| 衝突處理方式 | 每次 merge 解一次衝突 | 每個 commit 都可能產生 conflict，需要逐個處理 |
