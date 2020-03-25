---
title: Rのジオコーディングで詰まった話
tags: R 位置情報
author: motsu_engineering
slide: false
---
# 状況
住所から経度緯度を求めたい。いわゆるジオコーディングを行いたい。今回はGoogle APIとRのライブラリであるggmapを用いてジオコーディングを行った。
# 使用言語
R 3.6.1
# 発生した問題点
```R
hoge %>% 
  mutate(緯度 = geocode(住所)$lat,
         経度 = geocode(住所)$lon)
```
を実行した際に、

```
Error in geocode(住所) : is.character(location) is not TRUE
```

とデータの型がcharacterではないことをエラーが出た。

# 解決方法
```
hoge$住所 <- as.character(hoge$住所)
```

としてデータの型をcharacterに変更した。
# 終わりに
データの型によるエラーで今後ジオコーディングを行う際の備忘録として記している。
# コード
```R
# パッケージの読み込みとAPIの設定
library(ggmap)
library(tidyverse)
library(dplyr)
register_google("your google api key ")
has_google_key() 

# データの読み込み
hoge <- read.csv("hoge.csv",row.names = 1)
# 経度緯度に変換したい住所のデータ型をcharに変更
hoge$住所 <- as.character(hoge$住所)
# ジオコーディングを行う
hoge_address <- geocode(hoge$住所)
# データを結合する
hoge <- cbind(hoge,hoge_address)
# csv形式で出力する
write.csv(hoge, "hoge.csv")
```
# 参考
[R:複数ポイントの一括ジオコーディング→ggplot2でマッピングして背景にGoogleMapを重ねる。](https://qiita.com/ytakeda/items/3cd59bed1ced5e72ca3a)
[ggmapパッケージを用いて住所から緯度経度のデータを得る](https://qiita.com/koki25ando/items/fa17a17195d4abf77282)
