---
title: Bitwise Operators in Go
date: 2025-07-14 18:41:33
tags: ["Go"]
---
## 基本運算子

| 運算子 | 名稱      | 說明                         | 範例（十進位） | 範例（二進位）        |
|-------|-----------|-----------------------------|----------------|----------------------|
| `&`    | AND       | 兩位都為 1 才為 1             | `6 & 3 = 2`    | `110 & 011 = 010`     |
| `\|`   | OR        | 只要其中一位為 1 就為 1        | `6 \| 3 = 7`   | `110 \| 011 = 111`    |
| `^`    | XOR       | 相同為 0，不同為 1            | `6 ^ 3 = 5`    | `110 ^ 011 = 101`     |
| `<<`   | 左移      | 每移一位，相當於乘以 2          | `3 << 1 = 6`   | `011 << 1 = 110`      |
| `>>`   | 右移      | 每移一位，相當於除以 2          | `6 >> 1 = 3`   | `110 >> 1 = 011`      |

## AND (`&`) — 位元交集

```go
a := 6 // 110
b := 3 // 011
c := a & b // 010 → 2
```

## OR (`|`) — 位元聯集

```go
a := 6 // 110
b := 3 // 011
c := a | b // 111 → 7
```

## XOR (`^`) — 位元異或

```go
a := 6 // 110
b := 3 // 011
c := a ^ b // 101 → 5
```

## 左移 (`<<`) / 右移 (`>>`)

```go
a := 3       // 011
b := a << 1  // 110 → 6
c := a >> 1  // 001 → 1
```

## 常見技巧應用

- `x & 1`：判斷是否為奇數（奇數最低位為 1）
- `x << n`：相當於 `x * (2^n)`
- `x >> n`：相當於 `x / (2^n)`（向下取整）
- `x ^ x = 0`：XOR 同值為 0
- `x & (x - 1)`：清除最右邊的 1（可用來統計 1 的個數）
