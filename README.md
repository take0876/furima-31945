# DB 設計

## users table

| Column               | Type     | Options     |
| ----------           | ------   | ----------- |
| nickname             | string   | null: false |
| email                | string   | null: false |
| encrypted_password   | string   | null: false |
| first_name           | string   | null: false |
| last_name            | string   | null: false |
| first_name_kana      | string   | null: false |
| last_name_kana       | string   | null: false |
| birthday             | integer  | null: false |

### Association

- has_many :products
- has_many :purchase_history
- has_many :shipping_address


## products table

| Column           | Type        | Options                        |
| ----------       | ----------  | -----------                    |
| user             | references  | null: false,foreign_key: true  |
| name             | string      | null: false                    |
| price            | references  | null: false                    |
| description      | text        | null: false                    |
| seller           | references  | null: false                    |
| category         | references  | null: false,foreign_key: true  |
| condition        | references  | null: false, foreign_key: true |

| delivery_charge  | references  | null: false, foreign_key: true |
| prefecture       | references  | null: false, foreign_key: true |
| delivery_way     | references  | null: false, foreign_key: true |


### Association

- belongs_to :user

## purchase_history table

| Column       | Type        | Options                        |
| ----------   | ----------  | -----------                    |
| user_id      | references  | null: false,foreign_key: true  |
| products_id  | references  | null: false,foreign_key: true  |

### Association

has_many :products
has_many :user

## shipping_address table

| Column       | Type        | Options                        |
| ----------   | ----------  | -----------                    |
| user_id      | references  | null: false,foreign_key: true  |
| products_id  | references  | null: false,foreign_key: true  |

### Association

has_many :products
has_many :user