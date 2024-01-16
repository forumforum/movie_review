# DB 設計

## movies table

| Column             | Type                | Options                        |
|--------------------|---------------------|--------------------------------|
| title              | string              | null: false                    |
| trailer            | string              | null: false                    |
| genre              | string              | null: false                    |
| director           | string              | null: false                    |
| screen_time        | integer             | null: false                    |
| release_year       | integer             | null: false                    |
| synopsis           | text                | null: false                    |


### Association

- has_many :reviews
- has_many :favorite_movies
- has_many :watched_movies

## reviews table

| Column               | Type              | Options                        |
|----------------------|-------------------|--------------------------------|
| user_id              | references        | null: false, foreign_key: true |
| movie_id             | references        | null: false, foreign_key: true |
| evaluation           | integer           | null: false                    |
| text                 | text              | null: false                    |
| spoiler              | boolean           | default: false                 |
| created_at           | datetime          | null: false                    |
| updated_at           | datetime          | null: false                    |

### Association

- belongs_to :user
- belongs_to :movie

## users table

| Column             | Type                | Options                       |
|--------------------|---------------------|-------------------------------|
| email              | string              | null: false, unique: true     |
| encrypted_password | string              | null: false                   |
| nickname           | string              | null: false                   |


### Association

- has_many :reviews
- has_many :favorite_movies
- has_many :watched_movies


## favorite_movies table

| Column              | Type               | Options                        |
|---------------------|--------------------|--------------------------------|
| movie_id            | references         | null: false, foreign_key: true |
| user_id             | references         | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :movie

## watched_movies table

| Column               | Type              | Options                        |
|----------------------|-------------------|--------------------------------|
| movie_id             | references        | null: false, foreign_key: true |
| user_id              | references        | null: false, foreign_key: true |

### Association

- belongs_to :movie
- belongs_to :user
