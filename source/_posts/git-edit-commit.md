---
title: "git コミットを修正する"
date: 2022-12-12T07:40:20+09:00
tags: ["git"]
---
## 直前のコミット

### commit --amend

```zsh
git commit --amend
```

#### reset-author

コミットの作者もリセットできる

```zsh
git commit --amend --reset-author
```

## 古いコミット

### rebase -i

```zsh
git rebase -i HEAD~n 
```

コマンドで、デフォルトのテキストエディタに直近 n コミットの一覧を表示できる
修正したいコミットの前の`pick`の文字を`edit`に変更して保存・終了する

内容修正した後

```zsh
git add .
git commit --amend
git rebase --continue
```

## Reference

https://backlog.com/ja/git-tutorial/stepup/28/

https://backlog.com/ja/git-tutorial/stepup/33/
