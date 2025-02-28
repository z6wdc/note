---
title: Recommender System Model
date: 2021-07-12T12:40:47+09:00
tags: ["Recommender System"]
---

在 Recommender System 中常見的手法

## Rank

其實在還沒有什麼資料的時候

直接推薦使用者 rank 高的 item 就是個常見的做法

在計算 rank 的時候

也可以參考這個[算式](https://myanimelist.net/info.php?go=topanime)

## Content Based Filtering

利用 item 本身的資訊來找出相似的 item 並推薦

如果 item 有內容介紹之類的文章

也可以利用 TF-IDF 來加以分析

### Similarity

計算相似度的常用方法

- mean squared difference

- Jaccard similarity

- Cosine Similarity

- Pearson Correlation Coefficient

## Collaborative Filtering

### Model Based

PCA

SVD

Matrix Factorization

### Memory Based

#### User Based

先找與你喜好相近的人

再推薦他們喜歡的東西給你

流程如下：

1. user -> item rating matrix

   ||item1|item2|item3|item4|item5|
   |--|--|--|--|--|--|
   |user1|4|5||||
   |user2|||||1|
   |user3||5|5|5|5|5|

2. user -> user similarity matrix

   ||user1|user2|user3|
   |--|--|--|--|
   |user1|1|0|1|
   |user2|0|1|0|
   |user3|1|0|1|

3. look up similar users

4. candidate filtering

#### Item Based

用你喜歡的 Item 去找相似的 Item 來推薦你

流程如下：

1. item -> user rating matrix

   ||user1|user2|user3|
   |--|--|--|--|
   |item1|4|5||
   |user2|||1|
   |user3||5|5|

2. item -> item similarity matrix

   ||item1|item2|item3|
   |--|--|--|--|
   |item1|1|0|1|
   |item2|0|1|0|
   |item3|1|0|1|

3. candidate filtering

## Hybrid

綜合 `Content Based` 跟 `Collaborative` 的方法
