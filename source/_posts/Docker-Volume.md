---
title: Docker Volume
date: 2021-09-20T17:43:55+09:00
tags: ["Docker"]
---
[Volume](https://docs.docker.com/storage/volumes/)

讓我們來存放 data 的地方

就不會因為 container 被刪除

而使得 存放在 container 的 data 也連帶被刪除

## Anonymous Volume

```bash
docker run -v /app/data
```

## Named Volume

```bash
docker run -v data:/app/data
```

## Bind Mount

```bash
docker run -v /path/to/code:/app/code
```
