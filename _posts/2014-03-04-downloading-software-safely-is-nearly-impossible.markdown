---
author: viviworld
comments: true
date: 2014-03-04 07:01:05+00:00
layout: post
link: http://www.labazhou.net/2014/03/downloading-software-safely-is-nearly-impossible/
slug: downloading-software-safely-is-nearly-impossible
title: 安全地下载软件几乎是不可能的
wordpress_id: 392
categories:
- 安全
- 软件
tags:
- https
- javascript
- md5
- putty
- RSA
- windows
---

假如你有一个新品牌的Windows笔记本，你现在真是太兴奋了。你非常确定美国国家安全局没有[在路上截取它](http://www.forbes.com/sites/erikkain/2013/12/29/report-nsa-intercepting-laptops-ordered-online-installing-spyware/)，这样它只预装了讨厌的Microsoft、Lenovo和一些Lenovo的商业伙伴的吃内存的软件（goatware【注1】）。你现在需要一个SSH客户端，便于你连上Linux机器，一切将是美好的。下面是如何获取一个SSH客户端。



	
  1. 网上搜索[[windows ssh client](https://www.google.com/search?q=windows+ssh+client&oq=windows+ssh+client)]。

	
  2. 点击第一个进入[http://www.putty.org/](http://www.putty.org/)。现在，既然你想找到好的、真的由Simon Tatham写的PuTTY，而不是一些未经验证的恶意软件，你检查了icon锁，和“https://" URL协议。没有，开始担心，据说Tatham是一个加密软件开发者。

	
  3. 不要担心；[putty.org甚至不归Tatham所有](http://www.whois.com/whois/putty.org)。它目前被一个名叫”denis bider“的家伙拥有，他可能只是喜欢占用其他人的产品名称做域名，并提供链接。好吧，让我们点击这个链接……

	
  4. [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)。啊，部分URL正好含有Tatham的名字，那么……等等，是这样子吗？事实上，不是；只有域名能够表面站点所有权。[Richard Kettlewell目前拥有greenend.org.uk](http://www.whois.com/whois/greenend.org.uk)。

	
  5. 找了找，还是没找到icon锁和”https://"协议。还有，密码学和安全软件------和所有软件一样------不应该总是通过一个验证过的服务来发布吗？

	
  6. 手动增加“https://"。看到这个站点对HTTPS没有响应。开始怀疑站点的真实性。[![putty https打不开](http://www.labazhou.net/wp-content/uploads/2014/03/putty-https.png)](http://www.labazhou.net/wp-content/uploads/2014/03/putty-https.png)

	
  7. 不要担心！页面往下拉，可以看到Tatham提供的RSA和DSA加密的二进制签名，比如[http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe.RSA](http://the.earth.li/~sgtatham/putty/latest/x86/putty.exe.RSA). 注意[域名earth.li当前的所有者是Jonathan McDowell](http://www.whois.com/whois/earth.li)。当你点击链接到签名的时候，你会真正得到某样东西的RSA签名，但是没办法确切知道签名者是谁或他的签名内容------任何能够违背网站放置有害的可执行PuTTY程序的攻击者（或者在你连接到网站时，遭受中间人攻击【注2】）也能够容易地搞定这个签名。

	
  8. 试图换成HTTPS来下载签名，[https://the.earth.li/~sgtatham/putty/latest/x86/putty.exe.RSA](https://the.earth.li/~sgtatham/putty/latest/x86/putty.exe.RSA)，注意到服务器返回404.越来越怀疑了。

	
  9. 深呼吸一下，[看看Tatham对于签名机制如此复杂的解释，但为什么发布渠道是匿名的呀](http://www.chiark.greenend.org.uk/~sgtatham/putty/keys.html)。

	
  10. 对Tatham的PGP密钥是否经过了注册中心表示严重怀疑，比如MIT的PGP密钥服务器。[没有](http://pgp.mit.edu/pks/lookup?search=tatham&op=index)。

	
  11. 严重怀疑MIT的PGP密钥服务器是不是没有验证过。

	
  12. 想起来，即使你从一个未验证的密钥服务器获取了Tatham的PGP密钥，你仍然需要下载一个PGP程序。与其重复GnuPG教程里的步骤，不如放弃，开始决定下载一个未验证的PuTTY的拷贝。

	
  13. 注意到Tatham让你参考 [http://www.pc-tools.net/win32/freeware/md5sums/](http://www.pc-tools.net/win32/freeware/md5sums/) ，为Windows准备的MD5校验器，慎重考虑后，至少检查一下PuTTY摘要里的匿名（最终是没用的）MD5。发现[http://www.pc-tools.net](http://www.pc-tools.net)也没有对HTTPS的响应，不浪费时间了。

	
  14. 已经下载了putty.exe，在点击之前思索良久。注意，当你点了可执行程序，它将在这台Windows机器上以你的用户账号的所有权限运行。它有能力读取、删除和修改你所有的文档和邮件，也能够把你收藏的色情东西发到Wikipedia。

	
  15. 希望不要发生。

	
  16. 不管了，点击putty.exe。连接到你的Linux服务器上的账户，现在也处于来自因特网的一个未验证的程序的控制之下了。想了想，如果这次下载没有危害，自称为”PuTTY“的东西一定是被可能了解如何用C实现RSA的开发者编写的，他不知道如何或为什么使用RSA。（在这一点上，你曾经连接到你的真实Linux服务器上了吗？很难理解）

	
  17. 突然想到，[Web Crypto](http://www.w3.org/TR/WebCryptoAPI/)看起来出奇地正常了，而[不管原生代码沙文主义的反对](http://rdist.root.org/2010/11/29/final-post-on-javascript-crypto/)。至少JavaScript运行在[同源策略](http://en.wikipedia.org/wiki/Same-origin_policy)下【注3】，[Chrome的多进程模型](http://www.chromium.org/developers/design-documents/process-models)将其放在沙箱里，因此它不能完全以你的Windows用户账户来运行。

	
  18. 失望。


原文地址：[http://noncombatant.org/2014/03/03/downloading-software-safely-is-nearly-impossible/](http://noncombatant.org/2014/03/03/downloading-software-safely-is-nearly-impossible/)



	
  * 注1：goatware：非常吃内存的软件，让你的电脑变慢。[http://www.urbandictionary.com/define.php?term=Goatware](http://www.urbandictionary.com/define.php?term=Goatware)

	
  * 注2：中间人攻击（Man-in-the-MiddleAttack，简称“MITM攻击”）是一种“间接”的入侵攻击，这种攻击模式是通过各种技术手段将受入侵者控制的一台计算机虚拟放置在网络连接中的两台通信计算机之间，这台计算机就称为“中间人”。[http://baike.baidu.com/view/1531871.htm](http://baike.baidu.com/view/1531871.htm)

	
  * 注3：JavaScript的同源策略：[https://developer.mozilla.org/zh-CN/docs/Same_origin_policy_for_JavaScript](https://developer.mozilla.org/zh-CN/docs/Same_origin_policy_for_JavaScript)


