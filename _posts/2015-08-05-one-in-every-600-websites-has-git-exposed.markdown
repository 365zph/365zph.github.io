---
author: viviworld
comments: true
date: 2015-08-05 01:51:57+00:00
excerpt: 对外暴露你的 .git 文件夹，属于低级错误。因为任何人都可以下载你的整个源代码库，后者常包括数据库密码、salt、hash 和第三方 API key、或用户名和密码。
layout: post
link: http://www.labazhou.net/2015/08/one-in-every-600-websites-has-git-exposed/
slug: one-in-every-600-websites-has-git-exposed
title: 每 600 个网站当中就有 1 个网站暴露了 .git
wordpress_id: 2356
categories:
- 安全
tags:
- api
- aws
- Git
---


	
  * 原文地址（original source）：[http://www.jamiembrown.com/blog/one-in-every-600-websites-has-git-exposed/](http://www.jamiembrown.com/blog/one-in-every-600-websites-has-git-exposed/)

	
  * 作者（author）：[https://twitter.com/jamiembrown](https://twitter.com/jamiembrown)





* * *



[![git pull 不是简单的操作](http://www.labazhou.net/wp-content/uploads/2015/08/git-pull.jpg)](http://www.labazhou.net/wp-content/uploads/2015/08/git-pull.jpg)

对于 web 开发人员而言，对外暴露你的 .git 文件夹，属于低级错误。因为任何人都可以下载你的整个源代码库，后者常包括数据库密码、salt、hash 和第三方 API key、或用户名和密码。

在过去几年，我在另一个个人项目里，建立了一个数据库，收录了 150 万个还算有影响力的域名。一些是权威网站（比如 BBC、卫报、或政府、教育、军方的域名），另一些是拥有外部链接的域名，这些链接至少来自那些种类的某一种。

在 150 万网站当中，2402 个网站暴露了它们的 .git 文件夹、且可下载。600 个知名网站中就有 1 个、或互联网上 0.16% 的网站，危险地暴露了 .git 文件夹。

对于这些 .git 代码库，有些是无害的，但是根据随机取样，有很多包含了危险信息，它们为攻击网站提供了直接参考。数百个 .git 文件夹列出了数据库密码、或包含了面向服务的 API key，比如 Amazon AWS、或 Google Cloud。另一些包含了指向它们自己网站的 FTP 详情。很多还包含了以 .sql 文件存储的数据库备份，或隐藏文件夹的内容，它们本应该做访问限制的。

一个著名的人权团体暴露了曾注册过同性恋运动的、每个人的信息（包括他们的家庭住址和 email 地址），它们以 csv 文件的格式存储在他们的 git 代码库里，可从网站任意下载。一家销售数字报告的公司，向下载他们 .git 文件夹的任何人，免费提供其报告的整套数据库。

因此，请开发人员务必检查一下，确保你的 .git 文件夹无法在网站访问到，形如 http://www.yourdomain.com/.git/ 。如果能访问，请立即锁定。理想的做法，是删除这个文件夹，找一个更好的方式来部署代码、至少通过使用 .htaccess 以禁止访问。然后假设有人已经下载过了所有东西，搞清楚他们可能看到了什么。密码、salt、hash 或 API key 需要修改吗？他们应该访问了哪些数据？他们可能做了什么操作，变更或损害了你的服务？

还有，请向其他开发人员传播这件事------因为此时此刻，[这必定成为了互联网上最大的漏洞之一](http://www.labazhou.net/2015/01/why-do-we-still-write-insecure-software/)。



* * *



**相关阅读**



	
  * 《[robots.txt 探索笔记](http://www.labazhou.net/2015/05/what-one-may-find-in-robots-txt/)》

	
  * 《[漫谈配置](http://www.labazhou.net/2015/03/devops-the-problem-with-configurations/)》


