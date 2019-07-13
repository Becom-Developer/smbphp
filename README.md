# NAME

smbphp - 駅の伝言板 Station message board php バージョン

# SYNOPSIS

php を活用した web アプリの制作の学習用として伝言板のアプリを作成する

## URL

## SETUP

- Docker を活用した環境設定は [SEE ALSO](#see-also) の `docker_dev` を参考(途中)

- ローカル環境に直接構築する

Mac

homebrew を使って php を準備

```
(システムの php が使われてる)
$ which php
/usr/bin/php
(2019/07/13現在での Mac はわりとあたらしめのPHPが入っている)
$ php --version
PHP 7.1.23 (cli) (built: Feb 22 2019 22:19:32) ( NTS )
...
(brew を更新しておく)
$ brew update
Updated 1 tap (homebrew/core).
...
(問題点を診断しておく)
$ brew doctor
...
(警告がでるようなら改善)

(php で検索してみる)
yk-iMac2017:smbphp yk$ brew search php
==> Formulae
...
php@7.2 ...
(7.2をインストール)
$ brew install php@7.2

(brew インストール後にパスを通すメッセージができているので、メッセージ通り対応後ターミナル再起動)

(brew の php を使えるようになった)
$ which php
/usr/local/opt/php@7.2/bin/php
$ php --version
PHP 7.2.20 (cli) (built: Jul  5 2019 12:51:26) ( NTS )
Copyright (c) 1997-2018 The PHP Group
Zend Engine v3.2.0, Copyright (c) 1998-2018 Zend Technologies
    with Zend OPcache v7.2.20, Copyright (c) 1999-2018, by Zend Technologies
```

PHP パッケージ管理 Composer を準備

```
$ curl -sS https://getcomposer.org/installer | php
All settings correct for using Composer
Downloading...

Composer (version 1.8.6) successfully installed to: /Users/yk/composer.phar
Use it: php composer.phar

(ヘルプが出る)
$ php composer.phar
...
Composer version 1.8.6 2019-06-11 15:03:05
...

(composer.phar は実行したディレクトリに存在することに注意)
```

web フレームワーク laravel を用意

```
(作業ディレクトリに移動)
$ cd ~/github/smbphp
(laraver インストール laraver 公式ページ参考)
$ php ~/composer.phar global require laravel/installer
Changed current directory to /Users/yk/.composer
...
Generating autoload files
...

(パスを通す、そのあと一度ターミナルを再起動)
$ echo 'export PATH="$HOME/.composer/vendor/bin:$PATH"' >> ~/.bash_profile

(プロジェクトを作成)
$ laravel new smbphp
Crafting application...
...

(ディレクトリ階層を一つ上げておく、隠しファイルも含めて)
$ mv smbphp/.[^\.]* .
$ rmdir smbphp

(vendor のファイルをインストール)
$ php ~/composer.phar install

(開発サーバー起動)
$ php artisan serve
Laravel development server started: <http://127.0.0.1:8000>
...
^C
(control + c で終了)
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
- <https://knowledge.sakura.ad.jp/13265/> - Docker入門
- <https://www.php-fig.org/> - PHP FIG 公式
- <https://packagist.org/> - Packagist (Composer のメインレポジトリサービス)
- <https://getcomposer.org/> - Composer
- [docker_dev](https://github.com/Becom-Developer/textbook/blob/master/docker_dev.md) - docker_dev
