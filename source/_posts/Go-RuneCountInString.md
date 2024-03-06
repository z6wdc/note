---
title: "Go RuneCountInStringで文字列の文字数を取得"
date: 2022-12-12T07:42:59+09:00
categories: ["ja"]
tags: ["Go"]
---
`Go` にて文字列の文字数を取得したい時に

`len` の場合

`byte`で数えるまたは一つの `Unicode character`は`1~4`bytesが使われるため

英語以外の文字列はうまく文字数を取れないことがあります。

`unicode/utf-8` パッケージの `RuneCountInString` 関数を使えば

文字列の文字数を取得できるようになります。

```go
package main

import (
	"fmt"
	"unicode/utf8"
)

func main() {
	name := "テスト太郎"
	fmt.Println("len:", len(name))
	fmt.Println("RuneCountInString:", utf8.RuneCountInString(name))
}
```

```zsh:output
len: 15
RuneCountInString: 5
```
