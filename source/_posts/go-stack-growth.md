---
title: stack growth
date: 2025-09-09 09:45:38
tags: ['Go']
---
## Go 的 Stack 成長特性

-   Go 採用 **動態可擴展的 stack**。
-   Go 一開始每個 goroutine 的 stack **只有 2 KB**。
-   當遞迴或函式呼叫需要更多空間時，Go 會自動分配更大的 stack，並把原本的內容搬移過去。
-   Stack 會成倍成長（通常是 2 倍）。例如：2 KB → 4 KB → 8 KB → 16 KB...

### 特點

-   **優點**：節省記憶體，goroutine 可以非常多。
-   **缺點**：需要搬移時有額外成本。

## 程式碼範例

https://github.com/z6wdc/go-snippets/tree/main/stackgrowth
