## usersテーブル
| colum               | type   | option                    |
| ------------------- | ------ | ------------------------- |
| email               | string | null: false, unique: true |
| encrypted_password  | string | null: false               |
| nick_name           | string | null: false               |
| last_name           | string | null: false               |
| first_name          | string | null: false               |
| last_name_katakana  | string | null: false               |
| first_name_katakana | string | null: false               |
| birthday            | date   | null: false               |

## Association
has_many : products
has_many : buys


## productsテーブル
| colum         | type       | option      |
| ------------- | ---------- | ----------- |
| name          | string     | null: false |
| text          | text       | null: false |
| price         | integer    | null: false |
| user          | references | null: false |
| charge_id     | integer    | null: false |
| prefecture_id | integer    | null: false |
| day_id        | integer    | null: false |
| category_id   | integer    | null: false |
| status_id     | integer    | null: false |

## Association
belongs_to : user
has_one : buy


## buysテーブル
| colum             | type       | option                         |
| ----------------- | ---------- | ------------------------------ |
| product           | references | null: false, foreign_key: true |
| user              | references | null: false, foreign_key: true |

## Association
belongs_to : product
belongs_to : user
has_one : buyer_information


## buyer_informationテーブル
| colum         | type       | option                         |
| ------------- | ---------- | ------------------------------ |
| postal_code   | string     | null: false                    |
| prefecture_id | integer    | null: false                    |
| city          | string     | null: false                    |
| address       | string     | null: false                    |
| building_name | string     |                                |
| phone_number  | string     | null: false                    |
| buy           | references | null: false, foreign_key: true |

## Association
belongs_to : buy


## ActiveHash //モデルのみ制作
| model_name | Association                                     |
| ---------- | ----------------------------------------------- |
| charge     |has_many: products                               |
| prefecture |has_many: products, belongs_to:buyer_information |
| day        |has_many: products                               |
| category   |has_many: products                               |
| status     |has_many: products                               |