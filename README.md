## users テーブル

| Column           | Type   | Options     |
| ---------------- | ------ | ----------- |
| nickname         | string | null: false |
| mail             | string | null: false |
| password         | string | null: false |
| password_confirm | string | null: false |
| user_name        | string | null: false |
| birthday         | string | null: false |

### Association
- has_many :item
- has_many :comment
- has_one :buyer

## items テーブル

| Column       | Type       | Options                        |
| ------------ | ---------- | ------------------------------ |
| item_name    | string     | null: false                    |
| image        | string     | null: false                    |
| price        | string     | null: false                    |
| category     | string     | null: false                    |
| status       | string     | null: false                    |
| delivery_fee | string     | null: false                    |
| consignor    | string     | null: false                    |
| date         | string     | null: false                    |
| user         | references | null: false, foreign_key: true |
| buyer        | references | null: false                    |

### Association
- belongs_to :user
- has_many :comment
- belongs_to :buyer

## buyers テーブル

| Column    | Type       | Options                        |
| --------- | ---------- | ------------------------------ |
| address   | string     | null: false                    |
| card_info | string     | null: false                    |
| user      | references | null: false, foreign_key: true |

### Association
- belongs_to :user
- has_one :item

## comments テーブル

| Column | Type       | Options                        |
| ------ | ---------- | ------------------------------ |
| text   | references | null: false, foreign_key: true |
| user   | references | null: false, foreign_key: true |
| item   | string     | null: false                    |

### Association
- belongs_to :user
- belongs_to :item

