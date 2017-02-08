---
author: viviworld
comments: true
date: 2015-03-02 08:26:19+00:00
layout: post
link: http://www.labazhou.net/2015/03/interviews-with-floss-developers-joey-hess/
slug: interviews-with-floss-developers-joey-hess
title: 自由/开源软件开发者Joey Hess的采访
wordpress_id: 1656
categories:
- 编程
tags:
- basic
- bug
- debian
- hacker
- Haskell
- Perl
- python
- 程序员
- 自由软件
---

原文地址（original source）：[https://zgrimshell.github.io/interviews-with-floss-developers-joey-hess/](https://zgrimshell.github.io/interviews-with-floss-developers-joey-hess/)

很难有一种更好的方式就自由/开源软件项目背后的开发者展开一些列的采访，他们有着难以置信的思维，比如Joey Hess。对于他在自由软件生态系统上的贡献，特别是Debian上的贡献，要用笔触来写的话，本身将是一部书。他的影响甚至超过了其项目------人们直接关注他的博客文章来留意他在做什么以及过得怎么样。一名来自小木屋的[hacker](http://www.labazhou.net/2014/03/a-short-history-of-hack/)。如果你真的需要对真正hacker有个印象，那么Joey就是代表。由于本文不是一部书，我将只提到他已经参与到背后的几个项目------git-annex、ikiwiki、etckeeper、debian installer、部分dpkg、debhelper、devscripts和taskel。就这么多吧。

[![Joey Hess, Debian](http://www.labazhou.net/wp-content/uploads/2015/03/joey-hess.jpg)](http://www.labazhou.net/wp-content/uploads/2015/03/joey-hess.jpg)

我：给大家打个招呼？

Joeyh：我是Joey，个人网站是 [https://joeyh.name/](https://joeyh.name/)

我：你是如何开始编程的？

Joeyh：Atari 130XE电脑，装有BASIC和一个无聊的字处理软件，就没有其它了。其他朋友都没有电脑，因此得到软件的唯一途径就是手动在demo程序里敲代码，然后开始修改并编写自己的软件。这就是容易的学习方法。在学校也有一些这种logo。

我：你能给其他想学习编程的人什么建议？

Joeyh：你给了我一道难题，这比我开始的时候去真正理解一些东西还要难，比没有太多可用的资料时还被激励学编程更难。或许装备有真正交互的、简单的Arduino【注1】裸机系统能够回答你。

我最近有提到我的侄子，他正在学习Python，“[Python the Hard Way](http://learnpythonthehardway.org/)"网站已经让他快速地掌握了很多东西。

我：说说你用来做开发的电脑配置？

Joeyh：卸载了间谍软件的Lenovo笔记本，Debian非稳定版、xmonad、xfce、vim。

我：你是如何看待Purism的（开源硬件笔记本发起项目，最近得到了CrowdSupply的投资）？

Joeyh：我对此了解不多，不过貌似消费层次的硬件质量不高，因此关闭了、且不值得信赖，需要搞清楚开发或者挑选开源的替代软件，做为一个社区，它们应该是能够满足我们需求的东东，并专注于此。一些项目正在尝试，我希望它们能够成功。

我：你如何看待Debian开发的未来？

Joeyh：嗯，我差不多不再担心它了。如果你回头看看我在过去2-3次的DebConfs会上的演讲，你就能找到关于它的最好的思考。

我：做为Debian开发者，你退休了。那么，你想过有一天重新回来，以及（或者）你计划去加入一些其它社区吗？

Joeyh：回归将是自豪的，不是吗？但是我想我不会的。毕竟，人不能两次踏进同一条河流。

相反，Debian可能将不得不容忍我这个让人讨厌的上游作者，我不会提交tar包，而是提交debian/directories，做为一名bug报告人员，我乐于享受报告有意思的bug，比如 [-0 NaN](http://bugs.debian.org/778800)。

自从我离开Debian后，我好像有更多的时间可以参与到其它在线社区了，不过是以更加扩散的方式。或许这只是本来的样子，参与到自由软件、但没有拥抱像Debian之类的大型软件。

我：关于Debian会议，都有哪些值得回忆的时刻？

Joeyh：太多了！在会场外面的波兰农贸市场的野餐，吃的是浆果和玉米粉蒸肉；在瑞士忙碌一天后的虹鳟鱼和篝火；在爱丁堡离奇夜晚的会场即兴修理管风琴；夜晚和Ian Murdock一起漫步在Porto Alegre，他对于即将从事的事业是多么地谦虚；在西班牙整夜地hack；在芬兰的午夜太阳和持续不断的派对下无法入眠；呆在亚特兰大的宾馆大堂里设计Build-Depends。

我：你玩游戏吗？Valve Steam免费提供给Debian开发者，你使用Steam玩Valve游戏吗？

Joey：我玩过Half Life和Portal，但是攻略已经占用了我太多时间。我通常喜欢时间短的独立游戏，或者能告诉我们一些新的游戏玩法的游戏，最近喜欢的游戏是 [A Dark Room](http://adarkroom.doublespeakgames.com/)。

不过我更喜欢有趣的、现实中的桌面游戏，和朋友一起玩，比如Carcassanne Discovery和Hive。

三月份，为了参与“[Seven Day Roguelike Challenge](http://7drl.org/)”，我将试着在一周内用Haskell编写一个rouguelike游戏【注2】，每天在博客写我的进展。

我：当前你是一名Haskell黑客（git-annex），你是如何评价这门语言的，它和Python、C、JavaScript、Ruby和Perl相比，你又作何评论？

Joeyh：不只是git-annex项目；我当前的所有项目都是用Haskell语言写的。

我认为，我们期望程序员在写代码时脑子里存多少东西，这是让人惊奇的。缓冲会溢出吗？修改全部变量的值将破坏代码的其它地方吗？输入已经被过滤了吗？接口改变了吗？Haskell马上解决了当中的一些问题，但更多的是，它让你开始注意到这种无处不在的问题，它提供了完全消除你代码中的一类问题的方法。

比如 [http://joeyh.name/blog/entry/making_propellor_safer_with_GADTs_and_type_families/](http://joeyh.name/blog/entry/making_propellor_safer_with_GADTs_and_type_families/)。我避免的这类bug从来没有影响过我的代码，但是阻止这类bug仍然是值得做的，因此我不必再担心它们了。

我：你建议把Haskell做为学习的首选语言吗，尤其是那些对于数学跃跃欲试的人？

Joeyh：我认为这个建议不错。或者它可以是另外的方式------在我年轻的时候，我就喜欢数学，但是数学把我淘汰了，这种方式在很多人身上都发生过，我想学习更多的关于高阶数学时，像Perl和C之类的语言不能提供太多帮助。我在Haskell里却能处处碰到一些。

我：相比于你使用Perl的时光，你是如何比较Haskell效率的？

Joehy：这很难比较；我现在是一个非常不同的程序员了。当我用Perl时，我很可能将更加迅速地发现了一些快速hack。但是，它们更像是保持快速hack。现在，或许我要花更长的时间才能达到这一步，但是代码好像更牢靠了，在扩展成更大的或不同程序上变得更有延展性。

还有，我对编写软件资源库感到非常疲惫了。

我：你能描述下你的生活哲学吗（你生活在森林里的小木屋，大量使用太阳能，包括我在内的很多人都很好奇，是什么在驱使着你向往这种生活，它又是如何影响着你的总体生活质量和幸福的。看看当今掠夺性的资本主义社会，你能够在一个月之内轻松赚取$10,000，貌似你是一名无政府主义者，且非常谦虚）？

Joeyh：我想开发一些或许可持续的、有价值的东东。这对于软件世界，难度是非常大的，因为很难过于超前考虑，也因为大部分工作没有强调这种真正价值。我非常幸运，能够找到一个点，在自由软件上投入这么多年的全部时间，我愿意为之放弃很多东西。

舍弃现代便利性，生活在小木屋里是非常棒的，因为这里安静，你可以尽可能多地思考；互联网随处都有，没有私密空间（或许有点儿慢）；当你用太多时间静静地思考时，你将需要根据季节去砍木柴、挑水、跳到河里去避暑。

（谦虚？和大多数程序员一样，我内心深处有着飘飘然的自负……）



	
  * 注1：Arduino，是一个开放源代码的单芯片微控制器，它使用了Atmel AVR单片机，采用了基于开放源代码的软硬件平台，建构于简易输出/输入（simple I/O）接口板，并且具有使用类似Java、C语言的Processing/Wiring开发环境。[http://zh.wikipedia.org/wiki/Arduino](http://zh.wikipedia.org/wiki/Arduino)

	
  * 注2：《Rogue》是迷宫探索式电子游戏，最早由迈克尔·托依和格伦·韦科曼在1980年左右开发。部分因为游戏内容的过程生成，游戏在1980年代中期大学Unix系统上很流行。《Rogue》使迷宫探索在电子游戏领域普及，其他开发者制作了诸多统称为“类rogue”（Roguelike）的派生作品。比如它直接给与了《Hack》灵感，此游戏之后又衍生出《NetHack》。类rouge还影响了其他类型的商业游戏，如《暗黑破坏神》。[http://zh.wikipedia.org/wiki/Rogue](http://zh.wikipedia.org/wiki/Rogue)


