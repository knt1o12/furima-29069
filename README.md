##usersテーブル
<!-- ユーザー情報 -->

|Column  |Type  |Options      |
|--------|-------|------------|
|nickname|varchar|null: false |
|email   |varchar|unique: true|
|password|char   |null: false |
<!-- 
ニックネーム
メールアドレス
パスワード
 -->

### Association
has_many :items
has_one :purchase_record

##itemsテーブル
<!-- 商品情報 -->

|Column        |Type    |Options          |
|--------------|------- |-----------------|
|image         |string  |null: false      |
|name          |string  |null: false      |
|introduction  |text    |null: false      |
|category      |string  |foregin_key: true|
|condition     |string  |null: false      |
|postage       |boolean |null: false      |
|ship_form     |string  |foregin_key: true|
|shiipping_date|datetime|foregin_key: true|
|price         |integer |null: false      |
|user_id       |integer |foregin_key: true|
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


##purchase_recordテーブル
<!-- 購入記録 -->

|Column  |Type  |Options      |
|--------|-------|------------|
|user_id |string |null: false |
|item_id |string |null: false |

### Association
belongs_to :user
belongs_to :items
has_one : shipping_address

##shipping_addressテーブル
<!-- 住所（発送先) -->

|Column      |Type   |Options          |
|------------|-------|-----------------|
|postal code |integer|null: false      |
|prefecture  |string |foregin_key: true|
|municipality|string |null: false      |
|address     |string |null: false      |
|phone_number|integer|null: false      |
<!--
 郵便番号
 都道府県
 市区町村
 番地
 電話番号
 -->

 ### Association
belongs_to :purchase_record
