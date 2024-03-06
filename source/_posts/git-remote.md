---
title: git remote
date: 2021-07-18T09:18:02+09:00
categories: ["zh-Hant-TW"]
tags: ["git"]
---
[git remote](https://git-scm.com/docs/git-remote)

## 看目前設定

```bash
git remote -v
```

## 追加設定

```bash
git remote add <name> <url>
```

## 刪除設定

```bash
git remote remove <name>
```

```bash
git remote rm remove <name>
```

## 刪除 remote 上已刪除的 branch

```bash
git remote prune <name>
```
