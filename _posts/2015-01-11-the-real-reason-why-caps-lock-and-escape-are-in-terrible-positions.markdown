---
author: viviworld
comments: true
date: 2015-01-11 12:34:34+00:00
layout: post
link: http://www.labazhou.net/2015/01/the-real-reason-why-caps-lock-and-escape-are-in-terrible-positions/
slug: the-real-reason-why-caps-lock-and-escape-are-in-terrible-positions
title: Caps Lock和Escape键位置不佳的真正原因
wordpress_id: 1510
categories:
- 杂项
- 网络
tags:
- linux
- Vim
- windows
- X窗口系统
- 键盘
---

原文地址（source）：[http://simplyian.com/2015/01/08/The-real-reason-why-Caps-Lock-and-Escape-are-in-terrible-positions/](http://simplyian.com/2015/01/08/The-real-reason-why-Caps-Lock-and-Escape-are-in-terrible-positions/)

Caps Lock键是完全没用的，这是一个公认的事实。我一年只用一到两次，因此绝对不能认为 它处于主导行（home row）上的小拇指旁边 是合理的。这个地方和Enter键一样方便，尽管完全没有用处。

相反地，Escape键非常有用。当我在YouTube上全屏观看视频、关闭Facebook上的聊天和在Vim里使用命令时，会用到它。然而，它使用频率非常高、位置却是最糟糕的：键盘的左上角。在很多笔记本上，它还很小。

[![chromebook键盘](http://www.labazhou.net/wp-content/uploads/2015/01/chromebook-keyboard.png)](http://www.labazhou.net/wp-content/uploads/2015/01/chromebook-keyboard.png)



[![mac上的Escape键](http://www.labazhou.net/wp-content/uploads/2015/01/escape-mac.png)](http://www.labazhou.net/wp-content/uploads/2015/01/escape-mac.png)

对于重度Escape键用户，这是效率的惊人福利。


### Caps Lock是怎样得到它的主导地位的


追溯到打字机时代，Shift键基本上用于切换打字机里的某些规则，让你打出另一套字符，通常是大写字母。“Shift Lock”键是个切换键，基本上保持[键盘](http://www.labazhou.net/2014/10/programming-by-voice-staying-productive-without-harming-yourself/)处于被切换的位置，它和如今大部分键盘上的Caps Lock键的位置相同。

[![打字机上的键](http://www.labazhou.net/wp-content/uploads/2015/01/typewriter.png)](http://www.labazhou.net/wp-content/uploads/2015/01/typewriter.png)

当计算机时代到来的时候，Caps Lock键被挪到了现在Control键的位置、Control键位于Caps Lock键的位置。然而，Control键对于以前的打字机员和大型机用户不太方便，Caps Lock键在IBM的、101键增强型键盘上被挪回了最初的位置。

[![101键的增强型键盘](http://www.labazhou.net/wp-content/uploads/2015/01/101key-ibm.png)](http://www.labazhou.net/wp-content/uploads/2015/01/101key-ibm.png)

101键增强型键盘很快成为键盘布局事实上的标准，这就是我们的键盘为什么有如今的Caps Lock位置的原因。[关于101键增强型键盘的更多信息可以在这里找到](http://www.pcguide.com/ref/kb/layout/stdEnh101-c.html)。


### Escape键的位置是怎样变成最糟糕的


同时，Escape键被放在了键盘较远的左上角，意味着可以尽可能多地当做功能键使用。它创建于60年代，允许程序员从一种代码切换到另一种代码。

然而，这对于普通用户是没有意义的，Windows操作系统开始使用这个键做为关闭对话框、大部分意味着“停止”。其它操作系统也跟着这样做，Escape键变成了退出、或以某种方式暂停程序的键。


### 为什么Vi使用Escape键切换模式


如果你是Vi或Vim用户，你可能使用Escape键多些。对于该程序的任何功能，它都是必需的，你可能发现自己每一分钟至少要敲它两次。然而这个位置不太明显，它的位置是如此地不爽。为什么不是Control键？或者Alt键呢？

Vi建立之初，Escape键还处于Tab键的位置，而Control键位于Caps Lock的位置：**ADM-3A**【注1】。

[![ADM-3A键盘](http://www.labazhou.net/wp-content/uploads/2015/01/adm-3a.png)](http://www.labazhou.net/wp-content/uploads/2015/01/adm-3a.png)

这个位置真是太方便了。你不必为了敲这个键而移动你的手，这个键比较大，和如今笔记本键盘上的小方块不一样。今天的键盘没有这样制造，真是太糟了。


### 解决方案？


在Chromebook上，你可以修改键盘设置，将“Search”按钮映射到Escape键。

最容易、低廉的解决方案就是交换Caps Lock和Escape键。在运行着X窗口系统【注2】的系统上，你可以将下面的代码放入 ~/.Xmodmap：

    
    ! Swap caps lock and escape
    remove Lock = Caps_Lock
    keysym Escape = Caps_Lock
    keysym Caps_Lock = Escape
    add Lock = Caps_Lock


关于实现这一点还有很多其它解决方案，但是重要的是，我当前是作为一名Linux用户。

然而，你仍然有标识不当的键。还有，这种修复在Windows上不起作用。

你可以买到一些键的位置不错的键盘，比如：[Happy Hacking Keyboard](http://www.amazon.com/gp/product/B000EXZ0VC/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=B000EXZ0VC&linkCode=as2&tag=colleged07a-20&linkId=NZT5S47X3O26UYYH)【注3】。然而，它们通常价格昂贵，因为需求少导致生产的数量非常有限。

Caps Lock和Escape键设计的时代里，我们还没有今天所拥有的大部分工具。它们是历史的遗迹，走过了计算机的历史。



	
  * 注1：The ADM-3A was one of the first computer terminals manufactured by Lear Siegler, first produced in 1975.[citation needed] It had a 12 inch screen displaying 12 or 24 lines of 80 characters. [http://en.wikipedia.org/wiki/ADM-3A](http://en.wikipedia.org/wiki/ADM-3A)

	
  * 注2：X窗口系统（X Window System，也常称为X11或X）是一种以位图方式显示的软件窗口系统。最初是1984年麻省理工学院的研究，之后变成UNIX、类UNIX、以及OpenVMS等操作系统所一致适用的标准化软件工具包及显示架构的运作协议。[http://zh.wikipedia.org/wiki/X_Window%E7%B3%BB%E7%B5%B1](http://zh.wikipedia.org/wiki/X_Window%E7%B3%BB%E7%B5%B1)

	
  * 注3：Happy Hacking Keyboard（缩写为HHKB）是由株式会社PFU（富士通的全资子公司）所经销的计算机键盘。本键盘由和田英一和PFU研究所共同开发，于1996年12月开始销售。[http://zh.wikipedia.org/wiki/Happy_Hacking_Keyboard](http://zh.wikipedia.org/wiki/Happy_Hacking_Keyboard)


