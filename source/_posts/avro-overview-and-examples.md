---
title: avro overview and examples
date: 2025-05-08 16:36:00
tags: ["avro"]
---
## 什麼是 AVRO

Apache Avro 是一種資料序列化格式

專為高效的資料儲存與傳輸而設計，屬於 Apache Hadoop 生態系中的一部分。

它的特點包括：
- 使用 JSON 定義 schema
- 使用二進位格式儲存資料（compact）
- 支援 schema 演化（例如加欄位、改型別）
- 非常適合用於 Kafka、HDFS、RPC 等場景

## 為了解決什麼問題

AVRO 的設計目的是為了解決資料交換與儲存過程中，常見的以下幾個問題：

### 1. JSON/CSV 的結構不穩定與冗長問題

#### 問題說明：
你可能使用 JSON 存放 Kafka 傳來的事件記錄，例如：

{ "userId": "u123", "loginTime": "2024-05-08T10:00:00Z" }

但過了一段時間，有人新增了一個欄位叫做 ipAddress，導致下游處理程式爆錯，因為：
- 沒有固定 schema，難以保證欄位存在與型別正確
- JSON 沒有型別驗證
- 每筆資料都要寫入欄位名稱 → 檔案很大、傳輸慢

#### AVRO 的解法：
- schema 明確定義欄位名稱與型別
- 資料本體為二進位格式，不含欄位名稱（節省空間）
- 透過 schema 驗證，可以提前擋掉不符欄位的資料

### 2. 不同服務間資料交換，格式不一致

#### 問題說明：
假設一個系統由多個服務組成：
- A 系統產出一批使用者資料（userId, name, birthday）
- B 系統只需要 userId 和 name，但使用 JSON 解析時，常因欄位不一致導致失敗或錯誤行為

#### AVRO 的解法：
- A 寫入時附帶 schema
- B 可以用自己的 reader schema 讀取自己關心的欄位，忽略其他欄位

### 3. 資料結構的版本更新（Schema Evolution）

#### 問題說明：
你設計了一個活動紀錄格式如下：

{ "userId": "u456", "event": "purchase" }

後來你希望加上商品 ID 與金額欄位：

{ "userId": "u456", "event": "purchase", "itemId": "i789", "amount": 100 }

舊資料沒有這些欄位，會不會壞掉？

#### AVRO 的解法：
- 可為新增欄位設定預設值（例如 amount = 0）
- 讀取舊資料時，自動補上這些欄位

## 參考

- https://avro.apache.org/
