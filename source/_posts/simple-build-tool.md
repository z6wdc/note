---
title: simple build tool
date: 2025-03-19 14:42:30
tags: ["sbt"]
---
## sbt 是什麼？
sbt（simple build tool）是一個專為 **Scala 和 Java** 設計的建置工具，主要用於 **編譯、測試、打包與部署**。它是 Scala 生態系統中的標準建置工具，類似於 Java 的 Maven 或 Gradle。

## SBT 的特色
1. **增量編譯（Incremental Compilation）**
   - SBT 只會重新編譯修改過的程式碼，提升開發效率。

2. **互動模式（Interactive Mode）**
   - 可以在 SBT 內開啟 REPL（Read-Eval-Print Loop），即時執行指令。

3. **支援多模組（Multi-Project Build）**
   - 可同時管理多個子專案，適合大型專案開發。

4. **原生支援 Scala**
   - SBT 使用 Scala 語法來定義建置設定（`build.sbt`），可靈活擴充。

5. **內建測試支援**
   - 內建對 **ScalaTest**、**Specs2** 等測試框架的支援，方便進行單元測試與整合測試。

---

## SBT 的基本結構
SBT 項目通常包含以下檔案：
```bash
my-project/
│── project/          # 存放 SBT 插件與額外設定
│── src/              # 原始碼與測試碼
│   ├── main/scala/   # 主要 Scala 程式碼
│   ├── test/scala/   # 測試程式碼
│── build.sbt         # SBT 的主要設定檔
│── target/           # SBT 產生的編譯結果
```

## sbt 的基本指令
| 指令 | 作用 |
|---------------|-------------------------|
| `sbt compile` | 編譯專案 |
| `sbt run`     | 執行專案 |
| `sbt test`    | 執行測試 |
| `sbt package` | 產生 JAR 檔 |
| `sbt clean`   | 清除編譯後的檔案 |
| `sbt console` | 進入 Scala REPL |
| `sbt ~compile`| 監聽檔案變更，自動重新編譯 |


## `build.sbt` 範例
```scala
// 設定專案名稱與版本
name := "MyScalaProject"
version := "0.1.0"

// 設定 Scala 版本
scalaVersion := "2.13.12"

// 新增依賴（例如 Akka）
libraryDependencies += "com.typesafe.akka" %% "akka-actor" % "2.6.20"
```
