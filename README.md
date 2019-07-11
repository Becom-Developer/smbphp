# NAME

smbphp - 駅の伝言板 Station message board php バージョン

# SYNOPSIS

php を活用した web アプリの制作の学習用として伝言板のアプリを作成する

## URL



## SETUP

Docker のインストール

Docker
docker のインストールには Docker Hub のアカウント登録が必要

インストールの案内に従いインストールを実行し、そのあと Docker アプリを立ち上げる

```
(docker コマンドが使えることを確認)
$ docker --version
Docker version 18.09.2, build 6247962

(クイックスタートの案内に従ってdockerを使ってみる)
(最後までおわると自分の Docker Hub アカウントに自分がつくったコンテナがアップされている)
(docker コマンドをためす)
$ docker container run hello-world
Unable to find image 'hello-world:latest' locally
latest: Pulling from library/hello-world
...

Hello from Docker!
...

For more examples and ideas, visit:
 https://docs.docker.com/get-started/

(途中で Hello form Docker! と表示するだけ)
(現在と過去に起動させたコンテナの一覧コマンド)
$ docker container ls -a
CONTAINER ID        IMAGE               COMMAND             CREATED              STATUS                          PORTS               NAMES
410b275df5d4        hello-world         "/hello"            About a minute ago   Exited (0) About a minute ago                       musing_euclid

(停止したコンテナ削除、コンテナ名は毎回変更される)
$ docker container rm musing_euclid
musing_euclid

(削除されたことの確認)
$ docker container ls -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES

(Docker をつかったphpを試してみる)
(任意の作業ディレクトリを用意)
$ mkdir -p ~/tmp/php-book && cd ~/tmp/php-book

$ docker container run -d --name php-book -v $(pwd):/var/www/html -p 80:80 php:7.2-apache
Unable to find image 'php:7.2-apache' locally
...
Status: Downloaded newer image for php:7.2-apache
ab79ec3f19c1755018dc7cb42a4492b3cf85ccefc7882655d5f56a194993f03c

(コンテナのなかに入る)
$ docker container exec -it php-book bash

(なかに入った)
root@ab79ec3f19c1:/var/www/html# echo '<?php phpinfo();' > index.php

(web ブラウザで下記にアクセスするとphpinfoが表示される)
http://localhost/

(いちどぬける)
root@ab79ec3f19c1:/var/www/html# exit

(デーモン化されてつねに動いたままになっている)
$ docker container ls -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
ab79ec3f19c1        php:7.2-apache      "docker-php-entrypoi…"   9 minutes ago       Up 9 minutes        0.0.0.0:80->80/tcp   php-book

(~/tmp/php-book の中のファイルは Dockerコンテナの中の /var/www/html の中に存在するような状態になっている)

(もう一度コンテナのなかに入ってみる)
$ docker container exec -it php-book bash

(vim が使えるか確認するが vim は使えない)
root@064aa59d626a:/var/www/html# which vim
root@064aa59d626a:/var/www/html# exit

(Docker file を作成して vim を使えるようにする)
$ cat ~/tmp/php-book/Dockerfile
FROM php:7.2-apache

RUN apt-get update

RUN apt-get install -y vim

(ビルド)
$ docker image build -t php-book:ver1 .
Sending build context to Docker daemon  3.072kB
Step 1/3 : FROM php:7.2-apache
...

 (コンテナ起動)
$ docker container run -d --name php-book-vim php-book:ver1
30ba2d1db066be40f74eebb93c9d59e64bf1f36318b026f75de7ac4003496b63

(コンテナの中に入る)
yk-iMac2017:php-book yk$ docker container exec -it php-book-vim bash

(vim コマンド確認)
root@30ba2d1db066:/var/www/html# which vim
/usr/bin/vim

(vim のバージョン)
root@30ba2d1db066:/var/www/html# vim --version
VIM - Vi IMproved 8.0 (2016 Sep 12, compiled Jun 21 2019 04:10:35)
...
root@30ba2d1db066:/var/www/html# exit

(このような状態になる)
$ docker container ls -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                NAMES
30ba2d1db066        php-book:ver1       "docker-php-entrypoi…"   3 minutes ago       Up 3 minutes        80/tcp               php-book-vim
064aa59d626a        php:7.2-apache      "docker-php-entrypoi…"   29 minutes ago      Up 29 minutes       0.0.0.0:80->80/tcp   php-book

(くわしい Docker の使い方は公式ページを参考にする)
```

### LOCAL



## START APP



### LOCAL



### DEVELOPMENT



## TEST




## WORK


## BACKUP



# TODO



# SEE ALSO

- <https://www.php.net/> - PHP 公式ページ
- <https://laravel.com/> - web フレームワーク Laravel 公式
- <https://www.docker.com/> - docker 公式
- <https://github.com/php-book/php-qa-plaza> - はじめての PHP プロフェッショナル開発
