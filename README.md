# テーブル設計

# direct message table

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


