# README

## usersテーブル

|Column|Type|Options|
|------|----|-------|
|email|string|null: false, unique: true|
|password|string|null: false|
|username|string|null: false, unique: true|

### Association
- has_many :posts
- has_many :reviews

## postsテーブル

|Column|Type|Options|
|------|----|-------|
|name|text|null: false|
|text|text|null: false|
|image|string|null: false|
|user_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :user
- has_many :reviews
- has_many :post_tags
- has_many :tags, through: post_tags

## reviewsテーブル

|Column|Type|Options|
|------|----|-------|
|text|text|null: false|
|user_id|integer|null: false, foreign_key: true|
|post_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :post
- belongs_to :user

## post_tagsテーブル

|Column|Type|Options|
|------|----|-------|
|tag_id|integer|null: false, foreign_key: true|
|post_id|integer|null: false, foreign_key: true|

### Association
- belongs_to :tag
- belongs_to :post

## tagsテーブル

|Column|Type|Options|
|------|----|-------|
|text|text|null: false|

### Association
- has_many :post_tags
- has_many :posts, through: post_tags
