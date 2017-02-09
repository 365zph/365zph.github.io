---
author: viviworld
comments: true
date: 2014-03-28 03:44:12+00:00
layout: post
link: http://www.labazhou.net/2014/03/huge-security-hole-in-sendgrid/
slug: huge-security-hole-in-sendgrid
title: Sendgrid的巨大安全漏洞
wordpress_id: 474
categories:
- 安全
tags:
- email
- Sendgrid
- 两步验证
- 比特币
- 社会工程攻击
- 邮件中继
---

[![Sendgrid巨大安全漏洞](http://www.labazhou.net/wp-content/uploads/2014/03/Sendgrid-huge-security-hole.jpg)](http://www.labazhou.net/wp-content/uploads/2014/03/Sendgrid-huge-security-hole.jpg)

本周我们发生了一起严重的安全事故，足以让我们震惊。虽然客户的账户没有遭到损害，但这是真正的千钧一发。

和很多公司一样，都想确保邮件能够成功到达你的收件箱，我们使用第三方邮件服务，Sendgrid，来确保发送能力。

几周前，我们收到了一份与Sendgrid技术支持聊天的记录，很明显有人试图通过社会工程攻击【注1】访问我们的账户。虽然Sendgrid没有在这个企图上跌倒，我们还是警告他们这次入侵，并要求他们保证将来社会工程攻击的企图也不会奏效。他们做了回复，并安慰了我们：


<blockquote>根据政策，我们从来不会更改一个账户的凭据或某个用户的邮箱地址，尤其是通过聊天或email工单。
我们会提供链接或说明帮助用户去操作，但是那些页面仅在正确的凭据下才能被访问到。</blockquote>


然而，事实表明这项政策本周被无视了，有人设法通过电话说服Sendgrid并更改了账户上的email地址。我们从他们那里收到了一封邮件，但为时已晚。攻击者已经登录到Sendgrid接管了。

他注册了一个域名，chunkhost.info，“你能帮我把我们的邮箱地址从support@chunkhost.com修改为support@chunkhost.info吗？”听起来足够可信，Sendgrid没有验证其他资料就完全同意了。


### 为什么有人想接管我们的Sendgrid账户？


Sendgrid有一个功能，允许你密送每一条外出消息到一个隔离的email地址。一旦他们激活了这个功能，他们将在其追踪的两个账户上发起密码重设的请求，这两个账户都和比特币相关。

密码重设邮件被真实地发送到了我们的客户，但也密送给了攻击者。有了密码重设链接，他们能够修改密码，进而访问我们客户的账户资料。

幸运的是，受影响的客户都使用了我们的两步验证功能。这意味着你不仅仅需要密码，还有你手机生成的一个token才能登录。

我们客户的账户得到了保护，攻击者被阻止了。但是这太悬了。

在大约20分钟里，我们注意到发生了什么，并阻止了他们的访问。我们关闭了密码重设功能，重置了所有会话，并切换到一个本地邮件中继【注2】。一旦我们确信控制了事态，我们才和Sendgrid进行沟通。昨天，他们这样告诉我们：


<blockquote>很明显，文件中的邮件地址被我们的系统修改……成了support@chunkhost.info，这完全证实了你的怀疑，攻击者说服了我们其中一名员工修改了文件中的邮件地址。在邮件地址被修改之后，他们能够容易地请求一个新密码，并获得账户访问权。这应当从来都不会发生的，我们会严肃对待类似情况。我对你们所作的一切表示歉意，我将保证向我们员工重申，我们有那样的政策，其存在都是有原因的。</blockquote>




### 谨慎对待第三方邮件发送商！


我们会继续自己发送邮件，同时探索其他的选择，但是其他公司应当引起重视，不要犯我们犯过的错误。如果你的账号曾经是入侵者的目标（特别是，如果你在做与比特币相关的事情），通过自己发送邮件来保护你自己和你的客户。

原文地址：[https://chunkhost.com/blog/15/huge_security_hole_in_sendgrid](https://chunkhost.com/blog/15/huge_security_hole_in_sendgrid)
注1：社会工程攻击（Social Engineering Attack)：[http://www.netchina.com.cn/users/0/115.html](http://www.netchina.com.cn/users/0/115.html)
注2：邮件中继：[http://www.baike.com/wiki/邮件中继](http://www.baike.com/wiki/邮件中继)
