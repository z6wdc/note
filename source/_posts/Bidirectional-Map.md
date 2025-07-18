---
title: 雙向 Hash Map
date: 2025-07-19 07:56:04
tags: ['LeetCode']
---
## 什麼時候要用雙向 Hash Map？

當題目需要你判斷：

* 兩組資料之間是否為**一一對應（bijection）**
* 「不能有重複對應」，也就是：

  * A → X
  * B → Y ✅ 合法
  * A → X，但 B 也 → X ❌ 不合法

## 題目整理

| 題號                                                             | 題名                       | 類型                   | 難度     |
| -------------------------------------------------------------- | ------------------------ | -------------------- | ------ |
| [205](https://leetcode.com/problems/isomorphic-strings)        | Isomorphic Strings       | 字串 ↔ 字串              | Easy   |
| [290](https://leetcode.com/problems/word-pattern)              | Word Pattern             | pattern ↔ words      | Easy   |
| [291](https://leetcode.com/problems/word-pattern-ii)           | Word Pattern II          | 回溯 + 雙向 map          | Hard   |

## 時間與空間複雜度分析

### 時間複雜度

* 設 pattern 長度為 n

* 每個 map 查詢 / 插入為 O(1)，共做 n 次（對每個字元或單字做一次對應判斷與設定）

  為什麼是 n 次？因為我們對每個輸入字元（如 'a'、'b'）或單字（如 "dog"、"cat"）都進行最多兩次查詢（正向與反向）與最多兩次插入，總共進行 n 輪處理。因此整體時間與 pattern 或輸入字串長度成正比。

**時間複雜度：O(n)**

### 空間複雜度

* 使用兩個 map，各最多存 n 筆

**空間複雜度：O(n)**

## 解題技巧與小提醒

1. 題目出現「每個 A 對一個 B，B 也只對一個 A」時，幾乎可以判斷需要雙向 map。
2. 使用兩個 map 可避免「一對多、多對一」錯誤，**比只用一個 map 更穩定**。
3. 注意判斷是否存在時要用 `ok` 判斷，而非依賴 default value。

   在 Go 語言中，從 map 取值即使 key 不存在，
   也會回傳對應型別的 default value（如整數 0、空字串 ""、布林 false 等），可能造成邏輯誤判。

   錯誤示範：

   ```go
   m := make(map[string]int)
   fmt.Println(m["x"]) // 輸出 0，但 "x" 並不在 map 中
   ```

   正確寫法：

   ```go
   if val, ok := m["x"]; ok {
       fmt.Println("存在，值為", val)
   } else {
       fmt.Println("key 不存在")
   }
   ```
