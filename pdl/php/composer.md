Composer
========

* [官方原文手冊](https://getcomposer.org/doc/)
* [中文手冊 by Lance](http://getcomposer.ycnets.com/doc/)
* [簡中](http://docs.phpcomposer.com/)
* [COMPOSER設計原理與基本用法](http://blog.turn.tw/?p=1039)
* [Begining Composer](https://speakerdeck.com/jaceju/begining-composer)

Composer 可以輕易地解決 PHP 套件下載、安裝、更新、管理等問題。

Composer 之於 PHP 感覺就很像 gem 之於 Ruby ， npm 之於 Node

Installation
------------

```bash
sudo apt-get install curl # 安裝 curl
curl -sS https://getcomposer.org/installer | php # 產生 composer.phar，然後可以直接執行操作
sudo mv composer.phar /usr/local/bin/composer # 用全域的方式執行就再下這個指令
```

[Mac OSX 出錯的解決方法](https://github.com/composer/composer/issues/2839)

套件安裝方式
------------

查套件的地方：

https://packagist.org/explore/

基本指令
--------

help

```bash
php composer.phar help install
```

initial:

```bash
php composer.phar init
php composer.phar install
```

update:

```bash
php composer.phar update
php composer.phar update vendor/package vendor/package2
php composer.phar update vendor/*
```

require:

```bash
php composer.phar require
php composer.phar require vendor/package:2.* vendor/package2:dev-master
```

search:

```bash
php composer.phar search monolog
```

show:

```bash
php composer.phar show
php composer.phar show monolog/monolog
php composer.phar show monolog/monolog 1.0.2
```

depends:

```bash
php composer.phar depends --link-type=require monolog/monolog
```

validate:

```bash
php composer.phar validate # It will check if your composer.json is valid
```

status:

```bash
php composer.phar status # php composer.phar status -v
```

self-update:

```bash
php composer.phar self-update
```

Config:

```bash
php composer.phar config --list
```

Modifying Repositories:

```bash
php composer.phar config repositories.foo vcs http://github.com/foo/bar
```

create-project:

```bash
php composer.phar create-project doctrine/orm path 2.2.0
```

Create Package
--------------

可以參考 [Packagist 首頁說明](https://packagist.org/) ，和 [Composer 語法說明](https://getcomposer.org/doc/04-schema.md)

建立自己的 package ，首先要在專案根目錄建立一個 `composer.json` 檔案：

```javascript
{
    "name": "your-vendor-name/package-name",
    "type": "library",
    "description": "A short description of what your package does",
    "keywords": ["log","logging"],
    "homepage": "http://example.com",
    "authors": [
        {
            "name": "Jordi Boggiano",
            "email": "j.boggiano@seld.be",
            "homepage": "http://seld.be",
            "role": "Developer"
        }
    ],
    "require": {
        "php": ">=5.3.0",
        "another-vendor/package": "1.*"
    }
}
```

Private Composer
----------------

http://getcomposer.ycnets.com/doc/05-repositories.md#hosting-your-own

* 使用 [Packagist](https://github.com/composer/packagist)
* 使用 [Satis](https://github.com/composer/satis) 上傳的 repository 記得要標版號，不然就算使用 * 也是找不到的。不過可以用 `dev-master` 來得到最新的 master 。

Composer Package Repository
---------------------------

* [Satis](http://getcomposer.ycnets.com/doc/articles/handling-private-packages-with-satis.md)
* https://github.com/smstw/Development-Tools/issues/1