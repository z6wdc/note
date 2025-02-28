---
title: "Go Hello World"
date: 2022-12-11T15:05:39+09:00
tags: ["Go"]
---
## install
https://go.dev/doc/install

## code
```go
package main

import "fmt"

func init() {
	fmt.Println("init")
}

func main() {
    fmt.Println("Hello", "World")
}
```

### package
コードの先頭では、このファイルに記述するコードがどのパッケージに所属するかを宣言する

### import
**fmt** というパッケージを **import** する

### func
**func** を使い、`main`, `init` という function を宣言する

実行順は `init` -> `main`になる

なお

**func** **Println**の始まりはPの大文字であればfunctionはPublicになり

もし始まりは小文字であればprivateになる

## command
```zsh
go run main.go
```

## Reference
https://go.dev/doc/tutorial/getting-started
