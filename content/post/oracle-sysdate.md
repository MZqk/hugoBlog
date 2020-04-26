---
title: "Oracle Sysdate 时间函数"
date: 2017-06-16T16:31:53+08:00
lastmod: 2020-04-26T16:31:53+08:00
draft: false
keywords: []
description: ""
tags: ["Oracle"]
categories: ["教程"]
author: "MZZZ"
---
<!--more-->

# Oracle 时间函数

## 天粒度
SELECT TRUNC(sysdate,'DD') FROM dual;
sysdate+1 加一天

## 小时粒度
* 取10天前0点
SELECT TRUNC(sysdate-10,'DD') FROM dual;
* 取3小时前
SELECT TRUNC(sysdate-3/24,'HH') FROM dual; 
select sysdate  - 3/24 from taa_onerow
sysdate+1/24 加1小时

## 分钟粒度
sysdate+1/(24*60) 加1分钟
sysdate+1/(24*60*60) 加1秒钟
类推至毫秒0.001秒

## 函数运算
加法 
select sysdate,add_months(sysdate,12) from dual;        --加1年 
select sysdate,add_months(sysdate,1) from dual;        --加1月 
select sysdate,to_char(sysdate+7,'yyyy-mm-dd HH24:MI:SS') from dual;  --加1星期 
select sysdate,to_char(sysdate+1,'yyyy-mm-dd HH24:MI:SS') from dual;  --加1天 
select sysdate,to_char(sysdate+1/24,'yyyy-mm-dd HH24:MI:SS') from dual;  --加1小时 
select sysdate,to_char(sysdate+1/24/60,'yyyy-mm-dd HH24:MI:SS') from dual;  --加1分钟 
select sysdate,to_char(sysdate+1/24/60/60,'yyyy-mm-dd HH24:MI:SS') from dual;  --加1秒 
减法 
select sysdate,add_months(sysdate,-12) from dual;        --减1年 
select sysdate,add_months(sysdate,-1) from dual;        --减1月 
select sysdate,to_char(sysdate-7,'yyyy-mm-dd HH24:MI:SS') from dual;  --减1星期 
select sysdate,to_char(sysdate-1,'yyyy-mm-dd HH24:MI:SS') from dual;  --减1天 
select sysdate,to_char(sysdate-1/24,'yyyy-mm-dd HH24:MI:SS') from dual;  --减1小时 
select sysdate,to_char(sysdate-1/24/60,'yyyy-mm-dd HH24:MI:SS') from dual;  --减1分钟 
select sysdate,to_char(sysdate-1/24/60/60,'yyyy-mm-dd HH24:MI:SS') from dual;  --减1秒