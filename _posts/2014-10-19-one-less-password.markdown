---
author: viviworld
comments: true
date: 2014-10-19 02:49:24+00:00
layout: post
link: http://www.labazhou.net/2014/10/one-less-password/
slug: one-less-password
title: 少一些密码
wordpress_id: 1127
categories:
- 安全
tags:
- email
- facebook
- Mozilla
- Webmaker
- 密码
---

在Mozilla，我帮助开发一个不依赖密码的登录系统。它也不使用诸如Facebook之类的社会化平台的登录。我认为我们已经创造了并行的替代方案------我乐于看到被使用，被其他设计师和开发者继续推动发展。当我们彼此身边的、需要密码的网站越少，被忘记的、被盗的、跨站点用一个密码的情况就会越少。

[![加入按钮](http://www.labazhou.net/wp-content/uploads/2014/10/join-sign-in-buttons-300x66.png)](http://www.labazhou.net/wp-content/uploads/2014/10/join-sign-in-buttons-300x66.png)


<blockquote>在本文，你可以了解到系统设计和用户体验。如果你对整个事情感兴趣，可以移步到[Webmaker blog上的文章](https://blog.webmaker.org/one-less-password/)。</blockquote>




### 加入------快速、简单


我们简化了加入Webmaker的流程。以前，在人们能够访问Webmaker之前，需要首先注册一个角色。这是莫名其妙的（因为名字和平台可能是新的、也不熟悉）。现在，新用户只需要输入他们的邮箱、选择一个用户名。他们马上就能访问Webmaker，不需要验证其账户。验证发生在用户首次登陆、或如果他们试着公布时去手动触发。（我们即将支持电话号码和短信，以作为邮箱的代替。）

[![join1](http://www.labazhou.net/wp-content/uploads/2014/10/join1.png)](http://www.labazhou.net/wp-content/uploads/2014/10/join1.png)


### 登录 ------不需要密码


登录就更有意思了。

网上已经有很多人讨论过这个话题了，我采用了通常的忘记密码的体验，并改造成主要的登录表单。

[![sign-in](http://www.labazhou.net/wp-content/uploads/2014/10/sign-in.png)](http://www.labazhou.net/wp-content/uploads/2014/10/sign-in.png)

一个人能够用他们的用户名和邮箱地址登录。Webmaker发送一封邮件，只有他们能够访问。这封邮件包含了一个登录按钮，和“记住我”的链接。这两种选择都会把他们带入网站、无需更多的点击。

[![登录表单](http://www.labazhou.net/wp-content/uploads/2014/10/login-email-2.png)](http://www.labazhou.net/wp-content/uploads/2014/10/login-email-2.png)


### 登录 ------跨设备


一些人是在学校或图书馆的公共电脑上使用Webmaker的。他们或许在手机上收到了登录邮件。对于这种情况，这封邮件将包含一个简短的key，他们可以看到并跨设备拷贝下来（上面邮件的黄色部分）。下面的图表描述了这个流程。

[![跨设备登录的流程图](http://www.labazhou.net/wp-content/uploads/2014/10/sign-in-across-devices.png)](http://www.labazhou.net/wp-content/uploads/2014/10/sign-in-across-devices.png)

这个key是临时的。一次使用或30分钟后，都会过期。如果被滥用，它也会在暴力破解时过期失效。


### 登录 ------可选的密码


对于在图书馆的公共电脑上工作的人们来说，密码可能是有用的。我们让密码变成可选择的，添加起来比较容易。事实上，人们在旅游的时候添加一个密码，当他们回到家里时就删除它，针对这两种情况的不同而顺畅地切换，以获取最佳体验。

[![sign-in-password](http://www.labazhou.net/wp-content/uploads/2014/10/sign-in-password.png)](http://www.labazhou.net/wp-content/uploads/2014/10/sign-in-password.png)

我想检验的一个理论是：如果我们在人们努力回忆自己密码的时刻，允许他们脱离密码，那么我们将增加这种替代登录方式的普及和理解。

[![password-opt-out](http://www.labazhou.net/wp-content/uploads/2014/10/password-opt-out.png)](http://www.labazhou.net/wp-content/uploads/2014/10/password-opt-out.png)

密码可以在个人首页上添加。上面展示的登录邮件上的链接，也可以做到。这个链接既做为登录链接，又把用户导向设置密码的地方。


### 服务器端的流程


人们将拥有根据他们的状况量身定制的体验，支持他们通过链接、key或者密码登录。服务器流畅地管理者这种体验，甚至对于那些忘记了以前建立过账户的人们，也是如此。

[![免密码的服务器端的流程图](http://www.labazhou.net/wp-content/uploads/2014/10/login-server-flow.png)](http://www.labazhou.net/wp-content/uploads/2014/10/login-server-flow.png)


### 反馈和讨论


我们欢迎你的反馈和疑问，在[Webmaker](https://blog.webmaker.org/one-less-password/)上有更多关于这个项目的信息。你也可以在我们的开发人员Chris DeCairos写的文章里找到更多的[技术讨论](https://chrisdecairos.ca/one-time-passwords-pt-2/)。


### 致谢


略

原文地址：[http://notebook.ideapublic.org/2014/one-less-password/](http://notebook.ideapublic.org/2014/one-less-password/)
