---
title: "搭建 SS 服务器"
date: 2018-02-16T16:40:34+08:00
lastmod: 2020-04-26T16:40:34+08:00
draft: false
keywords: []
description: ""
tags: []
categories: ["教程"]
author: "MZZZ"
---
<!--more-->

# 搭建ss服务器
## 选择VPS
### Vultr
*本人目前正在使用*
> [Vultr](https://www.vultr.com/?ref=7333360)全球最大的游戏主机提供商之一，使用它的原因主要是它是按小时计费的,价格也便宜。目前2.5美元每月的已经售完，5美元的每个月也有1T流量。

<a href="https://www.vultr.com/?ref=7333360"><img src="https://www.vultr.com/media/banner_2.png" width="468" height="60"></a>

### BandwagonHos
> [BandwagonHost](http://bwg.yiqimaila.com/bwg/buy.html)俗称*搬瓦工*,性价比很高。这种服务就是只拿来给新手学习Linux，我觉得也是很划得来。

### 阿里云
> 阿里云的产品在国内可以说是最好的云主机厂商之一。优点是相比外国的服务肯定要稳定些，但有一点不好就是建的网站无论大小都需要备案。

## 选择服务器节点
> 这里需要申明在国外购买的服务分配给的IP有一定可能会被墙掉，特别是我在Vultr上建的几个东京的站点无一能远程上（可能是人品问题）。

> 网络这方面大家可以自己ping通下，一般延时在200ms左右就能流畅使用。

## 选择操作系统
> 这里没什么好说的，建议选择Centos或Debian。这两个操作系统对今后的学习linux是很有好处的。

## 搭建Shadowsocks
**这处便是本文关键**
### 连接服务器
Windows用户建议下载[Xshell](https://www.netsarang.com/download/main.html)
、MAC下可直接ssh连接。
### 下载Shadowsocks

```bash
#安装python2.7及以上版本，
yum install m2crypto python-setuptools
easy_install pip
pip install shadowsocks
```
配置
```js
/etc/shadowsocks.json   
    
{
  "server": "192.0.0.1",
  "server_port":8388,
  "local_address": "127.0.0.1",
  "local_port":1080,
  "password": "12345678",
  "timeout":300,
  "method": "aes-256-cfb"
}
#也可配置多端口(记住要检查相应端口是否开启)
```
具体配置
```bash
yum install git 
git clone https://github.com/shadowsocks/shadowsocks.git
```
### 运行服务
```bash
#检查防火墙信息
firewall-cmd --query-port=443/tcp 
firewall-cmd --zone=public --add-port=443/tcp --permanent 
firewall-cmd --reload
#开启ss服务
ssserver -c /etc/shadowsocks.json -d start
```
### 简易防护
> 搭建云主机最重要的隐患就是恶意的网络攻击和厂商的抽风，搭建自行搜索保护服务器的方法（如关闭服务器的root远程登录），然后注意的就是利用网站的服务或则其他功能进行备份。

## 加速
两种加速代码均代理在github上，可在项目中查看详细信息。
* 锐速
[https://github.com/91yun/serverspeeder](https://github.com/91yun/serverspeeder)
* BBR
[https://github.com/teddysun/across](https://github.com/teddysun/across)

## 下载相应客户端
[https://github.com/shadowsocks](https://github.com/shadowsocks)
