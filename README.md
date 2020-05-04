# README


# freemarket_70c DB 設計


## usersテーブル

|Columm|Type|Options|
 |:------|:----|:-------|
 |family_name|string|null: false|
 |first_name|string|null: false|
 |family_name_kana|string|null: false|
 |first_name_kana|string|null:false|
 |nickname|string|null: :false|
 |e-mail|string|null: ：false|
 |number|integer|null: :false|
 |encrypted_password|string|null: :false|
 |password_confirmation|string|null: false|
 |gender|integer|null: :false|
 |birth_year|integer|null: false|
 |birth_month|integer|null: false|
 |birth_day|integer|null: false|
 |introduction|text||
 |user_image|string||


 ## Association
 has_many :cards
 has_many :addresses
 has_many :items
 has_many :comments


 ## index
 add_index: [:nickname, :e-mail]


 ## addressesテーブル
 |colum|type|Opsion|
 |:------|:----|:-------|
 |family_name|string|null: false|
 |first_name|string|null: false|
 |family_name_kana|string|null: false|
 |first_name_kana|string|null:false|
 |postal_code|string|null: false|
 |prefecture|string|null: false|
 |local|string|null: false|
 |local_number|string|null: false|
 |buildig|string||
 |user_id|integer|null: false, foreign_key: true|

 ## Association
 belongs_to :user

 ## index
 add_index: [:prefecture, :user_id]


 ## Cardsテーブル
 |Column|Type|Options|
 |:------|:----|:-------|
 |card_number|integer|null: false,|
 |name|string|null: false|
 |CVC|integer|null: false|
 |limit_date|integer|null: false|
 |user_id|integer|null: false, foreign_key: true|

 ## Association
 belongs_to :user

 ## index
 add_index: [:user_id]

 ## commentsテーブル
 |Column|Type|Options|
 |:------|:----|:-------|
 |user_id|integer|null: false,foreign_key: true|
 |item_id|integer|null: false,foreign_key: true|
 |text|text|null: :false|

 ## Association
 belongs_to :user
 belongs_to :item

 ## index
 add_index: [:user_id, :item_id]


 ## itemsテーブル
 |Column|Type|Options|
 |:------|:----|:-------|
 |user_id|integer|foreign_key: true|
 |name|string|null:：false|
 |description|text|null: :false|
 |price|integer|null:：false|
 |buyer_id|integer||
 |size|string||
 |condition|string|null: :false|
 |wait|string|null: :false|
 |postage|integer|null: :false|
 |category_id|integer|null: :false, foregin_key: :true|
 |brand_id|integer|null: :false, foregin_key: :true|
 |prefecture_id|integer|null: :false|
 
 ## Association
 belongs_to :user
 has_many :comments
 has_many :images
 belongs_to :brand
 belongs_to :category

 ## index
 add_index: [:name, :price]


 ## imagesテーブル
 |Column|Type|Options|
 |:------|:----|:-------|
 |src|string|null: false|
 |item_id|integer|null: false, foreign_key: true|

 ## Association
 belongs_to :item


 ## Brandsテーブル
 |Column|Type|Options|
 |:------|:----|:-------|
 |name|string|null: false|
 
 ## Association
 has_many :items

 ## index
 add_index: :name


 ## Categoriesテーブル
 |Column|Type|Options|
 |:------|:----|:-------|
 |name|string|null: false|
 |ancestry|string|
 
 ## Association
 has_many :items

 ## index
 add_index: [:name]
