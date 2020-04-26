---
title: "Linux 常用命令"
date: 2017-06-17T16:33:59+08:00
lastmod: 2020-04-26T16:33:59+08:00
draft: false
description: ""
tags: ["shell"]
categories: ["Linux"]
author: "MZZZ"
---
<!--more-->

# awk
## awk语法

|参数|说明|
|----|----|
|-F|以指定字符作为分割字段|

## awk用法

打印/etc/passwd内容
```
awk '{print}' /etc/passwd
```
>root:x:0:0:root:/root:/bin/bash    
daemon:x:1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin:x:2:2:bin:/bin:/usr/sbin/nologin
sys:x:3:3:sys:/dev:/usr/sbin/nologin
sync:x:4:65534:sync:/bin:/bin/sync
games:x:5:60:games:/usr/games:/usr/sbin/nologin
man:x:6:12:man:/var/cache/man:/usr/sbin/nologin
lp:x:7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail:x:8:8:mail:/var/mail:/usr/sbin/nologin
news:x:9:9:news:/var/spool/news:/usr/sbin/nologin
uucp:x:10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy:x:13:13:proxy:/bin:/usr/sbin/nologin
www-data:x:33:33:www-data:/var/www:/usr/sbin/nologin
backup:x:34:34:backup:/var/backups:/usr/sbin/nologin

以冒号为分隔符取1、3、6位内容
```
awk -F ":" '{print $1 $3 $6}' /etc/passwd
```
>bin2/bin   
sys3/dev    
sync4/bin
games5/usr/games    
man6/var/cache/man  
lp7/var/spool/lpd
mail8/var/mail  
news9/var/spool/news    
uucp10/var/spool/uucp   
proxy13/bin 
www-data33/var/www  
backup34/var/backups    

取出内容以Tab建作为分隔符
```
awk -F ":" '{print $1 "\t" $3 "\t" $6}' /etc/passwd
```
>root    0       /root  
daemon  1       /usr/sbin   
bin     2       /bin    
sys     3       /dev    
sync    4       /bin
games   5       /usr/games  
man     6       /var/cache/man  
lp      7       /var/spool/lpd  
mail    8       /var/mail   
news    9       /var/spool/news     
uucp    10      /var/spool/uucp     
proxy   13      /bin    
www-data        33      /var/www    
backup  34      /var/backups

内容加以排版
```
awk -F ":" '{print "ID="$1 "\t 家目录="$6}' /etc/passwd
```
>ID=root    家目录=/root  
ID=daemon        家目录=/usr/sbin   
ID=bin   家目录=/bin    
ID=sys   家目录=/dev    
ID=sync  家目录=/bin    
ID=games         家目录=/usr/games  
ID=man   家目录=/var/cache/man  
ID=lp    家目录=/var/spool/lpd  
ID=mail  家目录=/var/mail   
ID=news  家目录=/var/spool/news     
ID=uucp  家目录=/var/spool/uucp     
ID=proxy         家目录=/bin    
ID=www-data      家目录=/var/www    
ID=backup        家目录=/var/backups

# crontab
## crontab语法
>-l  列出定时任务列表      
-e  编辑定时任务内容      
-u  设定指定用户
## crontab用法
![crontab](http://note.youdao.com/yws/public/resource/2142162fc5a9548c53c40de42a6d3551/xmlnote/6750B9C6F7CA497D94D48E94183B9C28/3566)
>星号（*）：代表所有可能的值，例如month字段如果是星号，则表示在满足其它字段的制约条件后每月都执行该命令操作。

>逗号（,）：可以用逗号隔开的值指定一个列表范围，例如，“1,2,5,7,8,9”

>中杠（-）：可以用整数之间的中杠表示一个整数范围，例如“2-6”表示“2,3,4,5,6”

>正斜线（/）：可以用正斜线指定时间的间隔频率，例如“0-23/2”表示每两小时执行一次。同时正斜线可以和星号一起使用，例如*/10，如果用在minute字段，表示每十分钟执行一次。
# cat
# chattr
# date
# find
# expr

# git
## Git 配置
添加git信息
```bash
git config --global user.name "Scott Chacon"   
git config --global user.email "schacon@gmail.com"
# --global 为全局选项
```
git信息配置文件
>~/.gitconfig

## Git仓库
克隆一个项目
```bash
git clone https://github.com/MZqk/boco
```
初始化一个仓库
```bash
cd ./
git init
```
## Git流程
```bash
git add
#添加新创建或修改的文件到本地的缓存区（Index）
git rm
#删除后会自动将已删除文件的信息添加到缓存区
git commit
#命令提交到本地代码库
git status
#查看当前git仓库的状态
git diff --cached
#如果没有--cached参数，git diff 会显示当前你所有已做的但没有加入到索引里的修改
git push origin master
#将本地仓库同步到远端服务器
```
## 分支与合并
```
git branch 
#查看当前的分支列表
git branch experimental
#创建一个新的叫 experimental的分支
git checkout experimental
#切换到experimental分支
git merge  -m 'merge experimental branch' experimental
#将experimental分支合并到当前分支
git branch -d experimental
#只能删除那些已经被当前分支的合并的分支. 如果你要强制删除某个分支的话就用git branch –D
git reset --hard HEAD^
#回到合并之前的状态
```
## Git日志
```
git log
#显示所有的提交
git log v2.5.. Makefile fs/
#找出所有从"v2.5“开始在fs目录下的所有Makefile的修改
git log --stat
打印详细的提交记录
git log --pretty=oneline
格式化日志输出,可用medium,full,fuller,email 或raw
git log --graph --pretty=oneline
可视化提交图
git log --pretty=format:'%h : %s' --topo-order --graph
提交按拓扑顺序来显示
```
# grep

# sed
## sed语法

|参数|说明|
|---|---|
|-n|显示处理后的过程，自动换行|

## sed用法
文件内容
>line 1 This is a book  
line 2 That is a pen    
line 3 Happy Holiday    
line 4 Niscenter is a good place    
line 5 End


删除第2到4行内容
```
sed '2,4d' file
```
>line 1 This is a book  
line 5 End

替换每行第一个is为error
```
sed 's/is/error/' file
```
>line 1 Therror is a book   
line 2 That error a pen 
line 3 Happy Holiday    
line 4 Nerrorcenter is a good place     
line 5 End

替换全部的is为error
```
sed 's/is/error/g' file
```
>line 1 Therror error a book    
line 2 That error a pen     
line 3 Happy Holiday    
line 4 Nerrorcenter error a good place  
line 5 End  

在有center内容的一行替换is为xx
```
sed '/center/s/is/xx/g' file
```
>line 1 This is a book  
line 2 That is a pen    
line 3 Happy Holiday    
line 4 Nxxcenter xx a good place    
line 5 End

# tar
## tar语法

|参数|说明|
|---|---|
|-c  --crate |创建新的归档,即打包 |   
|-r  --append |向压缩文件追加内容  |   
|-t  --list |查看压缩全部的内容   |
|-u  --update |更新压缩文件   |
|-x  --extract |释放归档文件，即解压|  
|-v  |显示操作过程  |
|-z  |解压tar.gz、tgz文件选项 |    
|-j  |解压tar.bz2文件 |   
|-f  |制定压缩文件名  |   
|-C  |切换至指定目录  |
|--exclude file |压缩过程中排除指定文件|

## tar用法
- tar
>tar -xvf filename.tar

>tar -cvf filename.tar dirname
- tar.gz
>tar -zxvf filename.tar.gz

>tar -zxcf filename.tar.gz dirname
- tar.bz2
>tar -jxvf filename.tar.bz2

>tar -jxcf filename.tar.bz2 dirname

# test
## test语法

参数|说明
---|---
-d|如果文件为一个目录，则为真   
-e|如果文件存在，则为真     
-G|如果文件存在且归该组所有，则为真     
-O|如果文件存在并且归该用户所有，则为真  
-s|如果文件的长度不为零，则为真     
-r|如果文件可读，则为真        
-w|如果文件可写，则为真        
-x|如果文件可执行，则为真
|
-eq|数值等于,则为真
-ne|数值不等于,则为真
-gt|数值大于,则为真
-ge|数值小于等于,则为真
-lt|数值小于,则为真
-le|数值小于等于,则为真
|
=|字符相等，则为真
!=|字符不相等，则为真
-z|字符串长度为零，则为真
-n|字符串长度不为零，则为真

**Shell还提供了与( -a )、或( -o )、非( ! )三个逻辑操作符用于将测试条件连接起来，其优先级为："!"最高，"-a"次之，"-o"最低。**
## test用法
### 文件测试
```
cd /bin
if test -e ./bash 
then
    echo '文件已存在!'  
else
    echo '文件不存在!' 
fi
```
输出结果
>文件已存在!

### 数值测试
```
num1=100 
num2=100
if test $[num1] -eq $[num2]
then    
    echo '两个数相等！'   
else
    echo '两个数不相等！' 
fi
```
输出结果
>两个数相等！
### 字符串测试
```
num1="ru1noob"
num2="runoob"
if test $num1 = $num2
then
    echo '两个字符串相等!'
else
    echo '两个字符串不相等!'
fi
```
输出结果
>两个字符串不相等!

# xarge
