---
title: "Go Echo"
date: 2022-12-12T07:38:39+09:00
categories: ["ja"]
tags: ["Go","Echo"]
---
## Echoとは

High performance, extensible, minimalist Go web framework

https://echo.labstack.com/

### Quick Start

#### インストール

**Go**のバージョンは`1.16`を使う

```shell
mkdir myapp && cd myapp
go mod init myapp
go get github.com/labstack/echo/v4
```

### Hello, World!

```go:server.go
package main

import (
	"net/http"
	
	"github.com/labstack/echo/v4"
)

func main() {
	e := echo.New()
	e.GET("/", func(c echo.Context) error {
		return c.String(http.StatusOK, "Hello, World!")
	})
	e.Logger.Fatal(e.Start(":1323"))
}
```

```shell:start server
go run server.go
```

### Guide Reference

https://echo.labstack.com/guide/
