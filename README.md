### 4. Heroku 사용하기

> #### 1]. heroku 설치
>
> ```
> # 1. ubuntu에서 설치해주기
> $ wget -qO- https://cli-assets.heroku.com/install-ubuntu.sh | sh
> $ heroku login
>
> # 2. Gemfile 변경하기
> 1. gem 'sqlite3' -> group :development do 함수안으로 옮겨준다 end
> 2. gem 'pg' 맨 위에 추가함
> 3. $ bundle install
>
> # 3. 다시 ubuntu에서 설치하기
> $ sudo apt-get install postgresql
> $ sudo apt-get install postgresql-common
> $ sudo apt-get install postgresql-9.5 libpq-dev
> $ bundle install
>
> # 4. confing 폴더 -> database.yml
> production:
>  <<: *default
>  database: db/production.sqlite3  
> # 을 지우고
>  default: &default
>  adapter: postgresql
>  encoding: unicode
>  # For details on connection pooling, see rails configuration guide
>  # http://guides.rubyonrails.org/configuring.html#database-pooling
>  pool: 5
> # 을 추가해줌 
>
> # 5. Heroku gems 추가하기
> # 먼저 Gemfile에 추가하기
> gem 'rails_12factor', group: :production
> $ bundle install
> ruby "2.3.5" 추가해줌
>
> # 6. git을 통해서 저장하기 # ubuntu 프로젝트 폴더안에서 시작할꺼임
> 1) $ git init
> 2) $ git add .
> 3) $ git commit -m "init"
> 4) $ heroku create
> 5) $ git push heroku master
>
> # 데이터 관리할 때 사용함
> 1) heroku run rake db:migrate
>
> # 그리고 다음부터는 2, 4, 5, 6 만 해주면 됨!
> ```