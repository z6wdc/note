---
title: Go 型別轉換
date: 2025-07-17 16:55:14
tags: ['Go']
---
Go 語言是一種靜態型別語言，因此會遇到需要明確「型別轉換」的情況。

以下是一些常見的類型轉換範例與對應說明：

## 整數與浮點數

```go
var i int = 42
var f float64 = float64(i)
var u uint = uint(f)
```

- `int -> float64`: 可以直接轉換，浮點數會保留小數點。
- `float64 -> uint`: 會捨去小數部分，且負數會變成很大的正整數（因為溢位），要小心。

## 字串與數值

```go
import "strconv"

s := "123"
i, err := strconv.Atoi(s) // 字串轉 int

f := 3.14
s2 := strconv.FormatFloat(f, 'f', 2, 64) // float64 轉字串
```

- 使用 `strconv` 套件進行數值與字串的轉換。
- 注意錯誤處理，像 `Atoi` 可能會轉換失敗。

## rune（字元）與 int

```go
var r rune = 'A'
var i int = int(r) // 轉換為 ASCII 整數值
```

- `rune` 實際上是 `int32`，表示 Unicode 編碼的單一字元。
- 可以直接當作整數做運算。

## interface{} 與具體型別

```go
var x interface{} = "hello"
s := x.(string) // 型別斷言，斷言 x 是 string
```

- `x.(T)` 用來從 `interface{}` 取出實際型別。
- 若型別不符會 panic，建議使用：

```go
s, ok := x.(string)
if ok {
    // 斷言成功
}
```

## 使用型別斷言處理多型行為（Polymorphism）

```go
type Animal interface {
    Speak() string
}

type Dog struct{}
func (Dog) Speak() string { return "Woof" }

type Cat struct{}
func (Cat) Speak() string { return "Meow" }

func Describe(a Animal) {
    fmt.Println("Animal says:", a.Speak())

    switch v := a.(type) {
    case Dog:
        fmt.Println("This is a dog")
    case Cat:
        fmt.Println("This is a cat")
    default:
        fmt.Println("Unknown animal:", v)
    }
}

func main() {
    Describe(Dog{})
    Describe(Cat{})
}
```

```
Animal says: Woof
This is a dog
Animal says: Meow
This is a cat
```

- 使用 `switch v := x.(type)` 可根據實際型別做特化處理，是 Go 中處理多型行為的常見模式。

## byte、[]byte、rune 與 string

```go
s := "hello"
b := []byte(s)        // string 轉 []byte
s2 := string(b)       // []byte 轉 string
```

- `string` 是 UTF-8 編碼的唯讀不可變字串（immutable）。
- `[]byte` 是可修改的位元組資料（mutable），可用於編輯、加解密、I/O 等情境。
- `string` 與 `[]byte` 互轉時，代表的是「UTF-8 編碼 ↔ 位元資料」的轉換。

### 當 string 含有非 ASCII 字元時

```go
s := "你好"
fmt.Println(len(s))              // 會印出6 因為每個中文字是 3 個 byte（UTF-8 編碼）
fmt.Println([]rune(s))           // [20320 22909] → Unicode 編碼
fmt.Println(string([]rune(s)))   // 還原成 "你好"
```

- `len(s)` 是計算 byte 長度，不是字元數。
- 若直接用 `s[i]` 取值，會是 byte，不一定會是完整字元！
- 若你要逐字處理，可以轉成 `[]rune`：

```go
for _, r := range s {
    fmt.Printf("%c、", r) // 正確逐字印出 "你" 和 "好"
}
```

| 型別     | 本質     | 描述                      | 適用情境                      |
|----------|----------|-------------------------|------------------------------|
| `string` | UTF-8    | 只讀、不可變              | 儲存和傳遞文字資料              |
| `[]byte` | `[]uint8`| 可修改的原始位元組資料      | I/O、加解密、網路傳輸等         |
| `[]rune` | `[]int32`| 一個一個的 Unicode 字元   | 字元處理、計算顯示長度等         |
