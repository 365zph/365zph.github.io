---
author: viviworld
comments: true
date: 2014-04-02 01:51:03+00:00
layout: post
link: http://www.labazhou.net/2014/04/why-we-stopped-using-twitter-sso/
slug: why-we-stopped-using-twitter-sso
title: 为什么我们停止使用Twitter的单点登录
wordpress_id: 505
categories:
- 安全
tags:
- apple
- Buffer
- facebook
- iPhone
- SSO
- twitter
---

## 它真正简化了登录，但是为什么我们在Buffer的iPhone版拒绝用户使用Twitter的单点登录。


我们一直在Buffer的iPhone版使用Twitter iOS里的原生身份验证选项。直到去年我们出现了一次安全漏洞。


### 问题


Twitter SSO（单点登录）允许我们让用户登录到app，由于我们需要访问token来让Buffer张贴信息，甚至在app没有运行的时候，我们也不得不实现反向身份验证。这需要在app bundle包含Buffer的OAuth细节。

因此当我们去年遭遇安全漏洞的时候，我们快速地重设了Twitter应用程序的OAuth细节，这意味着iPhone app上的细节变成不合法了。app里的Twitter身份验证的SSO对任何人都不起作用了，并不是说对于新用户或现存用户的最大体验。

我们快速修改了app，让Twitter身份证验证恢复正常，并向app商店申请快速review正确的OAuth细节。幸运的是，苹果出乎意料地接受了我们的快速review请求，一切回到正轨。


### 将来怎么避免类似情况


不管什么原因我们未来都想消除类似现象再次发生的可能性。因此我们花时间使用SSO的方式、而没有用到现在需要的key/secret。

试了大量的可能解决方案，我们现在去掉了面向Twitter的SSO，尝试了大量方法在其它地方使用反向身份验证来获取访问token，但一无所获。

我们现在通过Buffer API来使用OAuth。我们可以在任何需要的时候去修改key/secret，而不必发布新的app，这意味着我们不会再次遇到Twitter身份验证被完全破坏的情况了。

现在我们把同样的解决方案用在了下次更新iPhone版的其它网络。对于Facebook唯一不同的是，我们使用它们的iOS SDK和SSO选项，因为我们不必包含key/secret。把这种方案应用到其它网络意味着具有相同的体验，我们没有在身份验证的混合模式选择'n'。

一旦我们找到能够方法来保证一切安全、易于更新，如果我们不得不重设任何细节，我们也能够在app里恢复，那么我们愿意重新使用Twitter的SSO。如果你任何想法，我们乐于倾听！

如果你想帮助改进iPhone版Buffer，以及致力于iPad版Buffer，那么为什么不加入我们的小团队呢！

原文地址：[https://medium.com/buffer-posts/bdd4f074d3b6](https://medium.com/buffer-posts/bdd4f074d3b6)
