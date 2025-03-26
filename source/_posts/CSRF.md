---
title: CSRF
date: 2025-03-26 16:02:29
tags:
---
CSRF（Cross-Site Request Forgery，跨站請求偽造） 是一種 Web 安全漏洞

攻擊者可以利用受害者已經驗證的會話，在未經授權的情況下，透過受害者的瀏覽器發送惡意請求到受害者已登入的網站，執行未經授權的操作。

## **CSRF 攻擊流程**
1. **受害者登入受信任的網站**（如銀行、購物網站、社交平台），並且瀏覽器存有該網站的認證 Cookie。
2. **攻擊者誘導受害者訪問惡意網站**，例如：
   - 透過電子郵件、社群媒體或廣告放置惡意連結。
   - 在受害者造訪的網站中嵌入惡意的 JavaScript 代碼（如 XSS 攻擊）。
3. **受害者的瀏覽器在未察覺的情況下向受信任的網站發送請求**：
   - 瀏覽器會自動附帶該網站的 Cookie，因為請求來自受害者的瀏覽器，網站會認為該請求是合法的。
   - 例如，攻擊者可以讓受害者透過 `GET` 或 `POST` 方法執行敏感操作，如轉帳、修改密碼、發送訊息等。
4. **受害者的請求成功執行**，攻擊者達成目的。

---

## **CSRF 攻擊範例**
假設受害者已登入某個銀行網站（`bank.com`），攻擊者可以在惡意網站中放置以下 HTML 代碼：

```html
<img src="https://bank.com/transfer?amount=1000&to=attacker_account">
```

當受害者造訪這個網站時，瀏覽器會自動向 `bank.com` 發送請求，並附帶受害者的登入 Cookie，導致資金被轉移到攻擊者的帳戶。

---

## **如何防禦 CSRF**

### **1. CSRF Token**
- 伺服器在每次表單提交或敏感操作時，生成一個獨特的隨機字串（Token）。
- 這個 Token 必須隨著請求一起提交，伺服器會驗證 Token 是否正確。
- 由於攻擊者無法輕易獲取這個 Token，因此無法偽造請求。

**範例：**
後端返回 CSRF Token：
```html
<form action="/transfer" method="POST">
    <input type="hidden" name="csrf_token" value="random_csrf_token">
    <input type="text" name="amount">
    <button type="submit">轉帳</button>
</form>
```

伺服器驗證 `csrf_token` 是否正確，若無效則拒絕請求。

---

### **2. SameSite Cookie 設定**
- 設定 `SameSite=Strict` 或 `SameSite=Lax`，防止瀏覽器在跨站請求時自動附帶 Cookie。
- `SameSite=Lax` 適用於大部分情境，`SameSite=Strict` 更為嚴格，但可能影響部分功能。

範例：
```http
Set-Cookie: session_id=abc123; Secure; HttpOnly; SameSite=Strict
```

---

### **3. 驗證 `Referer` 或 `Origin`**
- 伺服器可以檢查 HTTP `Referer` 或 `Origin`，確認請求是否來自受信任的來源。

---

### **4. 強制使用 POST 請求**
- 確保敏感操作（如轉帳、修改密碼）不使用 `GET` 方法，而是 `POST`，並搭配 CSRF Token。

---

### **5. 用戶驗證**
- 在關鍵操作前，要求用戶重新輸入密碼或 2FA 驗證，例如：
  - 銀行轉帳時，要求用戶輸入 OTP（一次性密碼）。
  - 修改郵箱或密碼時，要求重新登入。

---

## **結論**
CSRF 是一種利用使用者瀏覽器信任關係的攻擊方式，主要防禦措施包括：
- 使用 CSRF Token 驗證請求來源。
- 設置 `SameSite` 屬性的 Cookie 限制跨站請求。
- 驗證 `Referer` 或 `Origin` 以過濾可疑請求。
- 限制敏感操作只允許 `POST`，並要求額外身份驗證。
