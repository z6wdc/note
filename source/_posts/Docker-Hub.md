---
title: Docker Hub
date: 2021-09-20T12:36:52+09:00
tags: ["Docker"]
---
[docker hub](https://hub.docker.com/)

存放已經 build 好的 image

## tag

```bash
docker tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
```

Create a tag `TARGET_IMAGE` that refers to `SOURCE_IMAGE`

## login

```bash
docker login
```

Log in to a Docker registry

## push

```bash
docker push [OPTIONS] NAME[:TAG]
```

## pull

```bash
docker pull [OPTIONS] NAME[:TAG|@DIGEST]
```

## logout

```bash
docker logout
```

Log out from a Docker registry
