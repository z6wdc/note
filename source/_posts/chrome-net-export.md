---
title: Chrome net-export
date: 2025-03-16 09:44:59
tags: ["Chrome"]
---
`net-export` 是 Google Chrome 內建的工具，用來擷取網路流量的記錄（NetLog），以便進行網路診斷和除錯。

這個工具可以記錄所有經過 Chrome 的網路請求，包括 HTTP/HTTPS、WebSocket、DNS 查詢等，並輸出成 JSON 格式的 NetLog 檔案。

## **如何使用 `net-export` 來擷取 NetLog？**

### **方法 1：透過 Chrome 內建 UI**

1. 在 Chrome 地址列輸入：
   ```
   chrome://net-export/
   ```
   然後按 Enter 進入 `Net Export` 頁面。

2. 點擊 **「Start Logging to Disk」** 按鈕，選擇一個儲存 NetLog 檔案的路徑（例如 `netlog.json`）。

3. 在 Chrome 中進行你的操作（例如載入有問題的網站、執行 API 請求等）。

4. 完成後，回到 `chrome://net-export/` 頁面，點擊 **「Stop Logging」** 按鈕。

5. 你的 NetLog 檔案已儲存，可以用來進行分析。

## **如何分析 NetLog 檔案？**

你可以使用 Chrome 提供的 NetLog Viewer 來開啟這個 JSON 檔案：

1. 打開 `chrome://net-internals/#import`（或使用 [NetLog Viewer](https://netlog-viewer.appspot.com/)）。
2. 點擊 **「Choose File」** 上傳 `JSON` 檔案。
3. 瀏覽記錄的詳細資訊，找出可能的網路問題。

## **方法 2：透過命令列擷取 NetLog**

如果你想從命令列啟動 Chrome 並自動擷取 NetLog，可以使用以下指令：

### **Windows（cmd）**
```sh
chrome.exe --log-net-log=C:\path\to\netlog.json --net-log-capture-mode=IncludeSocketBytes
```

### **Mac/Linux**
```sh
/Applications/Google\ Chrome.app/Contents/MacOS/Google\ Chrome --log-net-log=~/netlog.json --net-log-capture-mode=IncludeSocketBytes
```

這樣 Chrome 啟動後就會開始記錄所有網路請求，直到你手動關閉 Chrome。

## **NetLog 捕捉模式（可選）**

在命令中，`--net-log-capture-mode` 參數有幾種模式：

- `Default`（預設）：只捕捉基本的網路事件。
- `IncludeCookiesAndCredentials`：包含 HTTP cookies 和授權資訊。
- `IncludeRawBytes`：記錄完整的傳輸資料。

例如：
```sh
chrome.exe --log-net-log=C:\netlog.json --net-log-capture-mode=IncludeCookiesAndCredentials
```
