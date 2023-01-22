# docker-hands-on

## nginxを使ってみよう
ここでは、NginxというWebサーバのDockerイメージを取得し、ローカルでWebサービスを起動してみます。

ここではサービスの起動と基本的な操作だけを学習し、HTMLなどで書いたコンテンツの表示に関してはLesson2以降で確認します。

**注意点:** コマンドを打てるターミナルウィンドウを２つ開いて置いてください。１つはDockerの起動と停止を行うため、もう一つはDockerで起動したコンテナに入ったり、状態を確認するために使います。

### 1. nginxのイメージを取得
実行するコマンド
```sh
docker pull nginx
```

実行結果
```sh
$ docker pull nginx
Using default tag: latest
latest: Pulling from library/nginx
Digest: sha256:b8f2383a95879e1ae064940d9a200f67a6c79e710ed82ac42263397367e7cc4e
Status: Image is up to date for nginx:latest
docker.io/library/nginx:latest
```

### 2. nginxの起動
実行するコマンド
```sh
docker run -it nginx
```

実行結果
```sh
$ docker run -it nginx
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2023/01/21 09:33:45 [notice] 1#1: using the "epoll" event method
2023/01/21 09:33:45 [notice] 1#1: nginx/1.23.3
2023/01/21 09:33:45 [notice] 1#1: built by gcc 10.2.1 20210110 (Debian 10.2.1-6) 
2023/01/21 09:33:45 [notice] 1#1: OS: Linux 5.15.49-linuxkit
2023/01/21 09:33:45 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2023/01/21 09:33:45 [notice] 1#1: start worker processes
2023/01/21 09:33:45 [notice] 1#1: start worker process 29
2023/01/21 09:33:45 [notice] 1#1: start worker process 30
2023/01/21 09:33:45 [notice] 1#1: start worker process 31
2023/01/21 09:33:45 [notice] 1#1: start worker process 32
```

### 3. [コンテナの一覧表示](https://docs.docker.jp/engine/reference/commandline/ps.html)

実行するコマンド
```
docker ps
```

実行結果
```sh
$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS     NAMES
b909af02bdeb   nginx     "/docker-entrypoint.…"   7 minutes ago   Up 7 minutes   80/tcp    epic_khayyam
```

停止中のコンテナを含めて表示する場合は `-a` を使います
```sh
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                     PORTS     NAMES
c49b7c6cd253   nginx     "/docker-entrypoint.…"   15 seconds ago   Exited (0) 5 seconds ago             relaxed_euclid
```


### 4. [実行中のコンテナに入る](https://docs.docker.jp/engine/reference/commandline/exec.html#docker-exec)
次のコマンドを実行
```bash
docker exec -it 確認したコンテナIDを指定 /bin/bash
```
コンテナ環境から抜ける
```bash
exit
```


### 5. nginxの停止
nginxを動作させているコンソールで`Ctrl + c`


### 6. 起動したコンテナの削除
停止したコンテナはメモリから開放されたものの、再開が可能なようにストレージを占領し続けています。
`docker rm コンテナID` を用いて使用しなくなったコンテナを削除します

```sh
# 停止したコンテナIDを確認
$ docker ps -a
CONTAINER ID   IMAGE     COMMAND                  CREATED          STATUS                     PORTS     NAMES
a24ce5fcf049   nginx     "/docker-entrypoint.…"   12 seconds ago   Exited (0) 9 seconds ago             nostalgic_chatelet

# コンテナを削除
$ docker rm a24ce5fcf049
a24ce5fcf049
```
