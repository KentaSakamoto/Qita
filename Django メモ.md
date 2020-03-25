---
title: Django メモ
tags: Django Python
author: motsu_engineering
slide: false
---
# py36ファイルをアクティベートする
```shell
activate py36
```

# ファイルのを一覧で確認
```shell
dir
```

# Djangoアプリを構築する
```django
django-admin startproject プロジェクト名 
```

# サーバーを起動する
```django
python manage.py runserver
```
# データの結合・統合を行う
```django
python manage.py migrate
```
# アプリケーションの追加
```django
python manage.py startapp アプリケーション名(複数形の名前が良い)
```
# 新しい定義ファイルを自動生成する
```django
python manage.py makemigrations
```
# データベースにアクセスする
```django
sqlite3 db.sqlite3
```
# Djangoの管理画面にアクセスするためにアカウントを作成する
```django
python manage.py createsuperuser
```
