# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

# ChatSpace DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|username|string|null: false, unique: true|
|email|string|null: false, unique: true|
|password|string|null: false|
### Association
- has_mane :groups_users
- has_many :groups, through: :groups_users
- has_many :chats


## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|string|null: false, unique: true|
### Association
- has_many :users, through: :groups_users
- has_many :groups_users
- has_many :chats


## chatsテーブル
|Column|Type|Options|
|------|----|-------|
|message|text||
|image|string||
|user_id|integer|null: false, foreign_key": true|
|group_id|integer|null: false, foreign_key": true|
### Association
- belongs_to :user
- belongs_to :group


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user