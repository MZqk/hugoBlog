<!--more-->


[hosts下载地址](https://github.com/MZqk/hosts)

首先科普下我们为什么不能访问Google、Twitter、Facebook 之类的网站

>这是因为我们国家有GFW（英文名称Great Firewall of China），
>也称中国防火墙或中国国家防火墙的存在。为什么要有这个东西的
>存在呢？对外的说法是保护国内的网络纯净和谐地发展道路,顺带养
>活下国内的BAT

>╮(￣⊿￣)╭**我想GFW的存在意义是保护的是外国友人不被国内傻逼打扰•̀.̫•́✧**

```
为了方便用户记忆，我们将IP变成一个个的域名来输入到浏览器进行访问。而这使得访问网站时要先将其域名解析成 IP。DNS的作用就是进行IP解析，把域名对应到IP。
在GFW的五种封锁方法中，有一种简单而效果很好的方法是DNS污染。GFW会对DNS的解析过程进行干扰，这会使对某些被干扰的域名返回一个错误的IP地址给你的主机，使你无法正确连接到你要的服务器上读取正确的信息。Hosts 文件本来是用来提高解析效率。在进行 DNS请求以前，系统会先检查自己的Hosts文件中是否有这个地址映射关系，如果有则调用这个IP地址映射，如果没有再向已知的 DNS 服务器提出域名解析。也就是说 Hosts 的请求级别比 DNS 高。当你的Hosts 文件里面有对应的 IP 时，它就会直接访问那个 IP，而不用通过 DNS。所以，当我们直接将Google、Twitter、Facebook 之类的 IP 放入 Hosts 文件后，就可以跳过 DNS的解析这一步，直接就行IP访问，不受 GFW 的 DNS污染干扰了。
```


>通俗易懂的说修改host后就能访问Google、Twitter、Facebook等被墙网站。

下面就来介绍修改hosts文件的方法
## windows

* 修改文件需要管理员权限

1. 找到文件目录C:\Windows\System32\drivers\etc\hosts
2. 把下载好的hosts文件全部内容复制到C:\WINDOWS\system32\drivers\etc目录中的hosts文件中
3. 保存后在重启浏览器输入https://www.google.com.hk看是否能访问
4. 如果还不可以访问在CMD窗口输入ipconfig /flushdns使其生效。

## Linux and Mac
1. Linux与Mac的hosts文件都在相同的目录下 **/etc/hosts**
2. 同样是用下载好的hosts替代原有的文件
3. Mac终端输入sudo killall -HUP mDNSResponder使其生效。
   Linux终端输入sudo systemctl restart NetworkManager。

注意 : 非systemd发行版，终端输入sudo rcnscd restart，如果不清楚请两个都试一次。

## Android

* 我们知道Android也是Linux系统中的一种，但其修改办法还是有些许不同

1. 需要获取root权限 
2. 文件所在路径/system/etc/hosts


补充一下：
>就是为什么 Hosts的IP要时不时更改，为什么 FB、Twitter 会仍旧上不去。是因为 GFW 的第二个大招，IP 封锁。比如访问国外一个 IP 无法访问，Ping 不通，tracert 这个 IP 后发现，全部在边缘路由器 (GFW) 附近被拦截。换言之，GFW 直接拦截带有这个 IP 头的数据包。所以，如果你更改的 IP 被封锁了，就算你过了 DNS 这一关，也仍旧不能翻过GFW。**而有些站，是直接被屏蔽，无论你怎么添加HOSTS都是不行的。**