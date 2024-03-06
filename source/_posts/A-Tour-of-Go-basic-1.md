---
title: "A Tour of Go basic 1"
date: 2022-12-12T07:44:31+09:00
categories: ["ja"]
tags: ["Go"]
---
## Using the tour

`A Tour of Go`とは
`Go`言語の最も重要な機能について説明するtourです。

https://go.dev/tour/list

### Basics - Packages, variables, and functions

#### Packages

Goのプログラムは、`package`で構成されます。
プログラムは main packageから開始されます。

```Go
package main
```

#### Imports

このコードでは、括弧でパッケージのインポートをグループ化し、
`factored import statement`としています。

```Go
import (
	"fmt"
	"math"
)
```


#### Exported names

`Go`では、
最初の文字が大文字で始まる名前は、
外部のパッケージから参照できる`exported name`です。
例えば、`Pi`は`math`パッケージからエクスポートされています。

```Go
package main

import (
	"fmt"
	"math"
)

func main() {
	fmt.Println(math.Pi)
}
```

#### Functions

関数は、0個以上の引数を取ることができます。
この例では、`add`関数は、`int`型の２つのパラメータを取ります。

```Go
func add(x int, y int) int {
	return x + y
}
```

関数の２つ以上の引数が同じ型である場合には、
最後の型を残して省略して記述できます。

```Go
func add(x, y int) int {
	return x + y
}
```

#### Multiple results

関数は複数の戻り値を返すことができます。


```Go
func swap(x, y string) (string, string) {
	return y, x
}
```

#### Named return values

Goでの戻り値となる変数に名前をつける`named return value`ことができます。
戻り値に名前をつけると、関数の最初で定義した変数名として扱われます。

名前をつけた戻り値の変数を使うと、
`return`に何も書かずに戻すことができます。これを`naked return`と呼びます。

```Go
func split(sum int) (x, y int) {
	x = sum * 4 / 9
	y = sum - x
	return
}
```

#### Variables

`var`は変数を宣言します。
関数の引数リストと同様に、複数の変数の最後に型を書くことで、変数のリストを宣言できます。

`var`はパッケージ、または、関数レベルで利用できます

```Go
package main

import "fmt"

var c, python, java bool // package level

func main() {
	var i int // function level
	fmt.Println(i, c, python, java)
}
```

#### Variables with initializers

`var`宣言では、変数毎に初期化子( initializer )を与えることができます。
初期化子が与えられている場合、型を書くことは省略できます。
その変数は初期化子が持つ型になります。

```Go
package main

import "fmt"

var i, j int = 1, 2

func main() {
	var c, python, java = true, false, "no!"
	fmt.Println(i, j, c, python, java)
}
```

#### Short variable declarations

関数の中では、`var`宣言の代わりに、`:=`の代入文を使い、暗黙的な型宣言ができます。

関数の外では、
キーワードではじまる宣言(`var`, `func`など)が必要で、
`:=`は利用できません。

```Go
func main() {
	var i, j int = 1, 2
	k := 3
	c, python, java := true, false, "no!"

	fmt.Println(i, j, k, c, python, java)
}
```

#### Basic types

`Go`の`Basic types`

```
bool

string

int  int8  int16  int32  int64
uint uint8 uint16 uint32 uint64 uintptr

byte // alias for uint8

rune // alias for int32
     // represents a Unicode code point

float32 float64

complex64 complex128
```

`int`, `uint`, `uintptr`型は、
32-bitのシステムでは32 bitで、64-bitのシステムでは64 bitです。

整数の変数が必要な場合は
`sized`, `unsigned`の型を使う理由がない限り、`int`を使うようにしましょう。

変数宣言は、`factored`宣言も可能です。

```Go
var (
	ToBe   bool       = false
	MaxInt uint64     = 1<<64 - 1
	z      complex128 = cmplx.Sqrt(-5 + 12i)
)
```

#### Zero values

変数に初期値を与えずに宣言すると、`zero value`が与えられます。
`zero value`は型によって以下のように与えられます:

- 数値型(int,floatなど): 0
- bool型: false
- string型: "" ( empty string )

```Go
package main

import "fmt"

func main() {
	var i int
	var f float64
	var b bool
	var s string
	fmt.Printf("%v %v %v %q\n", i, f, b, s)
}
```

```zsh:output
0 0 false ""
```

#### Type conversions

変数`v`、型`T`があった場合、`T(v)`は、変数`v`を`T`型へ変換します。
C言語とは異なり、Goでの型変換は明示的な変換が必要です。

```Go
var i int = 42
var f float64 = float64(i)
var u uint = uint(f)
```

#### Type inference

明示的な型を指定せず
変数を宣言する場合(`:=`や`var = `のいずれか)、変数の型は右側の変数から型推論されます。

右側の変数が型を持っている場合、左側の新しい変数は同じ型になります。

```Go
var i int
j := i // j is an int
```

右側に型を指定しない数値である場合、
左側の新しい変数は右側の数の精度に基いて`int`, `float64`, `complex128`の型になります。

```Go
i := 42           // int
f := 3.142        // float64
g := 0.867 + 0.5i // complex128
```

#### Constants

`constant`は、`const`キーワードを使って変数と同じように宣言します。
`constant`は、character, string, boolean, numericのみで使えます。
なお、`constant`は`:=`を使って宣言できません。

```Go
package main

import "fmt"

const Pi = 3.14

func main() {
	const World = "世界"
	fmt.Println("Hello", World)
	fmt.Println("Happy", Pi, "Day")

	const Truth = true
	fmt.Println("Go rules?", Truth)
}
```

#### Numeric Constants

`numeric constants`は、高精度な値 ( values )です。
型のない`constants`は、その状況によって必要な型を取ることになります。

```Go
package main

import "fmt"

const (
	// Create a huge number by shifting a 1 bit left 100 places.
	// In other words, the binary number that is 1 followed by 100 zeroes.
	Big = 1 << 100
	// Shift it right again 99 places, so we end up with 1<<1, or 2.
	Small = Big >> 99
)

func needInt(x int) int { return x*10 + 1 }
func needFloat(x float64) float64 {
	return x * 0.1
}

func main() {
	fmt.Println(needInt(Small))
	fmt.Println(needInt(Big)) // overflows int
	fmt.Println(needFloat(Small))
	fmt.Println(needFloat(Big))
}
```
