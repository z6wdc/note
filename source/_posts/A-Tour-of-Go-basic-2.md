---
title: "A Tour of Go basic 2"
date: 2022-12-12T07:44:35+09:00
tags: ["Go"]
---
## Using the tour

`A Tour of Go`とは
`Go`言語の最も重要な機能について説明するtourです。

https://go.dev/tour/list

### Basics - Flow control statements: for, if, else, switch and defer

#### For

`for`ループはセミコロン`;`で3つの部分に分かれています。

1. init statement
2. condition expression
3. post statement

ループは、`condition expression`が false となった場合、停止します

```Go
func main() {
	sum := 0
	for i := 0; i < 10; i++ {
		sum += i
	}
	fmt.Println(sum)
}
```

初期化と後処理ステートメントの記述は任意です。

#### For is Go's "while"

`init statement`と`post statement`の記述は任意、`;`も省略できます。
そうすることで、`while`は、`Go`では`for`だけを使います。

```Go
func main() {
	sum := 1
	for sum < 1000 {
		sum += sum
	}
	fmt.Println(sum)
}
```

#### Forever

`condition expression`も省略すれば、`infinite loop`になります。

```Go
func main() {
	for {
	}
}
```

#### If

`if`は、`for`と同様に、`()`は不要で、`{}`は必要です。

```Go
func sqrt(x float64) string {
	if x < 0 {
		return sqrt(-x) + "i"
	}
	return fmt.Sprint(math.Sqrt(x))
}
```

#### If with a short statement

`if`条件の前に、statementを書くことができます。
ここで宣言された変数は、`if`のスコープ内だけで有効です。

```Go
func pow(x, n, lim float64) float64 {
	if v := math.Pow(x, n); v < lim {
		return v
	}
	return lim
}
```

#### If and else

`if`statementで宣言された変数は、 `else`ブロック内でも使うことができます。

```Go
func pow(x, n, lim float64) float64 {
	if v := math.Pow(x, n); v < lim {
		return v
	} else {
		fmt.Printf("%g >= %g\n", v, lim)
	}
	// can't use v here, though
	return lim
}
```

#### Switch

`Go`では選択された`case`だけを実行し、それに続く全ての`case`は実行されません。

もう一つの違いは
`Go`の`switch`の`case`は定数である必要はなく、
関係する値は整数である必要もないということです。

```Go
func main() {
	fmt.Print("Go runs on ")
	switch os := runtime.GOOS; os {
	case "darwin":
		fmt.Println("OS X.")
	case "linux":
		fmt.Println("Linux.")
	default:
		// freebsd, openbsd,
		// plan9, windows...
		fmt.Printf("%s.\n", os)
	}
}
```

#### Switch evaluation order

`switch`は、上から下へ`case`を評価します。
`case`の条件が一致すれば、そこで停止(自動的にbreak)します。

```
switch i {
case 0:
case f():
}
```

i==0であれば、 case 0でbreakされるため`f`は呼び出されません。

#### Switch with no condition

条件のないswitchは、`switch true`と書くことと同じです。

この`switch`の構造は、`if-then-else`のつながりをシンプルに表現できます。

```Go
func main() {
	t := time.Now()
	switch {
	case t.Hour() < 12:
		fmt.Println("Good morning!")
	case t.Hour() < 17:
		fmt.Println("Good afternoon.")
	default:
		fmt.Println("Good evening.")
	}
}
```

#### Defer

`defer`へ渡した関数の実行を、呼び出し元の関数の終わり(returnする)まで遅延させるものです。

```Go 
package main

import "fmt"

func main() {
	defer fmt.Println("world")

	fmt.Println("hello")
}

```

```zsh:output
hello
world
```

#### Stacking defers

`defer`へ渡した関数が複数ある場合、その呼び出しはスタック`stack`されます。
呼び出し元の関数がreturnするとき、渡した関数は`last-in-first-out`の順番で実行されます。

```Go
package main

import "fmt"

func main() {
	fmt.Println("counting")

	for i := 0; i < 10; i++ {
		defer fmt.Println(i)
	}

	fmt.Println("done")
}
```

```zsh:output
counting
done
9
8
7
6
5
4
3
2
1
0
```
