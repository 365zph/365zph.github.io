---
author: viviworld
comments: true
date: 2015-06-16 01:20:13+00:00
excerpt: 我经常把这个规则应用到潜在地可被挪入配置文件的所有设置上，这有助于使得它们小而可维护。即使我偶尔需要修改某些配置，直接在源代码里修改，已经足够应付大部分情况了。不要把「让硬编码成为你的默认选择」同「让硬编码成为你的唯一选择」混为一谈。
layout: post
link: http://www.labazhou.net/2015/06/make-hard-coding-your-default-choice/
slug: make-hard-coding-your-default-choice
title: 让硬编码成为你的默认选择
wordpress_id: 2173
categories:
- 编程
tags:
- api
- NLog
- 反面模式
- 硬编码
- 配置
---


	
  * 原文地址（original source）：[http://enterprisecraftsmanship.com/2015/06/08/make-hard-coding-your-default-choice/](http://enterprisecraftsmanship.com/2015/06/08/make-hard-coding-your-default-choice/)

	
  * 作者（author）：[https://twitter.com/vkhorikov](https://twitter.com/vkhorikov)





* * *



硬编码【注1】经常被认为反面模式【注2】。把随着时间而变化的这些值，硬编码到源代码里，每当这些值真正变化时，都需要重新编译。

然而这个陈述也是正确的，我觉得，当开发一个应用程序时，硬编码应该成为默认选择。


### 硬编码 VS 配置文件


当你忙于一个项目或功能时，总是有一些魔法数字或字符串，它们潜在地会在将来变化。第一个冲动就是让这些变化可配置，今后你就能轻松修改它们。

对于大多数情况，这种决定使得接下来的维护复杂化。我们这里所面对的，是一个经典的困境「简单 VS 敏捷」。随着应用程序的增大，修改它的某些参数变得更加容易，因为它们被提取到配置文件里，但同时总体维护负担增加了。

在极端情况下，你或许最终得到了数十个、甚至数百个可配置的参数，这使得维护应用程序变得极度痛苦。这种情形被叫做[配置地狱](http://www.labazhou.net/2015/03/devops-the-problem-with-configurations/)（configuration hell）。

就和其它很多软件设计决定一样，我们需要求助于 YAGNI【注3】原则。所有这些参数真的需要马上可配置吗？或者，我们只是为了提前安排好？如果属于后者的情况，当这个需要变得明显之前，我们最好砍掉配置文件，以保持其小巧。

**如果该必要性没有被证明，那么硬编码就应该是默认选择**。对于硬编码，我的意思不是说，你应该把魔法数字和字符串扩散到你的项目源代码里。它们仍然需要收集并被放在一个地方做为常量。然而，这意味着你应该将它们从配置文件移除。


### 日志的例子


让我们举些例子，看看我们在实践中该怎样应用上面提到的原则。

我喜爱的日志资源库是 [NLog](https://github.com/nlog/nlog/wiki)。它有着相当丰富的功能，每一项都可轻松配置。

下面是一个典型的 NLog 安装的配置文件：

    
    <nlog>
      <variable name=“logFile“ value=“C:\logs\log-${shortdate}.txt“/>
     
      <targets>
        <target name=“trace“ xsi:type=“AsyncWrapper“ queueLimit=“5000“ overflowAction=“Block“>
          <target name=“file“ xsi:type=“File“ encoding=“utf-8“
                  layout=“Date: ${longdate}\r\n Level: ${level}\r\n Message: ${message}\r\n“
                  fileName=“${logFile}.txt“
                  archiveFileName=“${logFile}.{#####}.txt“
                  archiveAboveSize=“2097152“
                  maxArchiveFiles=“200“
                  archiveNumbering=“Sequence“/>
        </target>
      </targets>
     
      <rules>
        <logger name=“*“ minlevel=“Warn“ writeTo=“trace“/>
      </rules>
    </nlog>


尽管设置本身相当合理，我还是想提出一个疑问：把所有这些设置放在配置文件里，真的有必要吗？我们将要修改它们吗？在大多数情况下，答案是不。即使你对此感到怀疑，根据 YAGNI 原则，那也意味着「不」。

幸运的是，NLog 允许我们使用其配置的 API，以在代码里做配置。因此，除了依赖于配置文件，我们能够轻松地将这些设置挪到源代码里。我们仔细看下这个例子，看看我们可以除掉哪些设置。

首先，在 `targets` 部分，你可以看到我们为真正的 `target` 使用了 async wrapper。我们真的想让它可配置吗？不，这种设置很少需要修改。好的，其它的 `target` 呢？它设置了很多有用的属性，比如日志的 `layout`、`file name`、`maximum log file size` 等等。我们真的需要这种「不用重新配置就可修改」的机会吗？很可能，不需要。

`rules` 部分呢？这部分并不像 `targets` 部分那样明显。为了触发规则而修改 最小日志等级（`minlevel`）的可能性貌似可以理解，因为我们或许因为调试的原因想在运行中修改它。然而，问题在于实践中我们从来不会这样做。因此，我们最好也移除这个设置。

好了，我们最终还剩下什么？仅有一个设置留下了，它就是日志文件本身的路径：

    
    <appSettings>
      <add key=“LogFilePath“ value=“C:\logs\log-${shortdate}.txt“ />
    </appSettings>


现在，所有其它设置被放在了源代码里：

    
    string layout = “Date: ${longdate}\r\n“ +
        “Level: ${level}\r\n“ +
        “Message: ${message}\r\n“;
     
    var config = new LoggingConfiguration();
     
    var target = new FileTarget { FileName = fileName, Layout = layout /* Other params */ };
    var asyncWrapper = new AsyncTargetWrapper(target)
    {
        QueueLimit = 5000,
        OverflowAction = AsyncTargetWrapperOverflowAction.Block
    };
    var rule = new LoggingRule(“*”, LogLevel.Error, asyncWrapper);
    config.AddTarget(“asyncWrapper”, asyncWrapper);
    config.LoggingRules.Add(rule);
     
    LogManager.Configuration = config;


你可以看到，我们移除了整个 `nlog` 部分，并把保留的设置挪入了 `appSettings` 部分。现在它变成了我们配置文件的普通一员。

唯一的设置就是，根据被应用的环境，真的需要具有不同的值。我们这里做的工作，就是减少表面配置，从而使得解决方案更加可维护，代价是少了一些灵活。我坚信这是不错的折衷方案。

随后，我们或许发现我们自己经常修改某项硬编码设置。这就发出了信号，我们找到了将其挪入配置文件的正当理由。但截至目前，就让硬编码成为你的默认选择吧。


### 总结


我经常把这个规则应用到潜在地可被挪入配置文件的所有设置上，这有助于使得它们小而可维护。还有，我注意到，即使我偶尔需要修改某些配置，直接在源代码里修改，已经足够应付大部分情况了。


### [Update]


我需要指出，本文的内容仅适用于内部用的软件（in-house software）【注4】。第三方资源库开发是[不同的故事](http://enterprisecraftsmanship.com/2015/02/08/shared-library-vs-enterprise-development/)。

还有，我真的感激我在本文得到的所有反馈，想不到会引发如此多的讨论。但是，不要把本文的主旨------「让硬编码成为你的默认选择」------同「让硬编码成为你的唯一选择」混为一谈。如果你真的需要从代码里提取某些值、使其可配置，你最好就这样做。我向你提倡的唯一一点就是自问一下，这种提取是否真的有必要。



* * *






	
  * 注1：硬编码（英语：Hard Code或Hard Coding）指的是在软件实现上，把输出或输入的相关参数（例如：路径、输出的形式或格式）直接以常量的方式书写在源代码中，而非在运行时期由外界指定的设置、资源、数据或格式做出适当回应。一般被认定是种反模式或不完美的实现，因为软件受到输入数据或输出的格式改变就必需修改源代码，对客户而言，改变源代码之外的小设置也许还比较容易。[https://zh.wikipedia.org/wiki/%E5%AF%AB%E6%AD%BB](https://zh.wikipedia.org/wiki/%E5%AF%AB%E6%AD%BB)

	
  * 注2：在软件工程中，一个反面模式（anti-pattern或antipattern）指的是在实践中明显出现但又低效或是有待优化的设计模式，是用来解决问题的带有共同性的不良方法。它们已经经过研究并分类，以防止日后重蹈覆辙，并能在研发尚未投产的系统时辨认出来。[https://zh.wikipedia.org/wiki/%E5%8F%8D%E9%9D%A2%E6%A8%A1%E5%BC%8F](https://zh.wikipedia.org/wiki/%E5%8F%8D%E9%9D%A2%E6%A8%A1%E5%BC%8F)

	
  * 注3："You aren't gonna need it" (acronym: YAGNI) is a principle of extreme programming (XP) that states a programmer should not add functionality until deemed necessary. [https://en.wikipedia.org/wiki/You_aren't_gonna_need_it](https://en.wikipedia.org/wiki/You_aren't_gonna_need_it)

	
  * 注4：In-house software is a software that is produced by a corporate entity for purpose of using it within the organization. [https://en.wikipedia.org/wiki/In-house_software](https://en.wikipedia.org/wiki/In-house_software) 另外，在阮一峰的《Joel Spolsky在耶鲁大学的演讲》一文里，有更为风趣的介绍：[http://www.ruanyifeng.com/blog/2007/12/joel_spolsky_talk_at_yale_part_i.html](http://www.ruanyifeng.com/blog/2007/12/joel_spolsky_talk_at_yale_part_i.html)


