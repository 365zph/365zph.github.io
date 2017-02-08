---
author: viviworld
comments: true
date: 2014-01-23 09:51:05+00:00
layout: post
link: http://www.labazhou.net/2014/01/how-i-hacked-kayak-and-booked-a-cheaper-flight/
slug: how-i-hacked-kayak-and-booked-a-cheaper-flight
title: 教你hack Kayak网站定便宜机票
wordpress_id: 222
categories:
- 软件
tags:
- BTGuard
- Incognito
- vpn
---

首先声明我没有采用黑帽黑客的“[hack](http://en.wikipedia.org/wiki/Hackers_(film))”方式，而是找到了一个低效率的行情然后为我所用。那一天我必须是个商人，也没有伤害到本文提到的任何电脑或系统。


### 长话短说【注1】，我使用VPN在Kayak【注2】定了一张机票，节省100美元。


长背景：我在寻找飞往新奥尔良的航班，这时候我意识到昨天我看到的票价应该便宜100美元的。我开始琢磨为什么一天内价格浮动这么多，并试着只用Google Incognito来查票价，但是没有打折。难道和我的VPN或其他东西有关？那晚我用VPN（顺便说下，我用BTGuard），Kayak就认为我来自于加拿大的多伦多。我猜测如果你不在要离开的城市时，航班会便宜些？


### 我做了什么？


原来我今天去Kayak查阅从迈阿密飞往新奥尔良的航班，我没有用[VPN](http://en.wikipedia.org/wiki/Virtual_private_network)，而是用Google的Incognito模式。看看航班的价格：

[![kayak_us_1](http://www.labazhou.net/wp-content/uploads/2014/01/kayak_us_1-1024x610.png)](http://www.labazhou.net/wp-content/uploads/2014/01/kayak_us_1.png)

此时我的IP显示我来自：

[![us_ip_2](http://www.labazhou.net/wp-content/uploads/2014/01/us_ip_2.png)](http://www.labazhou.net/wp-content/uploads/2014/01/us_ip_2.png)

由于那晚我看到的机票价格是便宜了100美元的，我觉得这有些奇怪。我认为那时候我登入了VPN，它或许与此有关（顺便说一句，我是用VPN来屏蔽我的流量……对不起，NSA）。因此我试着登入VPN，重新对比一下。

下面是我登入VPN的截图：

[![vpn_3](http://www.labazhou.net/wp-content/uploads/2014/01/vpn_3.png)](http://www.labazhou.net/wp-content/uploads/2014/01/vpn_3.png)

下面是我的IP显示的位置：

[![canadian-ip4](http://www.labazhou.net/wp-content/uploads/2014/01/canadian-ip4.png)](http://www.labazhou.net/wp-content/uploads/2014/01/canadian-ip4.png)

我再次访问Kayak，显示我来自于加拿大，截图如下：

[![kayak_canadza5](http://www.labazhou.net/wp-content/uploads/2014/01/kayak_canadza5-1024x535.png)](http://www.labazhou.net/wp-content/uploads/2014/01/kayak_canadza5.png)

大概有70美元左右的价格差异（我不认为这里面包含了税）！我最初看到的345美元的航班没有了……现在有了100美元的差价。当我定票时，需要支付的总额单位是欧元！问题是，它不是380欧元，而是207欧元！兑换成美元有280USD。

[![eurusd6](http://www.labazhou.net/wp-content/uploads/2014/01/eurusd6.png)](http://www.labazhou.net/wp-content/uploads/2014/01/eurusd6.png)

能带来什么启发呢？尽量通过VPN订票，或许你能够节约不少钱……即使你需要用欧元支付。

PS：我查了在线银行记录，我总共支付了281.60美元！

PSS：这个航班在不用VPN，通过Kayak + Google Incognito时，价格超过了400美元。

原文地址：[http://www.josecasanova.com/blog/how-i-hacked-kayak-and-booked-a-cheaper-flight/](http://www.josecasanova.com/blog/how-i-hacked-kayak-and-booked-a-cheaper-flight/)
注1：TL;DR：[http://www.ifanr.com/204080](http://www.ifanr.com/204080)
注2：Kayak：指[http://www.kayak.com](http://www.kayak.com)，类似携程网
