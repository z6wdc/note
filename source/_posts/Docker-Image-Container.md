---
title: Docker Image Container
date: 2021-09-19T17:23:56+09:00
tags: ["Docker"]
---
## Image

Templates / Blueprints for `containers`

## Container

The running "unit of software"

## base command

[base command](https://docs.docker.com/engine/reference/commandline/docker/)

### build

```bash
docker build PATH
```

Build an image from a `Dockerfile`

```bash
docker build -t name:tag PATH
```

Name and optionally a tag in the `name:tag` format

### run

```bash
docker run IMAGE
```

```bash
docker run --name name IMAGE
```

Assign a name to the container

```bash
docker run -d IMAGE
```

Run container in background and print container ID

```bash
docker run -it IMAGE
```

`-i` Keep STDIN open even if not attached

`-t` Allocate a pseudo-TTY

```bash
docker run --rm IMAGE
```

Automatically remove the container when it exits

### start

```bash
docker start CONTAINER
```

```bash
docker start -a CONTAINER
```

Attach STDOUT/STDERR and forward signals

### attach

```bash
docker attach [OPTIONS] CONTAINER
```

### logs

```bash
docker logs CONTAINER
```

```bash
docker logs -f CONTAINER
```

The `docker logs -f` command will continue streaming the new output from the container’s `STDOUT` and `STDERR`.

### rm

```bash
 docker rm CONTAINER
```

### container prune

```bash
docker container prune
```

Remove all stopped containers

### rmi

```bash
docker rmi IMAGE
```

### image prune

```bash
docker image prune
```

Remove unused images

### image inspect

```bash
docker image inspect IMAGE
```

### cp

```bash
docker cp CONTAINER:SRC_PATH DEST_PATH|-
```

Copy files/folders between a container and the local filesystem
