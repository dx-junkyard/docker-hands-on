# docker-hands-on

## Dockerの起動オプション
ここではDockerでよく使う起動オプションをためしてみます。
Lesson1でnginxのイメージ取得が済んでいる前提です。


### コンテナ削除指定
停止後にコンテナを自動で削除する場合は`--rm`を付ける
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
mkdir ./docker_work
echo "hello!" > ./docker_work/index.html
docker run -it --rm -p 8081:80 -v "$PWD/docker_work:/usr/share/nginx/html/" nginx
```

### ブラウザで表示してみる
ブラウザで [http://localhost:8081](http://localhost:8081) にアクセス。
