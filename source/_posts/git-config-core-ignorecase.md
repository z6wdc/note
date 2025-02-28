---
title: git config core.ignorecase
date: 2021-07-15T08:36:22+09:00
tags: ["git"]
---

[core.ignoreCase](https://git-scm.com/docs/git-config#Documentation/git-config.txt-coreignoreCase)

雖然預設為 false

但如果用了 `git clone` 或是 `git init`

就會設定成 true

如果需要可以再度更改為 false

```bash
git config core.ignorecase false
```

如果想直接把檔案名稱改成大寫的話

也可以利用下面的 command

```bash
git mv hello.txt Hello.txt
```

[reference](https://stackoverflow.com/questions/10523849/changing-capitalization-of-filenames-in-git/24979063#24979063)
