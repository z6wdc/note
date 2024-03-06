---
title: "Go Range"
date: 2022-12-12T07:41:47+09:00
categories: ["ja"]
tags: ["Go"]
---
## Range

Range　は要素の値のコピーが返されるので、
返される要素を変更しても、元の値を影響しない
変更したい場合は、直接参照すれば

### サンプルコード

```go
package main

import "fmt"

func main() {
	users := [3]string{"A", "B", "C"}
	fmt.Printf("%#v\n", users)

	for _, u := range users {
		u += "edited"
	}
	fmt.Printf("%#v\n", users)

	for i := 0; i < len(users); i++ {
		users[i] += " edited"
	}
	fmt.Printf("%#v\n", users)
}
```

```shell:output
[3]string{"A", "B", "C"}
[3]string{"A", "B", "C"}
[3]string{"A edited", "B edited", "C edited"}
```
