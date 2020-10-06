# README

・アプリ名
 Taskasave

・概要  
 ログインを行い、ユーザーごとののタスクの登録,管理を行うことができる  
 タスクには画像のアップロードが可能  
 タスクは保存、編集、削除が可能  

・制作背景(意図)  
　⇒日々の作業を全て人間の頭だけでは覚えておくことは難しい、自分に課されているタスクを管理するにはポストイットやメモ帳に記載して忘れないようにしなければならない。そういった小さなメモを一つのアプリで一括して管理をしたいと思いこのアプリケーションを開発しようと考えました。

・DEMO
タスク一覧画面

タスク新規登録画面

タスク詳細表示画面

タスク編集画面

タスク削除画面

ログイン画面

ユーザー新規登録画面



・DB設計
 ## tasksテーブル
 
|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unique: true|
|description|text|null: false|

# Association
belongs_to :user
has_many :active_storage_attachments

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false|
|password_digest|string|null: false|

# Association
has_many :tasks

## active_storage_blobsテーブル
|Column|Type|Options|
|------|----|-------|
|key|string|null: false, unique: true|
|filename|string|null: false|
|content_type|string|
|metadata|text|
|byte_size|bigint|null: false|
|checksum|string|null: false|
|created_at|datetime|null: false|

# Assosiation
has_many :active_storage_attachments





## active_storage_attachmentsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|record|references|null: false, polymorphic: true, index: false|
|blob|references|null: false|
|created_at|datetime|null: false|

# Association
belongs_to :tasks
belongs_to :active_storage_blobs