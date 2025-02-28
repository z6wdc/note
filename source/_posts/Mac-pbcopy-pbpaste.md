---
title: Mac pbcopy pbpaste
date: 2021-07-11T22:23:10+09:00
tags: ["Mac"]
---
Mac 可以利用 `pbcopy` 這指令來複製

```bash
pbcopy < target.txt
```

```bash
cat target.txt | pbcopy
```

然後可以利用 `pbpaste` 來貼出目前複製的內容

```bash
pbpaste
```
