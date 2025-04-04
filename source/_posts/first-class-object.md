---
title: first class object
date: 2025-04-04 17:36:49
tags:
---
在程式語言中，第一級物件（First-class object）是指可以像變數一樣操作的資料或結構。

具備以下能力：可以被賦值給變數、可以作為參數傳遞給函式、可以作為函式的回傳值、可以儲存在資料結構中（如陣列、Map、物件等）。

常見例子：JavaScript 中的函式就是第一級物件，例如：

```javascript
function greet() {
  console.log("Hello!");
}
const sayHi = greet;
sayHi();
function callFunc(f) {
  f();
}
callFunc(greet);
function outer() {
  return function inner() {
    console.log("I'm inner");
  };
}
const innerFunc = outer();
innerFunc();
```

除了「第一級物件」，實際上並沒有嚴格定義的第二級、第三級物件。

但有些語言中某些資料型別不具備上述全部特性，會被稱為「非第一級」或「second-class」（非正式術語），代表支援有限，例如早期 Java 中的函式不能被當作值傳遞；C 語言雖有函式指標，但無匿名函式，也不能輕易回傳函式。

第一級物件的重要性在於它允許使用高階函式（higher-order functions）、函式式編程（functional programming）、實作 callback、Promise、async/await 等模式，也能建立 closure（閉包）來保存建立當下的變數環境。
