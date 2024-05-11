```
#### Dockerホスト側作業
docker exec -it app bash

#### アプリケーションコンテナ作業
root@3bfaed592397:/var/www# composer create-project "laravel/laravel=11.*" .

#### .envの編集

# DB_CONNECTION=sqlite
# DB_HOST=127.0.0.1
# DB_PORT=3306
# DB_DATABASE=laravel
# DB_USERNAME=root
# DB_PASSWORD=

DB_CONNECTION=mysql # DBの種類
DB_HOST=db_mysql57  # docker-composeのdbのコンテナ名
DB_PORT=3306  # docker-composeのコンテナ側(右側)のポート
DB_DATABASE=test #docker-composeデータベース名
DB_USERNAME=user #docker-composeのユーザー名
DB_PASSWORD=password #docker-composeのDBパスワード名


chmod -R 777 storage/
php artisan migrate

※migrateができなかったら、以下を試してみる。
* docker compose down
* docker compose up --build
* php artisan migrate:fresh 
```


## メモ

Laravel Framework : 11.7.0
apache: 5.7.44
php: 8.3


