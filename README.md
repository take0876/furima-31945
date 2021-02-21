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
| birthday             | date     | null: false              |

### Association

- has_many :products
- has_many :purchase_histories


## products table

| Column              | Type        | Options                           |
| ----------          | ----------  | -----------                       |
| user                | references  | null: false,foreign_key: true     |
| name                | string      | null: false                       |
| price               | integer     | null: false                       |
| description         | text        | null: false                       |
| category_id         | integer     | null: false,foreign_key: true     |
| condition_id        | integer     | null: false, foreign_key: true    |
| delivery_charge_id  | integer     | null: false, foreign_key: true    |
| prefecture_id       | integer     | null: false, foreign_key: true    |
| delivery_way_id     | integer     | null: false, foreign_key: true    |


### Association

- belongs_to :user
- has_one :addresses
- has_one :purchase_history

## purchase_histories table

| Column       | Type        | Options                             |
| ----------   | ----------  | -----------                         |
| user         | references  | null: false,foreign_key: true       |
| product      | references  | null: false,foreign_key: true       |

### Association

- belongs_to :product
- belongs_to :user
- has_one :address

## addresses table

| Column              | Type        | Options                              |
| ----------          | ---------   | -----------                          |
| postal_code         | string      | null: false                          |
| prefecture_id       | integer     | null: false,foreign_key: true        |
| city                | string      | null: false                          |
| block_number        | string      | null: false                          |
| building_name       | string      | null: false                          |
| phone_number        | string      | null: false                          |
| purchase_history_id | references  | null: false,foreign_key: true        |

### Association

- belongs_to :purchase_history