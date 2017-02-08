---
author: viviworld
comments: true
date: 2015-07-10 01:32:13+00:00
excerpt: 如果你用到了 session 和会话 cookie，问题就来了。每次页面刷新，客户端的响应将含有一个空的 cookie：header 头，因此服务器将在每次请求都生成一个新的
  Set-Cookie header 头。如果你的（子）域名含有下划线，cookie 就无法在 IE 下正常运行。
layout: post
link: http://www.labazhou.net/2015/07/internet-explorer-wont-allow-cookies-subdomains-underscores/
slug: internet-explorer-wont-allow-cookies-subdomains-underscores
title: 为什么 IE 不支持（子）域名含有下划线
wordpress_id: 2256
categories:
- 浏览器
- 编程
tags:
- bug
- cookie
- DNS
- ie
- Spartan
- 微软
---


	
  * 原文地址（original source）：[https://ma.ttias.be/internet-explorer-wont-allow-cookies-subdomains-underscores/](https://ma.ttias.be/internet-explorer-wont-allow-cookies-subdomains-underscores/)

	
  * 作者（author）：[https://twitter.com/mattiasgeniar](https://twitter.com/mattiasgeniar)





* * *



我今天花了很多时间调试这个 bug。我将永远不会忘记，IE（Internet Explorer） 对于含有下划线的（子）域名，是如何处理其 cookie 的。

显然这是事后诸葛亮。事实上，曾经有一个 [Internet Explorer FAQ](http://blogs.msdn.com/b/ieinternals/archive/2009/08/20/wininet-ie-cookie-internals-faq.aspx)，描述了 IE 在呈现含有下划线的域名或子域名的网页时，它会做出怎样的反应。要不是这一次遇到，我甚至不知道它曾被提过。


### 我的问题


PHP 里的会话 cookie 在 Chrome 和 Firefox 里运行正常，但是在 IE 不正常。甚至在最新的 IE 版本、IE11 亦是如此。这貌似属于设计上的 bug，在 IE 寿终正寝之前将一直存在。

或许 [Project Spartan，又叫 Microsoft Edge](https://ma.ttias.be/meet-microsofts-project-spartan-new-ie6/) 将会改变这种陈旧的行为？


### 你说的是哪个 bug？


如果你的 web 应用程序使用的域名或子域名含有下划线，IE 将拒绝存储 cookie，任何种类的 cookie，从会话 cookie 到持久化 cookie。你的 web 服务器将依赖 Set-Cookie header 头，而客户端将乐于无视之。



	
  * 正常的域名：something.domain.tld。

	
  * 不正常的域名：some_thing.domain.tld


如果你用到了 session 和会话 cookie，问题就来了。每次页面刷新，客户端的响应将含有一个空的 cookie：header 头，因此服务器将在每次请求都生成一个新的 Set-Cookie header 头。

**如果你的（子）域名含有下划线，cookie 就无法在 IE 正常运行。**


### 什么原因？


这个行为在微软的 [kb316112](https://support.microsoft.com/en-us/kb/316112/en-us) 有介绍，它是一个 Windows 补丁，用于解决 CVE [MS01-005](https://technet.microsoft.com/en-us/library/security/ms01-055.aspx)，可追溯到 2001 年。

这是从 2001 年就出现的 cookie 漏洞，直到今天我们仍然经受其影响。

最初的 CVE 修复了这个问题：


<blockquote>该补丁消除了影响 IE 的三个漏洞。第一个涉及到 IE 处理没有「.」的 IP 地址的方式。

如果一个网站指定使用不含「.」的 IP 格式（比如，http://031713501415，而非 http://207.46.131.13），该请求在特定方式下就是不正确的，那么 IE 将认为这个网站不是互联网网站。它将把该网站视作内部网（Intranet）网站【注1】、只能打开内部网网域内的网页，而不能打开正确域下的网页。

这要求网站只需要较少的安全限制就可运行。

[MS01-051](https://technet.microsoft.com/library/security/ms01-051)</blockquote>


那么，为什么到了今天，针对 CVE 的修复仍然在影响着我们呢？

做为 [kb316112](https://support.microsoft.com/en-us/kb/316112/en-us) 的修复部分，微软提出了针对 DNS 下域名的更加严格的校验。这本质上意味着，所有的域名必须遵循 DNS RFC。它最初可追溯到 [RFC606 (1973)](http://tools.ietf.org/html/rfc606) 和 [RFC608 (1974)](http://tools.ietf.org/html/rfc608)。

猜猜最初的 DNS 语法没有包含什么？猜对了：**下划线**。

微软指出，将阻止任何含有不合法的 DNS 字符的 cookie。


<blockquote>安全补丁 MS01-055 将阻止服务器使用不正确的命名语法设置 cookie。含有 cookie 的域名只能在域名和服务器名字中使用字母数字字符（「-」或「.」）。

如果服务器名字含有其它字符，比如下划线（「_」），那么 IE 将阻止其 cookie。

[安全补丁 MS01-055](https://support.microsoft.com/en-us/kb/316112/en-us)</blockquote>


下面是我认为它们的错误之处。

**主机名字的确不支持下划线，但是它们在域名里是合法的。**不同之处在于「主机名字」和「域名」的解释。

发布于 1997 年的 RFC2181，明确地指出：


<blockquote>DNS 本身对于用来表示资源记录的具体标签只做了一个限制，这个限制与标签和全名的长度有关……

DNS 协议的实现不必把任何限制附加到可被使用的标签上。尤其是，DNS 服务器一定不能因为某个域含有可不被某些 DNS 客户端程序所接受的标签而拒绝它。

[RFC2181](http://www.ietf.org/rfc/rfc2181.txt)</blockquote>


对我而言，微软貌似引入了一种错误的校验，且混淆了主机名字和域名。


### 如何修复？


只能给 IE11 代码库发送一个修复的 [Pull Request](http://www.labazhou.net/2014/03/beginners-contributing-to-open-source/)！

好了，既然这明显不是一种选择，那么，除了在你的互联网域名中避免使用下划线，真没有其它办法了。对于自动生成的子域名（我经历过），尤为恼人，下划线偶尔被 IE 用户带入，就意想不到地出错了。

未来，我希望微软审查一下含有下划线的域名中的、设置 cookie 的策略。或许它们在遵循 RFC & 标准方面是正确的（尽管这是有争议的），不过它们是唯一这样做的浏览器。

你应该放弃原则，还是遵循采用了非标准实践的人民大众？



* * *



如果你喜欢这个内容，你可以分享到你的社交网络，帮我传播这个问题。谢谢！



* * *






	
  * 注1：内部网（Intranet），又称企业内部网或内联网，是一个使用与因特网同样技术的计算机网络，它通常创建在一个企业或组织的内部并为其成员提供信息的共享和交流等服务，例如万维网、文件传输、电子邮件等。[https://zh.wikipedia.org/wiki/%E5%86%85%E9%83%A8%E7%BD%91](https://zh.wikipedia.org/wiki/%E5%86%85%E9%83%A8%E7%BD%91)


