# ChatSpace-データベース設計


## userテーブル
|Column|Type|Options|
|------|----|-------|
|name|text|null: false|
|address|text|null: false, unique: true|
|password|text|null: false|
### Association
- has_many :groups
- has_many :messages


## groupテーブル
|Column|Type|Options|
|------|----|-------|
|group_title|text|null: false|
|user_id|integer|null: false, foreign_key: true|
### Association
- has_many :users
- has_many :users,  through:  :groups_users
- has_many :messages


## groups_usersテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :group
- belongs_to :user


## messageテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|group_id|integer|null: false, foreign_key: true|
|message|text|null: false, foreign_key: true|
|Image|string|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :group

