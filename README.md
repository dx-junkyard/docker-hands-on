# docker-hands-on

## ブラウザに表示されているメッセージを変更する
ここではnginxで表示している内容の変更を行います。


### nginxを起動
```sh
docker run -it --rm -p 8081:80 nginx
```


### ブラウザで表示してみる
ブラウザで [http://localhost:8081](http://localhost:8081) にアクセス。

### 起動したサーバに入る
```
CONTAINER_ID=`docker ps | grep -v "CONTAINER" | cut -f1 -d" "`
docker exec -it ${CONTAINER_ID} /bin/bash
```

### nginxの設定を確認
```sh
cat /etc/nginx/conf.d/default.conf
```

### 現在表示しているHTMLの内容を確認
```sh
cat /usr/share/nginx/html/index.html
```

### 表示されているメッセージを変更する
```sh
sed -ie 's/Welcom/Good by/' /usr/share/nginx/html/index.html
```

### 修正結果を確認する
```sh
cat /usr/share/nginx/html/index.html
```

