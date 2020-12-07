## usersテーブル
| colum               | type   | option      |
| ------------------- | ------ | ----------- |
| email               | string | null: false |
| encrypted_password  | string | null: false |
| nick_name           | string | null: false |
| last_name           | string | null: false |
| first_name          | string | null: false |
| last_name_katakana  | string | null: false |
| first_name_katakana | string | null: false |
| birthday            | date   | null: false |

## Association
has_many : products
has_many : buys


## productsテーブル
| colum            | type       | option                         |
| ---------------- | ---------- | ------------------------------ |
| name             | string     | null: false                    |
| text             | text       | null: false                    |
| price            | integer    | null: false                    |
| user             | references | null: false, foreign_key: true |
| charges_id       | integer    | null: false, foreign_key: true |
| prefectures_id   | integer    | null: false, foreign_key: true |
| days_id          | integer    | null: false, foreign_key: true |
| category_id      | integer    | null: false, foreign_key: true |
| status_id        | integer    | null: false, foreign_key: true |

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
| colum            | type       | option                         |
| ---------------- | ---------- | ------------------------------ |
| postal_code      | string     | null: false                    |
| prefectures_id   | integer    | null: false, foreign_key: true |
| city             | string     | null: false                    |
| address          | string     | null: false                    |
| building_name    | string     | null: false                    |
| phone_number     | string     | null: false                    |
| buy              | references | null: false, foreign_key: true |

## Association
belongs_to : buys
belongs_to : prefectures


## ActiveHash //モデルのみ制作
| model_name  | Association                                    |
| ----------- | ---------------------------------------------- |
| charges     |has_many: products                              |
| prefectures |has_many: products,belongs_to:buyer_information |
| days        |has_many: products                              |
| category    |has_many: products                              |
| status      |has_many: products                              |