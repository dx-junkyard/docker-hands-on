# docker-hands-on

## Dockerとは？
### コンテナ単位の仮想環境を手軽に作るためのもの
昔は１台ずつ目的に応じて用意していた物理的なサーバを、コンテナという仮想環境の中でソフトウェア的に実現することで、柔軟な運用を可能にしたものです。
例えば、Webサービスをつくるため、Web UI, Web API, DBと３つのサーバを用意しようと思った場合でも、１台のサーバの中に３台の仮想サーバを構築することが可能になります。

また、構築に関する情報がスクリプトで記述されるため、同じ環境を簡単に再現することができます。

[参考 Docker-docs-ja](https://docs.docker.jp/engine/introduction/understanding-docker.html) を参照してください。

## メニュー
* Lesson1: nginxのイメージを使ったdockerの基本的な操作
* Lesson2: 起動時によく使うオプション

## Webサーバを動かしてみる
### 1. nginxのイメージを取得
```sh
docker pull nginx
```

### 2. nginxの起動
```
docker run -it nginx
```

### 3. ブラウザで動作確認
[http://localhost:8080](http://localhost:8080)にアクセスしてみる。

### 4. nginxの停止
nginxを動作させているコンソールで`Ctrl + c`



## 起動方法を変えてみる
### 自動イメージ削除
停止後にイメージを自動で削除する場合は`--rm`を付ける
```
docker run -it --rm nginx
```

### ポート転送（１）
ポート番号80で受けたリクエストを80に転送する
```
docker run -it --rm -p 80:80 nginx
```

### ポート転送（２）
ポート番号8081で受けたリクエストを80に転送する
```
docker run -it --rm -p 8081:80 nginx
```

### 起動したサーバに入り、表示されるメッセージを変更する
```
docker run -it --rm -p 8081:80 nginx bash
cat /etc/nginx/conf.d/default.conf
cat /usr/share/nginx/html/index.html
sed -ie 's/Welcom/Good by/' /usr/share/nginx/html/index.html
cat /usr/share/nginx/html/index.html
```

### ローカルディレクトリをマウントする
```
docker run -it --rm -p 8081:80 -v "$PWD/docker_work:/usr/share/nginx/html/" nginx
```
