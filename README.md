# テーブル設計


## users table

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| name               | string | null: false |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false |
| comments_count     | integer | null:false, default: 0 |

### Association

- has_many :threads
- has_many :messages, foreign_key: :sender_id
- has_many :comments
- has_one :level

## threads table

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| title              | string | null: false |
| user_id            | bigint | null: false, foreign_key: true|

### Association

- belongs_to :user
- has_many :comments, dependent: :destroy

## comments table

| Column     | Type   | Options                       |
| ---------- | ------ | ----------------------------- |
| content    | text   | null: false                   |
| user_id    | bigint | null: false, foreign_key: true |
| thread_id  | bigint | null: false, foreign_key: true |

### Association

- belongs_to :thread,counter_cache: true
- belongs_to :user,counter_cache: true


## messages table

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| content | text       |                                |
| sender_id  | bigint | null: false, foreign_key: { to_table: :users } |
| receiver_id| bigint | null: false, foreign_key: { to_table: :users } |


### Association

- belongs_to :sender, class_name: 'User'
- belongs_to :receiver, class_name: 'User'

## levels table

| Column  | Type       | Options                        |
| ------- | ---------- | ------------------------------ |
| level      | integer |  null:false,default:0 |
| user_id    | bigint | null: false, foreign_key: true |

### Association

- belongs_to :user







