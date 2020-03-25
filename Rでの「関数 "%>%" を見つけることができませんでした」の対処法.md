---
title: Rでの「関数 "%>%" を見つけることができませんでした」の対処法
tags: R leaflet digest dplyr tidyverse
author: motsu_engineering
slide: false
---
# 経緯
Rのleafletパッケージを使おうと思い、

```R
library(leaflet)
shape %>% leaflet() %>%
  addTiles() %>%
  addProviderTiles(providers$CartoDB.Positron) %>%
  addPolygons(fillOpacity = 0.5,weight = 1,fillColor = "lightblue")
```
として上記のコードを実行すると、

```
shape %>% leaflet() %>% addTiles() %>% addProviderTiles(providers$CartoDB.Positron) %>%  でエラー: 
   関数 "%>%" を見つけることができませんでした 
```
とパイプ演算子が使えない状況になった。
# 解決方法(結論)

```R
install.packages("tidyverse")
```

# 解決方法(過程)
[Error: could not find function "%>%"](https://stackoverflow.com/questions/30248583/error-could-not-find-function)を読んで、以下のコードを実行した。

```R
install.packages("magrittr") 
install.packages("dplyr")    
library(magrittr) 
library(dplyr)    
```

その結果...

```
leaflet(.) でエラー:  関数 "leaflet" を見つけることができませんでした    
```
とleafletそのもの自体もインストールできていないことが判明。

そこで、

```R
 library(leaflet)
```
を実行すると、

```
 エラー: package or namespace load failed for ‘leaflet’ in loadNamespace(i, c(lib.loc, .libPaths()), versionCheck = vI[[i]]):
  ‘digest’ という名前のパッケージはありません 
 追加情報:  警告メッセージ: 
 パッケージ ‘leaflet’ はバージョン 3.5.3 の R の下で造られました 
```
というエラーメッセージがでてきたことから、Rのバージョンの違いによるエラーであることが判明した。そこでRのバージョンをダウングレード[R-3.5.3 for Windows (32/64 bit)](https://cran.r-project.org/bin/windows/base/old/3.5.3/)して再度試してみると...

```
 shape %>% leaflet() %>% addTiles() %>% addProviderTiles(providers$CartoDB.Positron) %>%  でエラー: 
   関数 "%>%" を見つけることができませんでした 
```
と変わらず。%>%関数はtidyverseパッケージに入ってるはず...

```R
install.packages("tidyverse")
```
を行い試してみると、うまくいった!
![キャプチャ.JPG](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/299072/2af82432-3fe2-5f26-9987-f813a321aff6.jpeg)

# 参考
[Error: could not find function "%>%"](https://stackoverflow.com/questions/30248583/error-could-not-find-function)
[ R の パイプ でエラー ”関数 "%>%" を見つけることができませんでした ”Error: could not find function "%>%””](https://www.medi-08-data-06.work/entry/2018/12/19/224533)
