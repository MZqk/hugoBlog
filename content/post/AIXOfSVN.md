---
title: "AIX 安装 SVN"
date: 2017-06-28T15:40:11+08:00
lastmod: 2020-04-26T15:40:11+08:00
draft: false
description: "AIX小型机基本都是部属在内部网络，安装软件尤其麻烦"
tags: ["软件安装"]
categories: ["教程"]
author: "MZZZ"
---
<!--more-->

yum源包地址
packages.lst
```
http://www.oss4aix.org/download/RPMS/subversion/subversion-1.7.3-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/subversion/subversion-devel-1.7.3-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/subversion/mod_dav_svn-1.7.3-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr/apr-1.4.6-1.aix5.2.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr/apr-devel-1.4.6-1.aix5.2.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr-util/apr-util-1.4.1-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr-util/apr-util-db4-1.4.1-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr-util/apr-util-devel-1.4.1-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr-util/apr-util-freetds-1.4.1-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr-util/apr-util-gdbm-1.4.1-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr-util/apr-util-ldap-1.4.1-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr-util/apr-util-odbc-1.4.1-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/apr-util/apr-util-sqlite-1.4.1-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/expat/expat-2.0.1-3.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/expat/expat-devel-2.0.1-3.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/file/file-libs-5.05-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/gettext/gettext-0.17-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/gettext/gettext-devel-0.17-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/neon/neon-0.29.5-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/neon/neon-devel-0.29.5-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/sqlite/sqlite-3.7.9-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/zlib/zlib-1.2.6-1.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/pkg-config/pkg-config-0.25-2.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/readline/readline-6.2-3.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/db4/db4-4.7.25-2.aix5.1.ppc.rpm
http://www.oss4aix.org/download/RPMS/openssl/openssl-0.9.8u-1.aix5.1.ppc.rpm
```
下载二进制包脚本
auto_wget.sh
```
#!/bin/sh

echo "auto download some rpm packages from Internet begin..."
if [ ! -f packages.lst ]; then
        echo "Error: file packages.lst not exist."
        exit -1
fi

for FILENAME in `cat packages.lst`
do
  echo "download $FILENAME begin..."
  wget $FILENAME
  echo "download $FILENAME end..."
done
echo "done"
exit 0
```
自动安装软件包脚本
auto_install.sh
```
#!/bin/sh

echo "auto install some rpm packages from Internet begin..."
if [ ! -f packages.lst ]; then
        echo "Error: file packages.lst not exist."
        exit -1
fi

for FILENAME in `awk -F"/" '{print $NF}' packages.lst'`
do
  echo "Installing $FILENAME begin..."
  rpm -ivh $FILENAME --nodeps
  echo "Installing $FILENAME end..."
done
echo "done"
exit 0
```

[官网介绍所需依赖环境](http://www.perzl.org/aix/index.php?n=Main.Subversion)


配置文件 