# docker-hands-on

## nginxを使ってみよう
ここでは、NginxというWebサーバのDockerイメージを取得し、
ローカルで起動してみます。

### 1. nginxのイメージを取得
次のコマンドを実行
```sh
docker pull nginx
```
実行結果
```aidl
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

### 2. nginxの起動
```
docker run -it nginx
```

### 3. ブラウザで動作確認
[http://localhost/](http://localhost/) にアクセスしてみる。


### 4. [コンテナの一覧表示](https://docs.docker.jp/engine/reference/commandline/ps.html)

次のコマンドを実行
```
docker ps
```
実行結果
```aidl
$ docker ps
CONTAINER ID   IMAGE     COMMAND                  CREATED         STATUS         PORTS     NAMES
b909af02bdeb   nginx     "/docker-entrypoint.…"   7 minutes ago   Up 7 minutes   80/tcp    epic_khayyam
```
### 5. [実行中のコンテナに入る](https://docs.docker.jp/engine/reference/commandline/exec.html#docker-exec)
次のコマンドを実行
```bash
CONTAINER_ID=docker psで表示したCONTAINER ID, ex: b909af02bdeb
docker exec -it ${CONTAINER_ID} /bin/bash
```
コンテナ環境から抜ける
```bash
exit
```
### 6. nginxの停止
nginxを動作させているコンソールで`Ctrl + c`


