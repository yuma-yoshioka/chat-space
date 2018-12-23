# DB設計

## membersテーブル

| Column | Type | Options |
| ------ | ---- | ------- |
| user_id | references | null: false, foreign_key: true |
| group_id | references | null: false, foreign_key: true |

### Association
- belongs_to :group
- belongs_to :user

## userテーブル

| Column | Type | Options |
| ------ | ---- | ------- |
| user_name | string | null: false, index:true, unique: true |
| email | string | null: false, unique: true |

### Association
- has_many :members
- has_many :messages
- has_many :groups through :members

## groupテーブル

| Column | Type | Options |
| ------ | ---- | ------- |
| group_name | integer | null: false |

### Association
- has_many :members
- has_many :messages
- has_many :users through :members

## messageテーブル

| Column | Type | Options |
| ------ | ---- | ------- |
| body | text |  |
| image | string |  |
| user_id | references | null: false, foreign_key: true |
| group_id | references | null: false, foreign_key: true |

### Association
- belongs_to :group
- belongs_to :user
