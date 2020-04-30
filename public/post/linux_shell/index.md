<!--more-->



> ls -d $(echo ${PATH//:/ }) > /dev/null 显示PATH中失效的目录 ​​​​

> awk -F ',' '{ x = x + $4 } END { print x }' test.csv 从CSV中计算列的总数

> diff <(wget -q -O - URL1) <(wget -q -O - URL2) 比较两个远程的网页 ​​​​

> :r! echo % 在vim中插入当前文件名

> cat file | tee >> file 把文件内容贴到他自己的尾巴上(直接cat 不可以)

> for ARG in * ; do sudo -u USER 7z x -o"$(echo $ARG|sed 's/\(.*\)\..*/\1/')" 
"$ARG" ; done 解压当前目录下的所有的压缩文件，各个压缩文件都解压在自己的目录中

> ssh user@remote-host "DISPLAY=:0.0 import -window root -format png -"|display 
-format png - 远程截屏 

> date --date=yesterday +%Y%m%d 格式化另一个日期 ​​​​

> history > ~/history-save-$(date +%d-%m-%y-%T) 备份命令历史

> for i in "*.txt"; do tar -c -v -z -f $i.tar.gz "$i" && rm -v "$i"; done 压缩所有的txt

>cat file.txt | sendmail -F myname -f admin@mysite.com guest@guest.com 命令行发邮件 

> rm $( ls | egrep -v 'abc|\s' ) 删除除了叫abc的文件 ​​​​

> find /path/ -type f -exec grep -l '<string of text>' {} \; | xargs sed -i -e 's%<string of text>%<new text string>%g' 查找并替换 ​​​​

> sleep 3s && espeak "wake up, you bastard" 2>/dev/null 计时器的实现

> tar tfz filename.tgz |xargs rm -Rf 撤销解压tar的方法 ​​​​

> awk 'BEGIN{IGNORECASE=1;FS="<title>|</title>";RS=EOF} {print $2}' file.html 获取html文件中title名字 ​​​​

> truncate -s 1M file 创建特定大小的文件 ​​​​

> ls -I "*.gz" 反向ls (ls 除了 *.gz) ​​​​

> setenforce 0 关闭 SE Linux ​​​​

> cat video.avi.001 video.avi.002 video.avi.003 >> video.avi 合并小电影 ​​​​

> find -printf '%u %g\n' | sort | uniq 获取当前目录的文件权限列表 ​​​​

> cat .ssh/id_dsa.pub | ssh elsewhere "[ -d .ssh ] || mkdir .ssh ; cat >> .ssh/authorized_keys" 妈妈再也不用担心我忘了ssh密码 ​​​​

> git svn --authors-file=some-authors-file clone svn://address/of/svn/repo new-git-dir 导入/克隆一个svn仓库到git仓库 ​​​​

> find ~/Desktop/ \( -regex '.*/\..*' \) -print -exec rm -Rf {} \; 查找删除隐藏文件 ​​​​

> cat ~/.viminfo  | sed -n '/^:[0-9]\+,\([0-9]\+\|\$\)s/p' 看看今天vim中使用了多少regex ​​​​

> echo -n "string" | md5sum - 生成md5 ​​​​

> free -m | awk '/Swap/ {print $4}' 释放swap

> cp -p `ls -l | awk '/Apr 14/ {print $NF}'` /usr/users/backup_dir 查找特定时间戳的文件 ​​​​ 

> convert *.jpg File_Output.pdf 合并jpg为pdf 

> zmv '(*.*)(.*)' '${1//./_}$2' 将文件名中的 . 替换成 _ 

> ls -1 /lib/modules 列出安装的 kernels ​​​​

> find . -type f -name filename.exe -exec sed -i "s/oldstring/oldstring/g" {} +; 在任何跟'filename.exe'同名的文件中查找并替换目标字符串。

> rm !(*.foo|*.bar|*.baz) Delete all files in a folder that don't match a 
certain file extension
删除一个目录下所有不匹配特定扩展名的文件 ​​​​

> ssh user@remote "tar cfp - /path/to/log/* | gzip" > local.tar.gz 远程压缩后写到本地 ​​​​

> find . -mmin -60 -not -path "*svn*" -print|more 忽略SVN文件和文件夹，递归查找最近一小时内修改过的文件 ​​​​

> apt-cache show pkgname | grep -i "version:" 查看包版本 ​​​​

> du -s * | sort -nr | head 寻找大文件 ​​​​

> lsof | grep pcm 列出正在播放声音的进程 ​​​​

> grep 'model\|MHz' /proc/cpuinfo  |tail -n 2 查看cpu型号 ​​​​

> export var1=`ps -A | grep '[u]nique' | cut -d '?' -f 1`; echo${var1/ /}; kill -9 $var1 在无法使用pidof和pgrep的情况下，杀死PID未知的进程

> nocomments () { cat $1 | egrep -v '^[[:space:]]*#|^[[:space:]]*$|^[[:space:]]*;' | sed '/<!--.*-->/d' | sed '/<!--/,/-->/d'; } 去掉注释 ​​​​

> while true ; do  sleep 1 ; clear ;  (netstat -tn | grep -P ':36089\s+\d') ;  done 监控端口连接 ​​​​

> find . -maxdepth 1 -empty -delete 清理大小为0的文件 ​​​​

> while [ /bin/true ]; do OLD=$NEW; NEW=`cat /proc/net/dev | grep eth0 | tr -s ' ' | cut -d' ' -f "3 11"`; echo $NEW $OLD | awk '{printf("\rin 监控 RT/TX ​​​​

> for i in *.xml; do sed -i 's/foo/bar/g' "$i"; done 批量替换xml中关键字

> sed -n '/^.\{255\}/!p' 清除多余255个字符的行 

> rar a -m0 "${PWD##*/}.rar" * 自动命名创建rar的包 ​​​​

> read -sn 1 -p "Press any key to continue..." Shell版 Press Any Key to Continue

> for count in $(seq 2 1001); do say "$count sheeps";sleep 2;done 催眠 

> lftp -u<<credentials>> <<server>> -e "du -a;exit" > server-listing.txt 获取ftp的目录结构 ​​​​

> for i in $(find . -mtime +30); do mv $i old/; done 移动30天前的文件到old文件夹

> ( ( sleep 2h; your-command your-args ) & ) 在后台2个小时后运行一个命令 

> grep ^[^#] /etc/file.conf 清理文件中的注释 

> cat /dev/urandom | tr -dc A-Za-z0-9 | head -c 32 长密码

> while $t; do for i in `seq 1 30`;do r="$[($RANDOM % 2)]";h="$[($RANDOM % 4)]";if [ $h -eq 1 ]; then v="\e[1m $r";else v="\e[2m $r";fi;v2="$v2 $v";done;echo -e $v2;v2="";done; 黑客帝国 ​​​​

> echo $(( $RANDOM % 10 + 1 )) 生成 1 到 10 的随机数 ​​​​
​​​​
> function gbl() { git for-each-ref --sort=-committerdate --format='%(committerdate) %(authorname) %(refname)' refs/remotes/origin/|grep -e ".$@"|head -n 10; } 按作者列出git远程分支

> ruby -e "i=0;loop{puts ' '*(29*(Math.sin(i)/2+1))+'|'*(29*(Math.cos(i)/2+1)); i+=0.1}" 显示一个波形图案 ​​​​

> awk -F":" '{ print $1 }' /etc/passwd | while read UU ; do STATUS=$(passwd -S ${UU} | grep locked 2>/dev/null) ; if [[ ! -z ${STATUS} ]] ; then echo "Account ${UU} is locked." ; fi ; done 查找某些特定帐户是否被锁住 ​​​​

> man -t ls > ls.ps && pdf2ps ls.ps && rm ls.ps 将man文档输出为pdf格式 ​​​​

> ls * | sed -e 'p;s/foo/bar/' | xargs -n2 mv 用sed批量重命名文件 ​​​​

> echo $(shuf -i 1-35 | head -n7 | sort -n) 帮你卖双色球(35选7) ​​​​

> find . -type d | sed -e "s/[^-][^\/]*\//  |/g" -e "s/|\([^ ]\)/|-\1/" 目录树 ​​​​
​​​​
> echo -e "\e[3$(( $RANDOM * 6 / 32767 + 1 ))mHello World!" 随机颜色的字

> nc -zw2 www.example.com 80 && echo open 查看tcp端口是不是打开了 ​​​​

> myrm(){ D=/tmp/$(date +%Y%m%d%H%M%S); mkdir -p $D; mv "$@" $D && echo "moved to $D ok"; }  建立删除回收机制

> UNIX2dos [-kn] oldfile newfile  转换为Linux格式

> perl -e "use POSIX qw(strftime); print strftime '%Y%m%d' , localtime( time()-3600*24*30) "  perl获取时间