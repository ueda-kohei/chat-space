# README

# ユーザー管理機能

## ユーザー管理機能テーブル

|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|name|text|null: false|
|address|text|null: false, unique: true|
|password|text|null: false|


# グループ制作機能

## userテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_title|text|null: false|
### Association
- has_many :user_groups
- has_many :groups, through: :user_groups

## groupテーブル
|Column|Type|Options|
|------|----|-------|
|group_title|text|null: false|
|group_id|integer|null: false, foreign_key: true|
### Association
- has_many :user_groups
- has_many :users, through: :user_groups

## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


# チャットメッセージ機能

## Bodyテーブル
|Column|Type|Options|
|------|----|-------|
|Body|text|null: false, foreign_key: true|
|group_title|text|null: false|
### Association
- has_many :Body_Images
- has_many :Images, through: :Body_Images

## Imageテーブル
|Column|Type|Options|
|------|----|-------|
|Image|string|null: false, foreign_key: true|
|group_title|text|null: false|
### Association
- has_many :Body_Images
- has_many :bodies, through: :Body_Images

## body_imageテーブル
|Column|Type|Options|
|------|----|-------|
|Body|text|null: false, foreign_key: true|
|Image|string|null: false, foreign_key: true|
### Association
- belongs_to :Body
- belongs_to :Image