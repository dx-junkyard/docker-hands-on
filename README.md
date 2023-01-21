# docker-hands-on

## Dockerとは？
### コンテナ単位の仮想環境を手軽に作るためのもの
昔は１台ずつ目的に応じて用意していた物理的なサーバを、コンテナという仮想環境の中でソフトウェア的に実現することで、柔軟な運用を可能にしたものです。
例えば、Webサービスをつくるため、Web UI, Web API, DBと３つのサーバを用意しようと思った場合でも、１台のサーバの中に３台の仮想サーバを構築することが可能になります。

また、構築に関する情報がスクリプトで記述されるため、同じ環境を簡単に再現することができます。

[参考 Docker-docs-ja](https://docs.docker.jp/engine/introduction/understanding-docker.html) を参照してください。

## メニュー
* [Lesson1](https://github.com/dx-junkyard/docker-hands-on/tree/Lesson1) : nginxのイメージを使ったdockerの基本的な操作
* [Lesson2](https://github.com/dx-junkyard/docker-hands-on/tree/Lesson2) : 起動時によく使うオプション
* [Lesson3](https://github.com/dx-junkyard/docker-hands-on/tree/Lesson3) : Webサーバで表示しているHTMLを変更してみる 〜コンテナに入って作業する方法〜（１）
* Lesson4: （作成中）Webサーバで表示しているHTMLを変更してみる 〜mountしたディレクトリで作業する方法〜（２）


