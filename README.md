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
![スクリーンショット 2020-10-06 19 26 55](https://user-images.githubusercontent.com/57664012/95193167-54c9ae80-080e-11eb-94f1-64f620546364.png)  
・ユーザーが登録したタスクの一覧を表示する  
・タスクの検索機能を実装、名称と登録日時の検索でタスクをスムーズに見つけるころができる  
・タスク欄にページネーション（kaminari）を実装。視覚的に見やすくタスクの一覧を表示する  
・編集、削除ボタンでスムーズなアクションが可能  
・タスク名称をクリックすることで詳細画面に遷移することが可能      

タスク新規登録画面  
![スクリーンショット 2020-10-06 20 27 16](https://user-images.githubusercontent.com/57664012/95196148-9eb49380-0812-11eb-86d0-82c1197d074e.png)  
・タスクの新規登録を行うことができる  
・active＿storageを採用し、画像の添付が可能。よりタスクに詳細な情報を与えることができる      


タスク詳細表示画面  
![スクリーンショット 2020-10-06 19 41 18](https://user-images.githubusercontent.com/57664012/95193318-99554a00-080e-11eb-86e3-5116c74b8c64.png)  
・タスクに登録された情報を確認することができる      
  


タスク編集画面  
![スクリーンショット 2020-10-06 19 46 14](https://user-images.githubusercontent.com/57664012/95193361-ad00b080-080e-11eb-949a-8ea171c0f459.png)  
・登録したタスクの編集をすることができる  
・画像は新たな画像を上書きすることが可能      
  
  
  


タスク削除画面  
![スクリーンショット 2020-10-06 19 48 59](https://user-images.githubusercontent.com/57664012/95193440-cb66ac00-080e-11eb-80d2-e7f06ff9fd23.png)
![スクリーンショット 2020-10-06 19 49 23](https://user-images.githubusercontent.com/57664012/95193497-de797c00-080e-11eb-8fe9-629367415d34.png)  
・登録したタスクの削除が可能、削除ボタンから削除のアクションに遷移      

ログイン画面  
![スクリーンショット 2020-10-06 19 50 49](https://user-images.githubusercontent.com/57664012/95193582-fc46e100-080e-11eb-8823-7bc284bdd139.png)  
・登録したメールアドレス、パスワードを入力しログインすることができる  
・ログインが成功した際はユーザーのタスク一覧画面に遷移      
  
  
  
ユーザー新規登録画面  
![スクリーンショット 2020-10-06 19 51 12](https://user-images.githubusercontent.com/57664012/95193665-1da7cd00-080f-11eb-806f-1e8f6b4cf73d.png)  
・ユーザー自身で新規登録を行うことができる  
・メールアドレスは既に登録された物は使用できないように制限      
  
  
  

・工夫したポイント  
タスクの保存、確認を主な目的としているのでなるべく複雑な機能は省き使い易いアプリを目指した。  
また、タスク一覧画面でページネーションや検索機能を導入することで登録したタスクをより素早く確認できるようなレイアウトや機能を意識して作成を行った

・使用した技術  
  
バックエンド  
Ruby,Ruby on Rails  
  

フロントエンド  
html、Slim  
  
  
データベース  
MySQL  
  
  
ソース管理  
Github、GithubDesktop  
  
  
エディタ  
VSCode  
  
  

・課題や今後実装したい機能  
 レイアウトを簡素な物ではなく見やすく工夫していきたい。  
 いくつかのタスクをまとめて一度に登録できるような機能があれば更に効率的なアプリにすることができると感じる。  
 非同期通信を導入すればよりスムーズにアクションができるのではないかと感じる




・DB設計
 # tasksテーブル
 
|Column|Type|Options|
|------|----|-------|
|name|string|null: false,unique: true|
|description|text|null: false|

## Association
belongs_to :user
has_many :active_storage_attachments

# usersテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|email|string|null: false|
|password_digest|string|null: false|

## Association
has_many :tasks

# active_storage_blobsテーブル
|Column|Type|Options|
|------|----|-------|
|key|string|null: false, unique: true|
|filename|string|null: false|
|content_type|string|
|metadata|text|
|byte_size|bigint|null: false|
|checksum|string|null: false|
|created_at|datetime|null: false|

## Assosiation
has_many :active_storage_attachments





# active_storage_attachmentsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|record|references|null: false, polymorphic: true, index: false|
|blob|references|null: false|
|created_at|datetime|null: false|

## Association
belongs_to :tasks
belongs_to :active_storage_blobs