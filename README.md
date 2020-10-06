# README

・アプリ名
 Taskapp

・概要(このアプリでできることを書いて下さい)
 ログインを行い、自分のタスクの登録を行う音ができる
 タスクは画像のアップロードが可能

・制作背景(意図)
　⇒日々の作業や予定の管理を行うため

・DEMO


・DB設計
 ## tasksテーブル
 
|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unique: true|
|description|text|null: false|

# Assosiation
belongs_to :user

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false|
|password_digest|string|null: false|

# Assosiation
has_many :tasks

