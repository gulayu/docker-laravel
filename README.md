# docker-laravel開発環境
## 手順
### 開発環境テンプレをクローンしてくる
```sh
git clone https://github.com/gulayu/docker-laravel
cd docker-laravel
docker-compose up -d --build
```

### laravelプロジェクトをクローンしてくる
```sh
docker-compose exec app bash
git clone <laravelプロジェクトのリポジトリ> .
```

### laravelインストール時の初期構築手順を実行
```sh
composer install
cp .env.example .env
php artisan key:generate
```
.envのDBの項目を適宜変更する
```
（参考）
DB_CONNECTION=mysql
DB_HOST=db
DB_PORT=3306
DB_DATABASE=test
DB_USERNAME=root
DB_PASSWORD=secret
※docker側の、infra/mysql/Dockerfileの設定に合わせること
```
DBにデータ投入（必要に応じて）
```sh
php artisan migrate
php artisan db:seed
```

###
welcome画面の確認  
http://127.0.0.1:8080  
※portはdocker-compose.ymlを参照