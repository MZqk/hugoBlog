<!--more-->

添加用户名
useradd -m name

创建用户指定家目录
useradd -d /home/name -m name

修改用户家目录
usermod -d /home/newname name

允许用户使用SSH登入
vim /etc/ssh/sshd_config
AllowUsers name

修改用户默认shell

1.useradd --shell /usr/bin/zsh name

2.vim /etc/passwd
name.....：/usr/bin/zsh

给予用户root权限
1.usermod -aG sudo name
2.vim /etc/sudoers
name    ALL(ALL:ALL) ALL