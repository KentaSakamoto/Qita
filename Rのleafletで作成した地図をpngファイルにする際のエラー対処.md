---
title: Rのleafletで作成した地図をpngファイルにする際のエラー対処
tags: R leaflet mapView htmltools
author: motsu_engineering
slide: false
---
# 状況
すでにleafletでmという変数にデータを入れている状況で、そのmをhtmlファイルではなく、pngファイルとして、画像として出力したい状況。
# エラー
```R
PhantomJS not found. You can install it with webshot::install_phantomjs(). If it is installed, please make sure the phantomjs executable can be found via the PATH variable.
```
# 解決策
```R
webshot::install_phantomjs()
```
を実行する。
# コード
```R
library(htmltools)
library(magrittr)
library(leaflet)
library(mapview)
webshot::install_phantomjs()

mapview::mapshot(m, file = paste0(getwd(), 
    "/tokyo_DID.png"))
```
# 参考
[PマップまたはjpgファイルとしてRマップにLeafletを保存する方法？ - コードログ](https://codeday.me/jp/qa/20190301/343512.html)
[leafletで描画した地図を画像ファイルとして保存する - cucumber flesh](https://uribo.hatenablog.com/entry/2017/03/28/204000)
[How to save Leaflet in R map as png or jpg file? - Stack Overflow](https://stackoverflow.com/questions/31336898/how-to-save-leaflet-in-r-map-as-png-or-jpg-file)
