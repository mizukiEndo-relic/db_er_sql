## Usage

### ローカルに 8 系の SQL がない場合、以下のコンテナを実行すると使えると思います。ローカルに 8 系がある人は以下のセットアップは不要

コンテナのビルドと実行

```
docker compose build
docker compose up -d
```

コンテナの mysql コマンドがうまく実行されない場合

```
mysql.server stop # 他のmysqlがローカルで干渉する場合
brew services stop mysql@5.7 # Homebrewで立ち上げている場合はこちら
```

### ファイルの実行

```
mysql -h 127.0.0.1 < <sqlfile>
```

# 使い方

```
git clone git@github.com:itsuki-n22/sql_puzzle.git
cd sql_puzzle
# コンテナを立ち上げ
docker-compose up -d
# コンテナに入る
docker-compose exec mysql sh
# MySQLログイン
mysql

# 外からログインする場合(mysqlクライアント有り) mysql -h 127.0.0.1
```

# 基本操作

```
# db 一覧表示
show databases;

# db を作成する
create database sample;
show databases;

# db の選択
use sample;

# テーブル一覧
show tables;

# テーブルの作成
create table users (id int, name varchar(10), age int);
desc users;

# ユーザの挿入
INSERT INTO users Values (1, "taro", 24);
INSERT INTO users Values (2, "jiro", 33);
INSERT INTO users Values (3, "kazu", 40);

# ユーザの取得
SELECT * FROM users;

# ユーザの削除
DELETE FROM users WHERE id = 1;

# ユーザの更新
UPDATE users SET name = "kayo" WHERE id = 2;

# 確認
SELECT * FROM users;
SELECT * FROM users WHERE id = 2;

# テーブルの作成
drop
desc users;

# 終了
exit
exit
docker-compose down
```
