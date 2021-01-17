##usersテーブル
<!-- ユーザー情報 -->

|Column            |Type  |Options     |
|------------------|------|------------|
|nickname          |string|null: false |
|email             |string|null: false, unique: true |
|encrypted_password|string|null: false |
|last_name         |string|null: false |
|first_name        |string|null: false |
|last_name_kana    |string|null: false |
|first_name_kana   |string|null: false |
|birthday          |string|null: false |
<!-- 
ニックネーム
メールアドレス
パスワード
姓
名
姓（フリガナ）
名（フリガナ）
誕生日
 -->

### Association
has_many :items
has_many :purchase_record

##itemsテーブル
<!-- 商品情報 -->

|Column        |Type       |Options          |
|-----------------|--------|-----------------|
|name             |string  |null: false      |
|introduction     |text    |null: false      |
|category_id      |integer |null: false      |
|condition_id     |integer |null: false      |
|postage_id       |integer |null: false      |
|ship_form_id     |integer |null: false      |
|shiipping_date_id|integer |null: false      |
|price            |integer |null: false      |
|user_id          |integer |foregin_key: true|
<!-- 
画像
商品名
商品の説明
カテゴリー
商品の状態
配送料の負担
発送元の地域
発送までの日数
価格
ユーザーid
 -->

### Association
belongs_to :user
has_one : purchase_record


##purchase_recordテーブル
<!-- 購入記録 -->

|Column  |Type    |Options      |
|--------|--------|------------|
|user_id |integer |foreign_key |
|item_id |integer |foreign_key |

### Association
belongs_to :user
belongs_to :item
has_one : shipping_address

##shipping_addressテーブル
<!-- 住所（発送先) -->

|Column             |Type   |Options          |
|-------------------|-------|-----------------|
|postal code        |string |null: false      |
|prefecture_id      |integer|null:false       |
|municipality       |string |null: false      |
|address            |string |null: false      |
|building           |string |                 |
|phone_number       |string |null: false      |
|purchase_record_id |integer|null: false      |
<!--
 郵便番号
 都道府県
 市区町村
 番地
 建物名
 電話番号
 購入記録id
 -->

 ### Association
belongs_to :purchase_record
