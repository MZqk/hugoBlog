<!--more-->


1.修改root密码
重启进入grub按e编辑
添加rd.break console=stty0
或者修改rw init=/sysroot/bin
进入修复模式
挂载根系统
mount -o remount.rw /sysroot
切换根目录
chroot /sysroot
修改root密码passwd
重建SELinux安全策略
touch /.autorelabel
退出重启
2.修改本机网络信息
修改主机名
/etc/sysconfig/network
HOSTNAME信息
/etc/sysconfig/network
localhost信息
或
hostnamectl  set-hostname  example.hostname
修改静态网卡信息
/etc/sysconfig/network-scripts/ifcfg-eth0
BOOTPROTO=static
DNS1=
IPADDR=
NETMASK=
GETWAY=
或
nm-connection-editor图形化界面
nmcli  connection  up  "System eth0" 
3.搭建默认软件仓库
yum-config-manager --add  http://example.com 
修改 /etc/yum.repos.d/example.repo 
关闭KEY检查gpgcheck=0
yum clean all
yum repolist
4.创建账户
创建用户组
groupadd adminuser
创建用户
useradd -G admin1  adminuser
创建用户不赋予shell交互
useradd -s /sbin/nologin admin2
设置用户密码
passwd admin1
5.配置文件权限
6.创建定时任务
开启cron服务

给admin1用户编辑一个任务
crontab -e -u admin1
7.创建共享目录
创建目录
mkdir /home/admin
给予用户组adminuser目录所有权
chown  :adminuser  /home/admin
赋予组内用户可读、可写和可执行权限，其他用户无权限
chmod 770 /home/admin
8.安装升级内核
下载内核
wget http://kernel.com/download/kernel.rpm
安装rpm包
rpm -ivh kernel.rpm
重启后确认内核版本
uname -r