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

## membersテーブル

|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key|
|group_id|references|null: false, foreign_key|

### Association
- belongs_to :group
- belogns_to :user

## groupsテーブル

|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|

### Association
- has_many :messages
- has_many :members
- has_many :users, through: :members

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false, unique: true|
|email|string|null: false, unique: true|

### Association
- has_many :messages
- has_many :members
- has_many :groups, through: :members

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|
|image|string|
|group_id|referenes|null: false, foreign_key: true|
|user_id|references|null: false, foreign_key: true|

### Associationテーブル
- belongs_to :group
- belongs_to :user
