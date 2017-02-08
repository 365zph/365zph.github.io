---
author: viviworld
comments: true
date: 2015-03-08 10:19:17+00:00
layout: post
link: http://www.labazhou.net/2015/03/how-to-create-a-tor-onion-site/
slug: how-to-create-a-tor-onion-site
title: 如何创建一个 Tor .onion 网站[更新]
wordpress_id: 1688
categories:
- 安全
- 软件
tags:
- debian
- nginx
- ssh
- Tor
- VPS
- 洋葱路由
- 防火墙
---


	
  * 原文地址（original source）：[https://scottlinux.com/2013/10/11/how-to-create-a-tor-onion-site/](https://scottlinux.com/2013/10/11/how-to-create-a-tor-onion-site/)

	
  * 作者（author）：[https://twitter.com/scottlinux](https://twitter.com/scottlinux)


[![如何创建一个 Tor .onion 网站](http://www.labazhou.net/wp-content/uploads/2015/03/tor-the-onion-router.jpg)](http://www.labazhou.net/wp-content/uploads/2015/03/tor-the-onion-router.jpg)

Tor 隐藏服务使用 .onion 域名。我将向你演示如何创建一个安全配置以阻止信息泄露、隐藏服务的 .onion 网站。

**注意：这是严肃的话题。**本向导目标是乐于运行 Linux 服务器的人群。注意安全。

一些基本提示：



	
  * 不要在这台服务器上运行或做其它事情。

	
  * 在新服务器或 VPS 上进行全新安装。

	
  * 不要保留或运行来自 VPS 提供商那儿的任何服务。

	
  * 用 Paypal 支付你的 VPS 服务，不过最好使用 Bitcoin。

	
  * 不要向 VPS 提供关于你的任何身份信息。

	
  * 不要在这台服务器上运行 Tor 中继，因为 Tor 中继在真实世界的公开 IP 是公开的。

	
  * 不要从这台服务器发送电子邮件。

	
  * 不要运行讨厌的或卑鄙的 web 软件。如果你的 web 软件有管理员登陆或管理员账号，[把密码改成复杂的 26 个字符组成的密码](http://www.labazhou.net/2014/07/how-a-password-changed-my-life/)。很多 Tor 网站被攻破只是某人猜到了管理员登陆密码。

	
  * 避免使用任何 JavaScript 之类脚本的 web 软件。

	
  * 确保你的 web 应用不会泄露任何错误信息或身份信息，比如在错误信息中的真实公开 IP。

	
  * 审查 web 前端代码，确保它不会从 jquery.com、Google Fonts 或任何外部服务拉取资源。

	
  * 及时做好 VPS 的安全更新。


**本向导使用 nginx 为使用 Debian Wheezy 的 Tor 提供网站文件服务。nginx 将被配置为只监听 Tor，只可通过 Tor 访问。**


### nginx


如果你还没有它，请安装 nginx：


<blockquote>$ sudo apt-get install nginx</blockquote>


nginx默认会发送一个当前运行的版本信息广播。通过设置下面文件中的 `server_tokens` 为 `off`，以关闭 nginx 版本信息：

/etc/nginx/nginx.conf：


<blockquote>http {
...
server_tokens off;
...</blockquote>


在同样的文件，彻底关闭来自 nginx 的日志：


<blockquote>http {
...
##
# Logging Settings
##
#access_log /var/log/nginx/access.log;
#error_log /var/log/nginx/error.log;
error_log /dev/null crit;</blockquote>




### 配置 nginx 监听 localhost 8080 端口


下面是你可以找到的、一个完整的可获取的默认文件。

网站 html 文件的位置在 /usr/share/nginx/www，这是 Debian 默认位置（可以随意修改网站根目录！）。

/etc/nginx/sites-available/default


<blockquote>server {
listen 127.0.0.1:8080 default_server;
server_name localhost;

root /usr/share/nginx/www;
index index.html index.htm;

location / {
allow 127.0.0.1;
deny all;

}
}</blockquote>




### 重启 nginx




<blockquote>$ sudo service nginx restart</blockquote>


关闭 rsyslog 以关闭任何系统日志。


<blockquote>$ sudo apt-get remove --purge rsyslog</blockquote>


关闭所有可被用来发送邮件的 email MTA 软件。


<blockquote>$ sudo apt-get remove --purge exim
$ sudo apt-get remove --purge postfix
$ sudo apt-get remove --purge sendmail</blockquote>


删除 wget，如果被连累了，它可通过恶意脚本识别你的主机。


<blockquote>$ sudo apt-get remove wget</blockquote>


如果开启 ssh，关闭 Debian 版本信息，这可用于从公开 IP 识别出 Debian 版本。

/etc/ssh/sshd_config


<blockquote>DebianBanner no</blockquote>




### 安装 Tor


按照 torproject.rog 文档，像这里所演示的去添加 Debian repo，然后你可以从 Tor 项目代码库，通过 sudo apt-get install tor 来安装。


### 编辑 /etc/tor/torrc


现在 Tor 安装好了，编辑 /etc/tor/torrc 确保下面的几行是正确的：


<blockquote>HiddenServiceDir /var/lib/tor/hidden_service/
HiddenServicePort 80 127.0.0.1:8080</blockquote>


保持上面的文件，然后启动（或重启）Tor。


<blockquote>$ sudo service tor start</blockquote>


当 Tor 启动时，它仍然在你的 HiddenServiceDir 文件夹创建了私钥，也创建了你唯一的 .onion 主机名。

下面是这些文件的样子。当然，你应该永远不要暴露或显示你的私钥！保密。下面的密钥是供演示和学习之用。


<blockquote>root@starbuck:~# cd /var/lib/tor/hidden_service/
root@starbuck:/var/lib/tor/hidden_service# ls
hostname private_key
root@starbuck:/var/lib/tor/hidden_service# cat private_key
-----BEGIN RSA PRIVATE KEY-----
MIICXAIBAAKBgQC9ymfMgQk12AFT4PXWV+XfmZ1tVDaGajya/jIuwnwtjFdMWe7m
VDWMjs8Z02GGJhH6tIIpoDUrWLi+YchNHlQBi2AnBFzAoSlfRcvobeBAaWuQn+aH
Uzr+xVXOADSIcfgtT5Yd13RKmUEKFV8AO9u652zYP1ss0l+S2mY/J/t/3wIDAQAB
AoGAMjQwcPBRN2UENOP1I9XsgNFpy1nTcor3rShArg3UO1g8X34Kq/Lql1vPfM1l
ps67Qs4tAEXYyraVaAcFrSCwp6MyeKYwxZtT7ki7q3rbMycvbYquxquh0uGy4aed
K8XWjPrUv3yzQSYslOehVWMTH7xTzaOvp5uhpAlHFRqN5MECQQDmpFkXmtfEGwqT
bRbKegRs9siNY6McWBCGrYc/BrpXEiK0j2QcrjC/dMJ4P9O4A94aG4NSI/005fII
vxrOmD9VAkEA0qhBVWeZD7amfvPYChQo0B4ACZZdJlcUd/x1JSOYbVKvRCvJLxjT
5LMwg93jj2m386jXWx8n40Zcus6BTDr6YwJBAKH8E0ZszdVBWLAqEbOq9qjAuiHz
NH+XqiOshCxTwVOdvRorCxjJjhspGdvyl/PJY5facuShuhgI13AlJ+KpMvECQHDJ
l1lzw1bPc2uLgUM8MfHj7h8z+6G4hAQODmaZHVaDK8XzL59gyqqrajFgTyOM9emm
n89w6flcxe9a+41mEoMCQBaM91yvrfp7N9BeDMCHlSDfAzX7sDqQn44ftHvZZI9V
4IouuRuLlqN0iaw4V73v3MUeqXoasmdeZ89bVGhVrC8=
-----END RSA PRIVATE KEY-----
root@starbuck:/var/lib/tor/hidden_service# cat hostname
juyy62wplbkk7gzy.onion
root@starbuck:/var/lib/tor/hidden_service#</blockquote>




### 配置并使用防火墙


启用防火墙，有选择地允许 22 端口。如果稍微偏执些，根本不要允许 22 端口，仅仅从提供商的控制面板控制台来管理。


<blockquote>$ sudo apt-get install ufw
$ sudo ufw allow ssh
$ sudo ufw enable</blockquote>


运气好的话，你现在应该看到基于 .onion 地址的默认 nginx 页面了！

[![基于 .onion 地址的默认 nginx 页面](http://www.labazhou.net/wp-content/uploads/2015/03/tor-onion-hiddenservice.png)](http://www.labazhou.net/wp-content/uploads/2015/03/tor-onion-hiddenservice.png)
