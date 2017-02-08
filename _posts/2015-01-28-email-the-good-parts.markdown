---
author: viviworld
comments: true
date: 2015-01-28 09:43:42+00:00
layout: post
link: http://www.labazhou.net/2015/01/email-the-good-parts/
slug: email-the-good-parts
title: Email精粹
wordpress_id: 1604
categories:
- 网络
tags:
- DKIM
- DMARC
- email
- gmail
- newsletter
- outlook
- SMTP
- spam
- SPF
- Yahoo
---

原文地址（original source）：[https://www.petekeen.net/email-the-good-parts](https://www.petekeen.net/email-the-good-parts)

每个人都知道email是神马。你点击“写信”，填上收件人邮箱地址，写上你的信息，或许给个精辟的主题，点击“发送”。等一会儿，你的收件人打开他们的[邮件](http://www.labazhou.net/2014/03/email-receipts-a-missed-opportunity/)就看到你发送的信息。很简单，对吧？

在“发送”和“等一会儿”之间，发生着大量的有趣的事情。本文就带你一窥当你点击“发送”时，你的信息是如何走到收件人那里的。


### 基础


其实，一封email只是一个文本文件。当你发送邮件时，你的邮件客户端（比如Gmail、Mail.app或Outlook）为你的文本，注入一些信息到“headers”（在你的文本前面的、格式化的文本），再把它丢弃给邮件服务器。下面是一个简单的写好的邮件示例：


<blockquote>From: Pete Keen <pete@petekeen.net>
To: Joe Example <joe@example.com>
Date: Sun, 28 Dec 2014 09:52:03 -0600
Subject: This is a simple message

Here's some text in the message. Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis interdum in neque sed tincidunt. Nullam sed auctor libero, sed facilisis ligula. Pellentesque habitant morbi tristique senectus et netus et malesuada fames ac turpis egestas. Aliquam sit amet dui a ligula ultrices porta quis vel mi. Nulla ac urna augue. Donec euismod tristique odio eget convallis. Cras ac quam vel sapien pharetra luctus. Aliquam sem eros, auctor non fringilla sed, viverra non turpis. Sed suscipit egestas posuere. In hac habitasse platea dictumst. Nulla facilisi.</blockquote>


正如你看到的，一封简单的邮件真没有太多东西。消息可以更加复杂，带有multi-part HTML信息和附件，但本质上它们只是和headers一起被格式化好的文本文件。


### 邮件传输


在你的客户端（邮件用户代理）组合好你的信息之后，把它交给一个邮件服务器（邮件传输代理），在邮件最终到达收件人的收件箱之前，邮件服务器在某个时刻要把它交给其它至少一台服务器。邮件传输是通过简单邮件传输协议(Simple Mail Transfer Protocol，简称SMTP)运作的，SMTP是一种简单的、基于文本的协议。下面是一个简单的SMTP事务处理（蓝色的向右箭头线是我们发送给服务器的命令，黑色的向左箭头线是我们从服务器接收的信息）：


<blockquote>← 220 web01.bugsplat.info ESMTP Postfix
→ HELO client.bugsplat.info
← 250 web01.bugsplat.info
→ MAIL FROM: test@bugsplat.info
← 250 2.1.0 Ok
→ RCPT TO: pete@bugsplat.info
← 250 2.1.5 Ok
→ DATA
← 354 End data with .
→ From: test@bugsplat.info
→ To: pete@bugsplat.info
→ Subject: this is a test
→ 
→ Example test.
→ .
← 250 2.0.0 Ok: queued as CD76D606BB
→ QUIT
← 221 2.0.0 Bye</blockquote>


该事务处理从一个宣告开始，我们用HELO命令回应我们是谁。服务器以域名回答我们。

接下来，我们告诉服务器消息从谁那儿发出，它最终应该被交给谁，然后我们实际去发送该消息。这里的一个重要概念是`MAIL FROM`和`RCPT TO`命令，它们和实际的消息内容及其`From`和`To`头信息是分隔开的，它们可以完全不同【注1】。这实际上就是email中的“BCC”函数的实现过程，BCC的地址实际上是在`RCPT TO`发送的，但是主地址是在To头信息里。

邮件服务器每收到一次消息，就添加一个带有域名的Received头信息、发送方机器的域名、精确时间和一些其它信息，通常放在头信息栈的顶部。下面就是我们在上面发送的信息的、Received头信息。


<blockquote>Received: by 10.140.147.132 with SMTP id 126csp2632885qht;
Sun, 28 Dec 2014 09:44:19 -0800 (PST)
Received: from web01.bugsplat.info (web01.bugsplat.info. [192.241.250.244])
by mx.google.com with ESMTPS id kg1si49786991pad.162.2014.12.28.09.44.17
for <peter.keen@gmail.com>
(version=TLSv1.1 cipher=ECDHE-RSA-RC4-SHA bits=128/128);
Sun, 28 Dec 2014 09:44:18 -0800 (PST)
Received: from client.bugsplat.info (sales02.bugsplat.info [104.131.72.15])
by web01.bugsplat.info (Postfix) with SMTP id CD76D606BB
for <pete@bugsplat.info>; Sun, 28 Dec 2014 17:43:19 +0000 (UTC)</blockquote>


该流程请参看下面的图示：

[![email发送过程图解](http://www.labazhou.net/wp-content/uploads/2015/01/email-diagram.png)](http://www.labazhou.net/wp-content/uploads/2015/01/email-diagram.png)

从底部读取头信息（对应于图示顶部），`sales02.bugsplat.info`连接到`web01.bugsplat.info`（它是真正的服务器），并以`pete@bugsplat.info`为目标发送一条消息。web01配置成转交该地址给我的Gmail地址，因此它连接到了Google的邮件服务器，使用如上完全相同的信息传递该消息。在Gmail里，处理我的账号时，就再没有跳转了。一条消息每次在服务器之间发送时，都涉及到了SMTP。

大量其它信息存在于头信息里，包括唯一的消息ID、时间戳、你可以发送投诉的邮件地址和加密串。

你可能想知道`web01.bugsplat.info`是如何第一时间找到Gmail服务器的。它是怎样知道向哪里发送消息？它查看DNS，Google已经为域名gmail.com设置了MX（邮件转发）记录。如下所示：


<blockquote>$ dig +short gmail.com mx
5 gmail-smtp-in.l.google.com.
10 alt1.gmail-smtp-in.l.google.com.
20 alt2.gmail-smtp-in.l.google.com.
30 alt3.gmail-smtp-in.l.google.com.
40 alt4.gmail-smtp-in.l.google.com.</blockquote>


邮件服务器按照优先级尝试，越小的数字有着越高的优先级。如果一个接收邮件服务器没有响应，发送方将尝试列表中的下一个，如果尝试完了，它将在重试之前挂起这个消息。你可以简单地使用`dig`工具查看你公司的MX记录：


<blockquote>$ dig +short yourdomain.com mx</blockquote>


更多关于DNS的信息，可以查看[DNS：The Good Parts](https://www.petekeen.net/dns-the-good-parts)。


### Spam


Spam【注2】是一个有些模糊的术语，但是可归结为不想要的消息。包括你没有注册的、不想要的、和/或活跃地有害的东西。

Spam已经存在很长时间了。事实上，互联网上第一条被确认的不想要的消息，发送于1978年，当时SMTP甚至没有普遍应用（该spam是Digital Equipment Corproation公司发布会的一个广告）。从那以后，它演变成了真正的业务模型。药品、交易、保险和世界上的任何其它事物，都通过spam消息做广告，发送的流氓邮件服务器达数十亿台。除了真正（不请自来的除外）的产品，同样的技巧被用来发送带有恶意的消息，比如钓鱼攻击。

隐含在邮件下面的协议，名叫SMTP，来自于一个比较文明的时代。在基础协议上，有着很少的检查或校验，这意味着伪造一条消息的各个部分是非常容易的，包括头信息。如果我知道你的地址，我就能轻松构造一条消息，整个外观看起来就像从你发出来的。


### 事务性邮件 VS Newsletter


今天有两种宽泛的邮件，而不是个人信件往来。事务性邮件通常是你的应用程序为响应用户而产生的，并发给一个用户，一次一封。

另一方面，newsletter被视作“群发”邮件。它们发给清单上的人们，同时发。这不代表它们就是spam，只是你在同一时刻发送了大量的、差不多完全相同的消息。

邮件服务提供商对这些不同种类消息做了区分。比如，spam规则被更加严格地应用到他们所检测到的群发邮件。Gmail根据你的消息中的关键词和通常格式，或许自动决定把你的群发邮件放入它们的“推广”标签里。


### 信任


过去的几年里，技术已经发展到帮助你阻止伪造邮件，帮助Gmail和Yahoo之类的大型提供商信任你的消息，包括事务性的邮件和newsletter。它们是：



	
  * **SPF**，发件人策略框架【注3】。让世界知道用你的域名发送邮件的服务器是验证过的。

	
  * **DKIM**，DomainKeys Identified Mail【注4】。允许发送加密签名消息给邮件服务器，验证你授权他们发送邮件。

	
  * **DMARC**【注5】。为收件人服务器指定一种策略，告诉它们如果消息在SPF或DKIM检查上失败了，应该做什么。


我谈到过[根据DMARC来修复你的邮件传送能力](https://www.petekeen.net/fix-your-email-deliverability-with-dmarc)。在未来的文章里，我会深入讨论每个话题，讨论它的历史、优势以及如何更好地部署。

附：你的邮件传送能力加强了吗？**Mail Rep**帮助你的业务提高达到率，只需两周时间。[点击这里了解Mail Rep](https://www.petekeen.net/mail-rep)。



	
  * 注1：邮件DATA中的TO，FROM等内容和MAIL FROM和RCPT TO命令中的email不同，可以随便造假。可参考：[http://www.cppblog.com/prayer/archive/2011/12/13/162021.html](http://www.cppblog.com/prayer/archive/2011/12/13/162021.html)

	
  * 注2：垃圾邮件（英语：spam），指的就是“不请自来，未经用户的许可强行塞入邮箱的电子邮件”。[http://zh.wikipedia.org/wiki/%E5%9E%83%E5%9C%BE%E9%82%AE%E4%BB%B6](http://zh.wikipedia.org/wiki/%E5%9E%83%E5%9C%BE%E9%82%AE%E4%BB%B6)

	
  * 注3：发件人策略框架（英语：Sender Policy Framework；简称SPF；RFC4408）是一个电子邮件验证系统，目的是解决电子邮件伪造。SPF允许管理员设定一个DNS TXT记录或SPF记录设定发送邮件服务器的IP范围。[http://zh.wikipedia.org/wiki/%E5%8F%91%E4%BB%B6%E4%BA%BA%E7%AD%96%E7%95%A5%E6%A1%86%E6%9E%B6](http://zh.wikipedia.org/wiki/%E5%8F%91%E4%BB%B6%E4%BA%BA%E7%AD%96%E7%95%A5%E6%A1%86%E6%9E%B6)

	
  * 注4：DKIM（DomainKeys Identified Mail）是一种电子邮件的验证技术，使用密码学的基础提供了签名与验证的功能。[http://zh.wikipedia.org/wiki/DKIM](http://zh.wikipedia.org/wiki/DKIM)

	
  * 注5：DMARC全称为Domain-based Message Authentication, Reporting & Conformance，它建立在SPF、DKIM这两份主流邮件认证协议的基础上，为邮件发件人地址（邮件头部的From字段）提供强大保护，并在邮件收发双方之间建立起一个数据反馈机制。它加大了那些通过伪造发件人地址手段的网络钓鱼者的难度。任何企业、品牌使用了DMARC，都可以很方便地告诉邮件接收方如何认证我的邮件，如何处理伪造我的邮件，如何把伪造邮件的数据反馈给我。对于顺利通过DMARC验证的邮件，则会像往常一样接受邮件服务商的反垃圾邮件系统等过滤器的检查，并最终投递到收件人的邮箱中。[http://mail.blog.163.com/blog/static/82209424201312275955605/](http://mail.blog.163.com/blog/static/82209424201312275955605/)



