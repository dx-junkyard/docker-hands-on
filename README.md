# docker-hands-on

## Dockerの起動オプション
ここではDockerでよく使う起動オプションをためしてみます。
Lesson1でnginxのイメージ取得が済んでいる前提です。


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

### ローカルディレクトリをマウントする
```
docker run -it --rm -p 8081:80 -v "$PWD/docker_work:/usr/share/nginx/html/" nginx
```

### ブラウザで表示してみる
ブラウザで [http://localhost:8081](http://localhost:8081) にアクセス。

### 起動したサーバに入る
```
CONTAINER_ID=`docker ps | grep -v "CONTAINER" | cut -f1 -d" "`
docker exec -it ${CONTAINER_ID} /bin/bash
```
nginxの設定を確認
```sh
cat /etc/nginx/conf.d/default.conf
```
表示されているメッセージを変更する
```sh
cat /usr/share/nginx/html/index.html
sed -ie 's/Welcom/Good by/' /usr/share/nginx/html/index.html
cat /usr/share/nginx/html/index.html
```

