---
title: "Shell 教程基础教程"
date: 2017-06-17T16:35:08+08:00
lastmod: 2020-04-26T16:35:08+08:00
draft: false
keywords: []
description: ""
tags: ["shell"]
categories: ["Linux"]
author: "MZZZ"
---
<!--more-->

## 变量
变量数组
>var_name=(varlue0 value1 varlue2 varlue3)
*name[n]=varlue*

只读变量
>readonly=varlue

删除变量
>unset var_nam

### 特殊变量

变量|含义
---|---
$0|当前脚本的文件名
$n|传递给脚本或函数的参数。n是一个数字，表示第几个参数。例如，第一个参数是$1，第二个参数是$2。
$#|传递给脚本或函数的参数个数。
$@|传递给脚本或函数的所有参数。
$*|传递给脚本或函数的所有参数。被双引号("")包含时，与$@稍有不同。
$?|上个命令的退出状态，或函数的返回值。
$$|当前Shell进程ID。对于 Shell 脚本，就是这些脚本所在的进程ID。

***
## 运算符
### 算数运算符

运算符|说明|举例
---|---|---
+|加法|`expr $a + $b` 结果为 30。
-|减法|`expr $a - $b` 结果为 -10。
*|乘法|`expr $a \* $b` 结果为  200。
/|除法|`expr $b / $a` 结果为 2。
%|取余|`expr $b % $a` 结果为 0。
=|赋值|a=$b 将把变量 b 的值赋给 a。
==|相等|用于比较两个数字，相同则返回 true。	[ $a == $b ] 返回 false。
!=|不相等|用于比较两个数字，不相同则返回 true。	[ $a != $b ] 返回 true。

### 关系运算符

运算符|说明|举例
---|---|---
-eq|检测两个数是否相等，相等返回 true。|[ $a -eq $b ] 返回 false。
-ne|检测两个数是否相等，不相等返回 true。|[ $a -ne $b ] 返回 true。
-gt|检测左边的数是否大于右边的，如果是，则返回 true。|[ $a -gt $b ] 返回 false。
-lt|检测左边的数是否小于右边的，如果是，则返回 true。|[ $a -lt $b ] 返回 true。
-ge|检测左边的数是否大于等于右边的，如果是，则返回 true。|[ $a -ge $b ] 返回 false。
-le|检测左边的数是否小于等于右边的，如果是，则返回 true。|[ $a -le $b ] 返回 true。

### 逻辑运算符

运算符|说明|举例
---|---|---
&&|逻辑的 AND|[[ $a -lt 100 && $b -gt 100 ]] 返回 false
ll|逻辑的 OR|[[ $a -lt 100 ll $b -gt 100 ]] 返回 true

***
## 环境配置
***
## 流程控制
### if分支
```
if [条件判断] ;then
	条件执行
if
```
### case分支
```
case $变量 in
"变量1")
	command1
	;;
"变量2")
	command2
	;;
*）
	exit 1
	；；
esac
```
### for循环
常用语法
```
for $变量 in var
do
  command
done
```
c语言语法
```
num=n
for ((a=1;a <= num; a+1 ))
do
  comand
done
```
### while循环
```
while [条件判断]
do
	command
done
```
c语言语法
```
((a=1))
num=n
while ((a <= num))
do
	command
done
```
### until循环
```
until [条件判断]
do
	command
done
```
### select结构
```
PS3=' 设置提示符字串 '
select $变量 in var
do
	command 
break
 done
```
## 函数
```
function funname ()
{
	command
}
```