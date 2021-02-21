# DB 設計

## users table

| Column               | Type     | Options                  |
| ----------           | ------   | ----------------------   |
| nickname             | string   | null: false              |
| email                | string   | null: false,unique: true |
| encrypted_password   | string   | null: false              |
| first_name           | string   | null: false              |
| last_name            | string   | null: false              |
| first_name_kana      | string   | null: false              |
| last_name_kana       | string   | null: false              |
| birthday             | integer  | null: false              |

### Association

- has_many :products
- has_many :purchase_histories
- has_many :addresses
- has_one :card


## products table

| Column           | Type        | Options                           |
| ----------       | ----------  | -----------                       |
| user_id          | references  | null: false,foreign_key: true     |
| name             | string      | null: false                       |
| price            | integer     | null: false                       |
| description      | text        | null: false                       |
| category         | integer     | null: false,foreign_key: true     |
| condition        | integer     | null: false, foreign_key: true    |
| delivery_charge  | integer     | null: false, foreign_key: true    |
| prefecture       | integer     | null: false, foreign_key: true    |
| delivery_way     | integer     | null: false, foreign_key: true    |


### Association

- belongs_to :user
- has_many :addresses

## purchase_histories table

| Column       | Type        | Options                             |
| ----------   | ----------  | -----------                         |
| user         | references  | null: false,foreign_key: true       |
| product      | references  | null: false,foreign_key: true       |

### Association

- belongs_to :product
- belongs_to :user

## addresses table

| Column          | Type        | Options                         |
| ----------      | ----------  | -----------                     |
| user_id         | references  | null: false,foreign_key: true   |
| postal_code     | string      | null: false,foreign_key: true   |
| prefecture      | references  | null: false,foreign_key: true   |
| city            | references  | null: false,foreign_key: true   |
| block_number    | references  | null: false,foreign_key: true   |
| building_name   | references  | null: false,foreign_key: true   |
| phone_number    | references  | null: false,foreign_key: true   |

### Association

- belongs_to :user
- belongs_to :product

##  cards table

| Column       | Type        | Options                        |
| ----------   | ----------  | -----------                    |
| user_id      | references  | null: false,foreign_key: true  |
| customer_id  | string      | null: false                    |
| card_id      | string      | null: false                    |

### Association

- has_one :user
- belongs_to :product