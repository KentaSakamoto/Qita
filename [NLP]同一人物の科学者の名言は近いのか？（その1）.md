---
title: [NLP]同一人物の科学者の名言は近いのか？（その1）
tags: COTOHA Python 自然言語処理
author: motsu_engineering
slide: false
---
# はじめに
来春B4になる予定の大学生です。最近自然言語処理に触れる機会があったので、思いついたネタでCOTOHA APIを試してみました。
# アイデア
同じ人物の名言が似ているかどうか！
という至極単純な発想です...
# 結果
コードについては[COTOHA 類似度算出APIを使って、FAQ検索システムを構築してみた](https://qiita.com/yukihon_lab/items/d7b2a5b4efd75d5edb04)を参考にさせていただきました。
では以下が結果となります。
岡潔さんの「人は極端になにかをやれば必ず好きになるという性質をもっています。好きにならぬのがむしろ不思議です。」と「人間が人間である中心にあるものは科学性でもなければ論理性でもなく理性でもない情緒である。」の類似度を比較してみました。
類似度は 0.877827 で同じ人の言葉であるだけにかなり近い結果が算出されました。

今後はさらに発展させていきたいと思います。
# 参考(全て2020/03/15アクセス)
[COTOHA API | NTTコミュニケーションズが開発した日本最大級の日本語辞書を活用した自然言語処理、音声認識APIプラットフォーム
](https://api.cecotoha.com/contents/index.html)

[COTOHA 類似度算出APIを使って、FAQ検索システムを構築してみた](https://qiita.com/yukihon_lab/items/d7b2a5b4efd75d5edb04)

[岡潔の名言 | 地球の名言](http://earth-words.org/archives/15232)
