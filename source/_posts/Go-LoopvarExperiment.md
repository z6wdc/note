---
title: Go語言 for 迴圈中閉包捕捉變數行為
date: 2025-07-18 20:09:10
tags: ['Go']
---
這段程式碼展示了在 `for` 迴圈中，閉包（closure）如何捕捉迴圈變數。

```go
package main

import "fmt"

func main() {
	var fns []func()
	for i := 0; i < 3; i++ {
		fns = append(fns, func() {
			fmt.Println(i)
		})
	}
	for _, fn := range fns {
		fn()
	}
}
```

## Go 1.22 以前

上述程式會印出三次 `3`。

這是因為匿名函式捕捉的是迴圈變數 `i` 的參考（reference），當迴圈結束時，`i` 的值已經變成 `3`。

### 輸出
```
3
3
3
```

## Go 1.22 起

Go 1.22 修正了這個行為，將每次迴圈中的變數 `i` 視為新的區域變數。

因此，輸出會是預期中的 `0 1 2`。

### 輸出
```
0
1
2
```

## 參考資料

- [Go Wiki: LoopvarExperiment](https://go.dev/wiki/LoopvarExperiment)
- [Go 語言版本差異測試專案](https://github.com/z6wdc/go-version-lab)
