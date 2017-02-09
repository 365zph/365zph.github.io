---
author: viviworld
comments: true
date: 2014-10-22 00:22:30+00:00
layout: post
link: http://www.labazhou.net/2014/10/programming-by-voice-staying-productive-without-harming-yourself/
slug: programming-by-voice-staying-productive-without-harming-yourself
title: 用语音编程：不用伤害自己就可保持效率
wordpress_id: 1140
categories:
- 编程
- 软件
tags:
- Dragon NaturallySpeaking
- github
- Vimium
- Yeti
---

我喜爱在ExtraHop工作的原因之一就是会议少、大块大块的连续开发时间。然而，我很快发现，我不习惯长时间敲代码了。我在ExtraHop工作数周后，我的手腕和胳膊不太舒服。这些地方在过去是断断续续的不舒服，但是放在以前，限制晚上在家使用电脑足以解决这个问题。不过，这一次不同了。

[![400x283xTony-ExtraHop](http://www.labazhou.net/wp-content/uploads/2014/10/400x283xTony-ExtraHop.jpg)](http://www.labazhou.net/wp-content/uploads/2014/10/400x283xTony-ExtraHop.jpg)
#Tony Grosinger是ExtraHop网络公司的框架工程师。

做为一个刚刚毕业的大学生，我担心每天的工作活动会引起永久性损伤。我开始研究人类工程学键盘和鼠标，期望找到万全的解决方式。正如你猜测的，我没有找到有魔力的方法，我的状态每况愈下。

这种不适让我沮丧，我更加担心，这种伤害将妨碍我在工作和生活上的快速、轻松创造和交流。


### 介绍一种方法


在尝试、摒弃了一些其它方法之后，ExtraHop的一个同事向我展示了[Tavis Rudd的视频](http://www.youtube.com/watch?v=8SkdfdXWYaI)，Rudd用其声音编程。起初，我怀疑这种方法的可靠性和效率。不过，看了视频之后，我坚信声音输入对于程序员来说是一种并行的选择。Rudd患有类似的病症，他已经搜寻了我刚做的所有类似调查，最终认为，再好的键盘也不足以解决这种痛苦。

那天晚上，我在网上查找那些通过声音编程的人，想找到提示和教程。这些人少之又少，很多人断言这是不现实的。我没有那么容易放弃掉，开始鼓捣一个工具包，它支持在Linux机器上通过声音编程。


### 配置：最难的部分


很快就搞清楚了，Dragon NaturallySpeaking是听写软件中的唯一选择。他们的产品在语言识别上领先其他人很多，但是他只能运行在Windows或Mac上。不幸的是，我在Wine【注1】上从来没有成功运行过Dragon NaturallySpeaking，我不得不在Windows虚拟机上，设置代理到Linux主机的命令。

我在本文将略去一些配置步骤，你可以在我的[Github repo](https://github.com/tgrosinger/aenea-grammars)找到如何搞定一切的详细指令。

如果你按照那些指令做了，你现在应该能够发送口授和示例命令到你的Linux主机了，不过离编程不远了。我在接下来的两周里编写语法，大部分过程是这样的：



	
  * 期望执行一个任务（编程、切换窗口等）。

	
  * 编写让我通过声音实现这个任务的命令。

	
  * 测试命令，增加相关的命令。

	
  * 重复。


这个过程进展缓慢，我希望，链接的仓库帮你避免从头开始。甚至在用了大概一个月以后，我每天仍然数次调整命令。Tavis Rudd宣称有2000多个自定义命令，这意味着我必须还有很多工作要做。


### 结果


如Rudd在讲话中解释的一样，麦克风是安装中的关键点。只能听到你的、好的麦克风将在识别的精度和速度上产生巨大的不同。我非常喜欢正在使用的[Blue Yeti](http://www.bluemic.com/yeti/)，但是我只有在办公室绝对安静的前提下才能使用它。

根据目前我建立的命令，我可以在窗口切换，导航web（借助[Vimium](https://chrome.google.com/webstore/detail/vimium/dbepggeogbaibhgnhhndojpepiihcmeb?hl=en)【注2】），在工作区切换，还有最重要的，我可以用合理的速度进行Python和Go的编程。这没有使用键盘编程快，不过一旦你掌握了这些命令，它还是有着惊人的效率。

我在上面提到的Github仓库分享的语法是针对我所需的工作流。我推荐你把它们作为起点，但要注意计算机可能识别你的词语与我的不一样。这些语法也是我经常用到的、针对特定语言的。请不要犹豫写下你喜爱的语言。最后，在[dotfiles仓库里的.vimrc文件](https://github.com/tgrosinger/dotfiles/blob/master/.vimrc)，可以找到声音命令触发器的自定义快捷方式。

用声音编程还不完美，不过它已经达到了可作为实际选项的地步。不要继续忍受手腕和胳膊的不适了，因为现在有了替代方法。欢迎给我发送pull request，我们可以继续让声音编程变得更好。



	
  * 原文地址：[http://www.extrahop.com/post/blog/programming-by-voice-staying-productive-without-harming-yourself/](http://www.extrahop.com/post/blog/programming-by-voice-staying-productive-without-harming-yourself/)

	
  * 注1：Wine计划是在1993年由Bob Amstadt及Eric Youngdale发起的，最初的目的是为了让16位的Windows 3.1程序可以在Linux上运行，但随着电脑和时代的演进，Wine也一路支持到目前的Windows 8和64位的电脑架构。[http://zh.wikipedia.org/wiki/Wine](http://zh.wikipedia.org/wiki/Wine)

	
  * 注2：像个 Geek 一样去浏览。[http://www.appinn.com/vimium/](http://www.appinn.com/vimium/)


