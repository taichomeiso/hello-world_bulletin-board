# テーブル設計


## users table

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| name               | string | null: false |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false |

### Association

- has_many :threads
- has_many :messages
- has_many :comments

## threads table

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| title              | string | null: false |
| user_id            | bigint | null: false, foreign_key: true|

### Association

- belongs_to :user
- has_many :comments

## comments 

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | text       |                                |
| user_id    | bigint | null: false, foreign_key: true |
| thread_id  | bigint | null: false, foreign_key: true |

### Association

- belongs_to :thread
- belongs_to :user

## messages table

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | text       |                                |
| user_id    | bigint | null: false, foreign_key: true |
| receiver_id| bigint | null: false, foreign_key: { to_table: :users } |


### Association

- belongs_to :user
- belongs_to :receiver, class_name: 'User'





