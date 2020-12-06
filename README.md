## usersテーブル
| colum               | type    | option   |
| ------------------- | ------- | -------- |
| email               | strings | NOT NULL |
| password            | strings | NOT NULL |
| nick_name           | strings | NOT NULL |
| last_name           | strings | NOT NULL |
| first_name          | strings | NOT NULL |
| last_name_katakana  | strings | NOT NULL |
| first_name_katakana | strings | NOT NULL |

## Association
has_many : Products
has_many : comments


## productsテーブル
| colum            | type       | option   |
| ---------------- | ---------- | -------- |
| name             | strings    | NOT NULL |
| text             | text       | NOT NULL |
| price            | integer    | NOT NULL |
| shipping_charges | strings    | NOT NULL |
| shipping_area    | strings    | NOT NULL |
| shipping_days    | strings    | NOT NULL |
| details_category | strings    | NOT NULL |
| details_status   | strings    | NOT NULL |
| user             | references | NOT NULL |

## Association
belongs_to : users
has_one : buy
has_many : comment


## commentテーブル
| colum            | type       | option   |
| ---------------- | ---------- | -------- |
| text             | text       | NOT NULL |
| user             | references | NOT NULL |
| product          | references | NOT NULL |

## Association
belongs_to : users
belongs_to : products


## buyテーブル
| colum                | type       | option   |
| -------------------- | ---------- | -------- |
| card_number          | integer    | NOT NULL |
| expiration_date      | integer    | NOT NULL |
| security_code        | integer    | NOT NULL |
| product_id           | references | NOT NULL |
| buyer_information_id | references | NOT NULL |

## Association
belongs_to : products
has_one : buyer_information


## buyer_informationテーブル
| colum        | type       | option   |
| ------------ | ---------- | -------- |
| postal_code  | strings    | NOT NULL |
| prefectures  | strings    | NOT NULL |
| city         | strings    | NOT NULL |
| address      | strings    | NOT NULL |
| phone_number | integer    | NOT NULL |
| buy_id       | references | NOT NULL |

## Association
belongs_to : buy