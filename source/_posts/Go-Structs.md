---
title: "Go Structs"
date: 2022-12-12T07:35:31+09:00
tags: ["Go"]
---
## Structs とは

`Go` には関連する情報をまとめするため、 `structs` が使われる

## Defining and Declaring

```Go
package main

import "fmt"

type person struct {
	firstName string
	lastName  string
}

func main() {
	var aaa person
	fmt.Println(aaa) // The default value is a empty string.
	fmt.Printf("%+v\n", aaa) // Use the "%+v" can print the fields also.

    // Updating Struct Values
    aaa.firstName = "aaa"
    aaa.lastName = "player"
}
```

## Embedding Structs

`Structs` に `structs` も宣言できる

```Go
package main

import "fmt"

type contactInfo struct {
	email   string
	zipCode int
}

type person struct {
	firstName string
	lastName  string
	contact   contactInfo
}

func main() {
	aaa := person{
		firstName: "aaa",
		lastName:  "player",
		contact: contactInfo{
			email:   "aaa@mail.com",
			zipCode: 1234567,
		},
	}
	fmt.Println(aaa)
}
```

宣言するときに、 `contactInfo` だけを宣言すると

`contactInfo contactInfo` の書き方と同じになる

```Go
type contactInfo struct {
	email   string
	zipCode int
}

type person struct {
	firstName string
	lastName  string
	contactInfo
}
```

## Updating Struct Values

```Go
package main

import "fmt"

type player struct {
	name  string
	score int
}

func main() {
	a := player{"aaa", 0}
	fmt.Println(a)
	a.updateScore(1)
	fmt.Println(a)
}

func (p player) updateScore(s int) {
	p.score = s
}
```
```zsh:output
{aaa 0}
{aaa 0}
```

上記の`updateScore` functionを使っても`a`のスコアが更新できない

### Pass By Value

`Go`は`Pass By Value`なので、下記のように

|address|value|note|
|---|---|---|
|0001|{aaa 0} 元のa値|更新されなかった|
|0002|||
|0003|{aaa 0} コピーされた値|funcがこの値を更新した|

元の`a`のスコアが更新されなかった

### Pointer

|address|value|
|---|---|
|0001|{aaa 0}|

Turn ___address___ into **value** with `*address`

Turn **value** into ___address___ with `&value`

### Point Receiver

ReceiverのTypeに*を追加することで

`(p *player)`

宣言するtypeはstruct playerではなく、struct playerのaddressになる

そうすれば、struct `a`のaddressのvalueをpassでき

元の`a`の値を更新できるようになる

```Go
package main

import "fmt"

type player struct {
	name  string
	score int
}

func main() {
	a := player{"aaa", 0}
	fmt.Println(a)

	pointerA := &a // Turn value into address
	pointerA.updateScore(1)
	fmt.Println(a)
}

func (p *player) updateScore(s int) {
    // Turn value into address
	(*p).score = s
}
```

```zsh:output
{aaa 0}
{aaa 1}
```

ちなみに、

aのvalueをadressに転換しなくても、`Go`も処理してくれる

```Go
package main

import "fmt"

type player struct {
	name  string
	score int
}

func main() {
	a := player{"aaa", 0}
	fmt.Println(a)

	a.updateScore(1) // Use a, the player struct type
	fmt.Println(a)
}

func (p *player) updateScore(s int) {
	(*p).score = s
}
```

結果も同じ

```zsh:output
{aaa 0}
{aaa 1}
```
