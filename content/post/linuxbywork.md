---
title: "使用 Linux 远程连接 Windows"
date: 2017-06-14T15:34:14+08:00
lastmod: 2020-04-26T15:34:14+08:00
draft: false
keywords: []
description: ""
tags: []
categories: ["教程"]
author: "MZZZ"
---
<!--more-->

办公环境为windows server2003与server2008

确保连接公司专线（或则挂载公司VPN）++修改IPv4的ip地址与网关掩码++

---
查看本机网卡配置
ifconfig

添加路由 
>route add -net 10.175.0.0 netmask 255.255.0.0 gw 10.175.24.254 dev eth0

修改网关
>route add -vF 10.175.0.0 netmask 255.255.0.0 gw 10.175.24.254 dev eth0

**linux使用的软件为**
- [remmina](https://www.remmina.org/wp/)
- [freerdp](https://github.com/FreeRDP/FreeRDP/wiki/PreBuilds)
