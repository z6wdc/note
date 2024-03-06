---
title: "git alias"
date: 2022-12-11T15:07:15+09:00
categories: ["ja"]
tags: ["git"]
---
## aliasとは

`git status` というコマンドをaliasを設定することにより、 `git st` で使える

## 設定方法

### command

```zsh
git config --global alias.st status
```

### .gitconfigに追加

```zsh
[alias]
	st = status
```

## 例
```zsh
[alias]
	br = branch
	st = status
```

## Reference

https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases
