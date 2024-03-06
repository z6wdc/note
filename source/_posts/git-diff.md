---
title: "git diff"
date: 2022-12-11T15:11:21+09:00
categories: ["ja"]
tags: ["git"]
---
## git diff とは

commits, commit, working treeなどの間の変更を表示する

### Comparing with arbitrary commits

```shell
git diff main
```

現在の**branch**と`main`の**branch**を比較する

### --name-only

```shell
> git diff --name-only main
a.txt
b.txt
c.txt
```

変更されたファイルの名前のみを表示する

### --name-status

```shell
> git diff --name-status main
M       a.txt
D       b.txt
A       c.txt
```

変更されたファイルの名前と状態のみを表示する

### --diff-filter=[(A|C|D|M|R|T|U|X|B)…​[*]]

指定したファイルの変更状態のみを表示する

- A:Added
- D:Deleted
- M:Modified
- R:Renamed

なお、大文字は指定、小文字は指定しない

```shell:upper-case letters
> git diff --diff-filter=AM --name-status  main
M       a.txt
A       c.txt
```

```shell:lower-case letters
> git diff --diff-filter=a --name-status  main
M       a.txt
D       b.txt
```

## Reference

https://git-scm.com/docs/git-diff
