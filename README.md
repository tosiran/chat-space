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

# DB設計
## usersテーブル
|Column|Type|Options|
|------|----|-------|
|username|string|null: false|
|email|string|null: false|
|password|string|null: false|
### Association
- has_many :messages
- has_many :groups

## groupsテーブル
|Column|Type|Options|
|------|----|-------|
|groupname|text|null: false|
|user_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- has_many :messages
- has_many :group_members
- has_many  :menbers,  through:  :group_members

## menbersテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
### Association
- has_many :group_members
- has_many  :group,  through:  :group_members

## group_membersテーブル
|Column|Type|Options|
|------|----|-------|
|group_id|integer|null: false, foreign_key: true|
|menber_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :member

## messagesテーブル
|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|image|text||
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


