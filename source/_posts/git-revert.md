---
title: git revert
date: 2024-11-08 15:37:08
tags: ["git"]
---
當要還原的時候有 `git reset` 跟 `git revert` 可以選擇

`git reset` 是修改歷史（刪除或改寫 commit）

`git revert` 透過新增一個「反向」commit 來撤銷之前的變更

所以通常用於想保留歷史記錄的情況

## command

還原單一commit

```bash
git revert <commit>
```

### option -n --no-commit

使用這選項會執行還原操作但不會自動生成提交（commit）

會將還原的變更放入暫存區再進行一次性提交

```bash
git -n <最新commit> <第二新commit> <最舊commit>
git commit -m "revert multiple commits"
```

commit 順序應該從最新到最舊避免依賴錯誤

或直接指定開頭跟結尾的 commit

```bash
git revert -n <最舊commit>..<最新commit>
```

## reference

https://git-scm.com/docs/git-revert.html
