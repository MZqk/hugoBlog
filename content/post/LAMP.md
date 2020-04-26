---
title: "安装 LAMP"
date: 2017-06-13T14:21:39+08:00
lastmod: 2020-04-26T14:21:39+08:00
draft: false
description: ""
tags: []
categories: ["教程"]
author: ""

# You can also close(false) or open(true) something for this content.
# P.S. comment can only be closed
comment: true
toc: true
autoCollapseToc: false
postMetaInFooter: false
hiddenFromHomePage: false
# You can also define another contentCopyright. e.g. contentCopyright: "This is another copyright."
contentCopyright: false
reward: false
mathjax: false
mathjaxEnableSingleDollar: false
mathjaxEnableAutoNumber: false

# You unlisted posts you might want not want the header or footer to show
hideHeaderAndFooter: false

# You can enable or disable out-of-date content warning for individual post.
# Comment this out to use the global config.
#enableOutdatedInfoWarning: false

flowchartDiagrams:
  enable: false
  options: ""

sequenceDiagrams: 
  enable: false
  options: ""

---
## 安装LAMP服务
### Linux
### Apache
安装apache
服务器ip查看运行状态
### Mysql
安装mysql
查看php操作模块
/etc/php7/conf.d/mysql.ini
添加php操作模块
>php7.0-mysql
### PHP
安装php
查看php加载模块
```
/etc/apache2/mods-enabled/php7.load
```
>/usr/lib/apache2/modules/libphp7.so
服务器phpinfo探针
/var/www/info.php

```php
<?php
echo mysql_connect('localhost','root','123456') ? '连接成功' ： '连接失败'；

phpinfo();
```

php扩展
php7.0-gd curl libcurl3 libcurl3-dev php7.0-curl
## LAMP配置文件
### L：/etc
### A：/etc/apache2
* apache.conf
1.conf.d/*
2.httpd.conf
3.mods-enabled/*
4.sites-enabled/*
-mods* Apache模块
-sites* 虚拟主机
### M:/etc/mysql
核心配置文件my.cnf
### P:/etc/php7.0
核心配置文件php.ini

