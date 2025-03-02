---
title: Document Object Model
date: 2025-03-02 16:40:51
tags:
---
## 什麼是 Document Object Model (DOM) ？

**文件物件模型（Document Object Model, DOM）** 是一種程式介面，允許開發者使用程式碼來存取和操作 HTML 或 XML 文件的結構。

DOM 提供了一種樹狀結構的表示方式，讓開發者可以透過 JavaScript 或其他語言來動態修改網頁內容。

## DOM 的結構

DOM 採用樹狀結構來表示 HTML 文件，每個節點（Node）代表 HTML 文件中的一個元素。

例如，以下是一個簡單的 HTML 文件：

```html
<!DOCTYPE html>
<html>
<head>
    <title>DOM Example</title>
</head>
<body>
    <h1>Hello, DOM!</h1>
    <p>This is a paragraph.</p>
</body>
</html>
```

這個 HTML 文件在 DOM 中的結構如下：

```
Document
└── html
    ├── head
    │   └── title
    │       └── "DOM Example"
    └── body
        ├── h1
        │   └── "Hello, DOM!"
        └── p
            └── "This is a paragraph."
```

## 操作 DOM

開發者可以透過 JavaScript 來存取和操作 DOM。

例如，以下是一些常見的操作：

### 1. 獲取元素

```javascript
// 使用 ID 選取元素
document.getElementById("myElement");

// 使用類名選取元素
document.getElementsByClassName("myClass");

// 使用標籤名稱選取元素
document.getElementsByTagName("p");

// 使用 CSS 選擇器選取元素
document.querySelector(".myClass");
document.querySelectorAll("p");
```

### 2. 修改內容

```javascript
// 修改元素的文字內容
document.getElementById("myElement").textContent = "新的內容";

// 修改 HTML 內容
document.getElementById("myElement").innerHTML = "<strong>加粗文字</strong>";
```

### 3. 修改屬性

```javascript
// 修改元素的屬性
document.getElementById("myLink").href = "https://example.com";
```

### 4. 修改樣式

```javascript
// 修改 CSS 樣式
document.getElementById("myElement").style.color = "red";
```

### 5. 事件監聽

```javascript
// 監聽點擊事件
document.getElementById("myButton").addEventListener("click", function() {
    alert("按鈕被點擊了！");
});
```
