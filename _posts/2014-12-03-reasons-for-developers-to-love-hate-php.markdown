---
author: viviworld
comments: true
date: 2014-12-03 06:19:14+00:00
layout: post
link: http://www.labazhou.net/2014/12/reasons-for-developers-to-love-hate-php/
slug: reasons-for-developers-to-love-hate-php
title: 为什么开发者对PHP又爱又恨
wordpress_id: 1390
categories:
- 编程
tags:
- facebook
- HHVM
- Perl
- php
- WordPress
---

原文地址（source）：[http://www.infoworld.com/article/2852329/php/reasons-for-developers-to-love-hate-php.html](http://www.infoworld.com/article/2852329/php/reasons-for-developers-to-love-hate-php.html)

受人尊敬的服务器端脚本语言PHP，因在web开发中的应用而知名。首次[由Rasmus Lerdorf在1995年发布](http://www.infoworld.com/article/2609877/web-development/believe-the-hype--php-founder-backs-facebook-s-hiphop-technology.html)，受WordPress和[Facebook](http://www.infoworld.com/article/2841561/php/php-7-moves-full-speed-ahead.html)的影响而变化着，据[W3Techs报道](http://w3techs.com/technologies/details/pl-php/all/all)，82%网站的服务器端编程语言是PHP。这门语言在[编程语言受欢迎程度排名](http://www.infoworld.com/article/2845147/application-development/big-data-sparks-interest-in-statistical-programming-languages.html)上，稍微落后于Java，在竞争对手Tiobe排行榜降到第六名。做为高性能的升级版本PHP 7，预期在2015年发布。

然而，就像任何语言，它也有支持者和反对者。下面解释了支持者声援PHP、和持不同意见者痛批它的原因。


### 好的：流行、入门快


“PHP是目前最流行的web开发语言，”PHP工具提供商Zend Technologies公司【注1】CEO Andi Gutmans说。在New Media Campaings供职的开发者Josh Lockhart，也是一名作家，强调了PHP较小的学习曲线、易于部署和快速的开发迭代。Lockhart说，“PHP是最易理解的web开发语言之一，它被安装在大部分服务器上（包含大部分共享主机）。因为有优秀的在线文档和最新的在线资源，学习起来相对容易。”


### 好的：好找工作


“[PHP](http://www.labazhou.net/2014/03/the-new-php/)帮助你赚钱、找到一份在服务器端的工作”，Gutmans说。在上周的Dice.com技术工作网站上的快速研究，找到了3,366份PHP相关的工作。与17,418份Java工作相比显得很平淡，紧追Perl（4,300）和Python（5,429），但是高于Ruby（2,973），甚至包括Objective-C（985）。Lockhart把PHP看做使用频率最高的语言之一，尽管它和Ruby、Python、Go和Rust之类的语言比起来，有些保守。


### 好的：继续在发展


这门语言自诩有闭包和命名空间之类的现代功能，还有性能和现代框架。正如Gutmans所指出的，“一些想离开的人在PHP能提供什么上面所受到的必要教育不多。”Lockhart说，开发者正在意识到，PHP有着强大的现代特性以及合适的面向对象编程模型。即将到来的版本7，在应用程序上提供了巨大的性能提升。Lockhart指出，Facebook对PHP的增强，包含了[HHVM虚拟机](http://www.infoworld.com/article/2610966/development-tools/facebook-invents-a-php-virtual-machine.html)和[Hack语言](http://www.infoworld.com/article/2610932/open-source-software/facebook-s-hack-language-builds-on-php.html)【注2】。


### 坏的：抱怨设计、缺乏重心


博主Eevee在2012年反对这门语言的公开信《[PHP：不规则的糟糕设计](http://eev.ee/blog/2012/04/09/php-a-fractal-of-bad-design/)》中说道，“事实上PHP里的每个特性都多多少少是不规则的”。Eevee不仅仅给这门语言差评，而且包括框架和生态系统。根据该博主说的，这门语言不是可预期的、一致的，而是充满了让人诧异和不一致的地方。在批评中，PHP被称作不透明的，没有默认的堆栈跟踪，一直承受着复杂的、功能不佳的类型，“没有清晰的设计哲学。早期的PHP受到了Perl的激励；带有‘out’参数的庞大的stdlib来自于C；面向对象部分模仿着C++和Java设计。”

Lockhart承认，Eevee的反PHP言论有些“夸大了事实本质”。尽管是一名PHP支持者，Lockhart在被问及时，还是足够和蔼地列出了批判：



	
  * 这门语言是不一致的，特别是函数名称和参数顺序。“这很容易修正，因此这不是个大问题。”

	
  * PHP仍然有很多遗留包袱，像全局变量、魔术引用等等。“这些坏的实践正在缓慢地从语言中修剪，但是在它们消失之前，它们还会怂恿愚昧的开发者坚持不好的实践。”

	
  * PHP不像其它语言那样专注，Lockhart将其归咎于“受到委员会驱动的、长期都是一块一块的”。





* * *






	
  * 注1：Zend Technologies 公司是一家互联网基础架构软件公司。Zend Technologies最为人们熟知的是它的两个奠基人：Andi Gutmans和Zeev Suraski，他们与其他以色列程序员一起，发展了由Rasmus Lerdorf开创的PHP语言。[http://zh.wikipedia.org/wiki/Zend_Technologies](http://zh.wikipedia.org/wiki/Zend_Technologies)

	
  * 注2：Hack，一种开源脚本语言，运行在HHVM虚拟机上，主要开发者为Facebook。在2014年3月20日正式发布。在发布前，Facebook已经在它的网站上广泛使用及测试。[http://zh.wikipedia.org/wiki/Hack_(%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80)](http://zh.wikipedia.org/wiki/Hack_(%E7%A8%8B%E5%BC%8F%E8%AA%9E%E8%A8%80))


