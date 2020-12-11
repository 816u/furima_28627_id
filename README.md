## users テーブル

| Column               | Type   | Options     |
| -------------------- | ------ | ----------- |
| nickname             | string | null: false |
| email                | string | null: false |
| encrypted_password   | string | null: false |
| user_last_name       | string | null: false |
| user_first_name      | string | null: false |
| user_last_name_kana  | string | null: false |
| user_first_name_kana | string | null: false |
| birthday             | date   | null: false |

### Association
- has_many :item
- has_many :comment
- has_one :buyer

## items テーブル

| Column          | Type       | Options                        |
| --------------- | ---------- | ------------------------------ |
| name            | string     | null: false                    |
| price           | integer    | null: false                    |
| category_id     | integer    | null: false                    |
| status_id       | integer    | null: false                    |
| delivery_fee_id | integer    | null: false                    |
| consignor_id    | integer    | null: false                    |
| date_id         | integer    | null: false                    |
| user            | references | null: false, foreign_key: true |
| address         | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- has_many :comment
- has_one :address

## addresses テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| item   | references | null: false, foreign_key: true |
| user   | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :item

## comments テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| text   | string     | null: false                    |
| user   | references | null: false, foreign_key: true |
| item   | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- belongs_to :item

