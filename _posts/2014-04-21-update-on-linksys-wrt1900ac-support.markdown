---
author: viviworld
comments: true
date: 2014-04-21 00:12:21+00:00
layout: post
link: http://www.labazhou.net/2014/04/update-on-linksys-wrt1900ac-support/
slug: update-on-linksys-wrt1900ac-support
title: 关于Linksys WRT1900AC支持的更新
wordpress_id: 590
categories:
- 软件
tags:
- Linksys
- Marvell
- OpenWrt
- 开源
---

由于Linksys官方发布中提及了关于Linksys对OpenWrt支持 引起了误解，我们想澄清OpenWrt对WRT1900AC的支持情况，以及正在进行的与Linksys的合作。

OpenWrt团队成员与Linksys的联系有一段时间了，讨论了OpenWrt对设备支持的合作。早在四月份，工程师Belkin提交了一些不完整的补丁，之前没有关于设备支持的技术合作。这些补丁目前被清除了，因为它们不能满足我们的质量标准。

最重要的地方仍然是缺乏一个Marvell 802.11ac无线芯片组的可用驱动。Belkin正致力于修复这个问题，但是他们没有给我们 这种驱动何时提供 的评估。

这种设备的默认固件好像在用Marvell提供的一个带有专利的驱动，根据配置它使用了非标准API。我们不知道Marvell将来是否开源这个驱动，或开发一个可替代的Linux驱动。我们相信这两种方法都需要大量的努力和时间。

鉴于此，我们目前推荐先不要购买这种设备，直到我们让软件的缺失部分对OpenWrt正常工作。

Linksys官方发布声明认为，这种设备是“OpenWrt准备好了”和“开源准备好了”。由于仍然差太多，甚至这种设备的GPL代码都没有提交到Linksys GPL代码中心，我们认为这些声明有些早了，以及不幸地起着误导作用。

Regards,
The OpenWrt Team

原文地址：[https://forum.openwrt.org/viewtopic.php?pid=230686#p230686](https://forum.openwrt.org/viewtopic.php?pid=230686#p230686)
