# CakePHP 環境を作る
* Dockerfileを作る(php,mysql)  
* docker-compose.ymlを作る  
> docker-compose up -d
> docker exec -it php-book-app-web bash

* install cakephp
> composer create-project --prefer-dist --no-interaction cakephp/app:3.6.* ./app

* http://localhost:5000  にアクセス

* 起動時にcomposer installを実行するための設定を追加
shellを作ってdocker起動時に実行するようにする  
docker-compose.ymlにcommandを追加  