---
title: gzファイル・tarファイルの展開
tags: Linux 初心者 Windows コマンド
author: motsu_engineering
slide: false
---
# はじめに
この記事は自分が躓いた部分の備忘録です。
[追記]
自分はコマンドプロンプトではなく、git bashで下記コマンドを実行しました。

# 状況
gzファイルという形式でデータをインストールしましたが、windowsで普段はzip形式でファイルを圧縮・展開しているので、展開方法がわかりませんでした。(とりあえず、圧縮ファイルであることはわかりました。)

# 解決法

### gzファイルの展開

```sh
gzip -d ファイル名.gz
```
### tarファイルの展開

```sh
tar xf ファイル名.tar
```
# 終わりに
コマンド集は[圧縮展開系のコマンドのまとめ](https://qiita.com/wnoguchi/items/cb0fa7c11b119e96f1e5)にまとまっているので、参考にしてください。



[追記]
また[まとめてgzファイルを展開する](http://idacchi-tech.hatenablog.com/entry/2016/04/13/170822)
を参照してもらえれば、同一ファイル内の複数のgzファイルを一度に展開することができます。

```sh
find . -name "*.gz" -print0 | xargs -0 -n1 gzip -d
```

# 参考(2020/1/7 アクセス)
[linux tar.gzの圧縮・解凍 メモ](https://qiita.com/HyunwookPark/items/047ba2da9ef16bcac356) 
[圧縮されたアーカイブファイルが展開出来ない！(ソースコードを自分でコンパイルした時のトラブルシューティング)](https://mekou.com/linux-magazine/%E5%9C%A7%E7%B8%AE%E3%81%95%E3%82%8C%E3%81%9F%E3%82%A2%E3%83%BC%E3%82%AB%E3%82%A4%E3%83%96%E3%83%95%E3%82%A1%E3%82%A4%E3%83%AB%E3%81%8C%E5%B1%95%E9%96%8B%E5%87%BA%E6%9D%A5%E3%81%AA%E3%81%84%EF%BC%81/)
[圧縮展開系のコマンドのまとめ](https://qiita.com/wnoguchi/items/cb0fa7c11b119e96f1e5)
[tarおよびgzipについて](http://www.kyoshin.bosai.go.jp/kyoshin/man/targzip.html)
[まとめてgzファイルを展開する](http://idacchi-tech.hatenablog.com/entry/2016/04/13/170822)
