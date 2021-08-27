# テーブル設計

## circles テーブル

| Column             | Type   | Options    |
| ------------------ | ------ | ---------- |
| email              | string | null:false |
| encrypted_password | string | null:false |
| name               | string | null:false |
| university         | string |            |
| people             | string |            |
| gender             | string |            |
| frequency          | string |            |
| introduction       | string |            |

### Association
- has_many :tweets
- has_many :comments

## users テーブル

| Column             | Type   | Options    |
| ------------------ | ------ | ---------- |
| email              | string | null:false |
| encrypted_password | string | null:false |
| nickname           | string | null:false |
| university         | string |            |

### Association
- has_many :comments

## tweets テーブル

| Column | Type       | Options           |
| ------ | ---------- | ----------------- |
| text   | text       | null:false        |
| circle | references | foreign_key: true |

### Association
- belongs_to :circle
- has_many :comments

## comments テーブル
| Column | Type       | Options           |
| ------ | ---------- | ----------------- |
| text   | text       | null:false        |
| circle | references | foreign_key: true |
| user   | references | foreign_key: true |
| tweet  | references | foreign_key: true |

### Association
- belongs_to :circle
- belongs_to :user
- belongs_to :tweet