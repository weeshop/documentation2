---
title: 安装
---

> 本文介绍非开发者用户如何安装 WeeShop，如果你是开发者请 [使用 Composer 进行工程创建](../dev_guide/project.html)

## 下载

请前往 [WeeShop Github 版本发布页面](https://github.com/weeshop/WeeShop/releases) 
下载最新版本的发行包。

## 使用 Docker 镜像安装

WeeShop 自带 Docker 镜像，如果会使用 Docker，安装将会非常方便。

在源码的根目录有一个 `docker-compose.yml` 文件，文件中已编排了一个 web 容器和一个 db 容器， 
如果主机已经安装了 docker，那么可以直接在源码根目录运行以下命令即可：
```bash
docker-compose up -d
```

运行命令后，通过访问 `http://localhost:8080` 即可打开 WeeShop 的图形安装界面，按提示输入必要信息安装即可。
需要注意的是，数据库的设置：

- 主机: db
- 端口：3306
- 用户：root
- 密码：123
- 数据库：weeshop

## 自定义服务器环境安装

由于 Docker 的便利性，强列建议使用 Docker 方式进行安装。

如果要自行架设置 Apache 和 MySQL 环境，请根据以下的要求来配置。

#### 运行环境要求

- 操作系统：任何支持 PHP 的操作系统，如 Windows/Linux/MacOS
- HTTP服务器：暂时只支持 Apache，请使用 2.4以上版本，并且需要开启 rewrite。
- PHP版本：请使用 7.1 以上版本。
- MySQL版本：请使用 Mysql 5.7或以上的版本。

#### 需要PHP扩展列表

取决于你的操作系统和软件版本和PHP的安装方式的不同，php包含的扩展模块可能不一样，
但是你可以检查一下以下的列表，如果已安装了这些扩展，那么基本上不会有问题，因为这是从开发人员的环境列出的清单：

```bash
bash-4.4# php -m
[PHP Modules]
apcu
bcmath
bz2
calendar
Core
ctype
curl
date
dom
exif
fileinfo
filter
ftp
gd
gettext
hash
iconv
imagick
intl
json
ldap
libxml
mbstring
mcrypt
mysqli
mysqlnd
openssl
pcntl
pcre
PDO
pdo_mysql
pdo_sqlite
Phar
posix
readline
redis
Reflection
session
shmop
SimpleXML
soap
sockets
SPL
sqlite3
standard
sysvmsg
sysvsem
sysvshm
tokenizer
wddx
xml
xmlreader
xmlrpc
xmlwriter
xsl
Zend OPcache
zip
zlib

[Zend Modules]
Zend OPcache
```


## 执行安装

- 解压源码包，把 web 目录设置为 apache 站点根目录。
- 确保 apache 进程对 `web/sites/default` 目录拥有可写权限，其他目录权需可读权限即可。
- 在浏览器中访问 apache 站点，即可打开WeeShop的图形化安装界面。
- 按照图形界面的要求填写数据库连接信息，和站点信息、管理员账号信息，即可完成安装。