---
title: for in vs for of
date: 2025-03-04 19:26:57
tags: ["JavaScript"]
---
## **1. `for...in`**
**用來遍歷物件的**「可枚舉屬性（enumerable properties）」

### **語法**

```javascript
for (let key in object) {
  // 執行區塊
}
```

### **適用於**
- 遍歷物件的**屬性（property）**
- 也可以遍歷陣列的索引（但不推薦）

### **範例：用 `for...in` 遍歷物件**

```javascript
const user = { name: "Alice", age: 25, city: "Tokyo" };

for (let key in user) {
  console.log(`${key}: ${user[key]}`);
}
```

**輸出**

```
name: Alice
age: 25
city: Tokyo
```

### **範例：用 `for...in` 遍歷陣列（不推薦）**

```javascript
const arr = ["A", "B", "C"];

for (let index in arr) {
  console.log(index, arr[index]);
}
```

**輸出**
```
0 A
1 B
2 C
```

## **2. `for...of`**
**用來遍歷可迭代物件（iterable objects），例如陣列、字串、Map、Set、NodeList 等**

### **語法**

```javascript
for (let item of iterable) {
  // 執行區塊
}
```

### **適用於**
- 陣列（Array）
- 字串（String）
- `Map`、`Set` 等可迭代物件（iterable objects）

### **範例：用 `for...of` 遍歷陣列**

```javascript
const arr = ["A", "B", "C"];

for (let value of arr) {
  console.log(value);
}
```
 
**輸出**

```
A
B
C
```

### **範例：用 `for...of` 遍歷字串**

```javascript
const str = "Hello";

for (let char of str) {
  console.log(char);
}
```

**輸出**

```
H
e
l
l
o
```

### **範例：用 `for...of` 遍歷 `Map`**

```javascript
const map = new Map([
  ["name", "Alice"],
  ["age", 25]
]);

for (let [key, value] of map) {
  console.log(`${key}: ${value}`);
}
```

**輸出**
```
name: Alice
age: 25
```
