---
author: viviworld
comments: true
date: 2014-03-26 15:03:52+00:00
layout: post
link: http://www.labazhou.net/2014/03/why-source-code-is-a-must/
slug: why-source-code-is-a-must
title: 为什么带有源代码的框架是绝对必要的
wordpress_id: 460
categories:
- 编程
tags:
- .net
- ASP.NET
- bug
- GPUImage
- Juce
- Oracle
- Ruby on Rails
- Spring
- SSToolKit
- 源代码
---

我的App都依赖第三方框架和类库。如果你在iOS市场，你可能使用[SSToolKit](http://sstoolk.it/)或[GPUImage](https://github.com/BradLarson/GPUImage)框架。如果你是一名web开发者，你或许使用优秀的[Spring](http://spring.io/)、[ASP.NET](http://www.asp.net/)或[Ruby on Rails](http://rubyonrails.org/)。不要忘了，Java和.NET运行时每天为数亿行代码提供动力。

软件是有bug的。如果你自己的app好像没有，它事实上是有的。即使你有着大量的单元测试、项目中不错的代码覆盖率以及非常少的技术债务，你使用的框架或许不是这样子的。有调查显示[60%的开发组](http://zeroturnaround.com/rebellabs/early-survey-results-app-releases-often-contain-critical-bugs/)在产品发布之后通常能够找到致命问题。

这个图表显示了Apache基金会代码库的测试覆盖率。红色代表低或没有覆盖。绿色代表覆盖。越大的区块代表越大的项目。

[![Apache基金会代码库的测试覆盖率](http://www.labazhou.net/wp-content/uploads/2014/03/apache-coverage-1024x574.png)](http://www.labazhou.net/wp-content/uploads/2014/03/apache-coverage.png)

大多数开发者甚至不想修复他们遇到的编译警告。在我的Mac OS机器上build稳定版Ruby 2.1.1时，就有一些编译器产生的警告。

    
    bignum.c:222:18: warning: unused variable 'maxpow16_exp'
    bignum.c:226:23: warning: unused variable 'maxpow16_num'
    bignum.c:239:18: warning: unused variable 'maxpow32_exp'
    ....
    complex.c:79:1: warning: unused function 'f_cmp'
    complex.c:109:1: warning: unused function 'f_lt_p'
    complex.c:116:1: warning: unused function 'f_mod'
    ....
    numeric.c:1461:10: warning: 'finite' is deprecated
    ....
    range.c:35:1: warning: unused function 'SET_EXCL'
    ....
    rational.c:478:1: warning: unused function 'f_rational_new_bang2'
    rational.c:583:1: warning: unused function 'f_rational_new1'


这些警告仅仅意味着存在大量未使用的方法，而不是真正的bug。这些警告的问题，开发者对此司空见惯了。他们了解它们，他们每天看到这些警告。我真的怀疑当一个新的警告出现的时候，是否会有人注意到。如果你已经有了超过20个的警告，这就很难注意到了。由于每天看着它们，你学会了无视。直到有一天你不能看到编译器日志里的任何警告。

但是他们为什么不移除这些未使用的变量或函数？


#### 你仍然确信，你的类库来自于很少看到致命问题的40%的那一部分？




### 如果你找到一个bug，该做什么


去报告。如果你刚好能够描述错误，你就是幸运的，那足以理解和重现问题。有一些明显的bug，你能够单独一行来描述。例如，当开发者在函数代码里看到 "[memset allways set '0' instead of value passed by the caller](https://code.google.com/p/android-source-browsing/source/detail?spec=svn.platform--bootable--bootloader--legacy.734756ca3968b54e32acab867a05b10fc5e13d07&r=734756ca3968b54e32acab867a05b10fc5e13d07&repo=platform--bootable--bootloader--legacy)"时，这个Android OS下的问题是显而易见的。

不幸的是，不是所有的问题都是那样明显。经常地，你不能马上理解是什么引起了问题。在引起错误的原因显现之前，你开始调试。现在第三方类库的源代码就能够帮到你了。你能够在类库本身内部检查方法调用。有时候你不正确地使用类库，你通过观察类库方法怎样被调用和行为表现就能理解它。你能够注意到出错的地方。

如果bug不在你的源代码里，你能够理解类库的代码是如何工作的，并希望找到一个变通方案。能够立即解决这个问题的、你的代码的变化。

你应当做一个简单的项目来重现问题，并把问题发送给类库作者。

然后令人感兴趣的事情发生了。


### 为你的问题得到一个修复


大多数小的商业（非免费）类库供应商修复问题速度较快。

[Juce](http://juce.com/)是由Julian Storer独自一人开发的、跨平台工具集。它是一个开源框架，他提供了一个商业许可。我实在感激他如此迅速地调查问题。

一些较大的供应商有低bug政策。[DevExpress](http://devexpress.com/)的家伙们的目标是不超过500个活动的致命bug。他们的员工告诉我，他们在修复问题上非常关注。他们在项目组采取了“零bug”政策。当你早晨来上班，你应当做的第一件事就是修复一个问题。如果旧功能出错了，你不能开始写新功能。

不幸的是，并不是每个问题都能得以解决。例如，MySQL有一个致命的、至今没有解决的、[日期标注为2006年的问题](http://bugs.mysql.com/bug.php?id=20786)。形势是如此地疯狂，以致于人们会庆祝bug的生日来引起人们对这个持续时间长的问题的关注。

[http://www.youtube.com/watch?v=oAiVsbXVP6k](http://www.youtube.com/watch?v=oAiVsbXVP6k)（译者注：这里有个视频介绍）

平台供应商不会太好。Oracle JDK截止到2014-3-22还有[9955个活动bug](https://bugs.openjdk.java.net/issues/?jql=project%20in%20(CODETOOLS%2C%20JDK)%20AND%20issuetype%20%3D%20Bug%20AND%20status%20in%20(Reopened%2C%20Open%2C%20%22In%20Progress%22%2C%20New)%20ORDER%20BY%20priority%20DESC)。.NET框架有[1161个活动bug](https://connect.microsoft.com/VisualStudio/SearchResults.aspx?KeywordSearchIn=2&SearchQuery=.net&FeedbackType=0&Status=1&Scope=0&Validation=True&Validations=1&SortOrder=5&TabView=0)。Android OS有[16068个打开的问题](https://code.google.com/p/android/issues/list?can=2&q=label%3AType-Defect)。苹果不允许浏览她们的bug清单，但是我怀疑她们会好些。

我在Oracle、Microsoft、DevExpress、Xamarin、Juce和一些类库供应商提交bug。坦白讲，你的bug将被快速解决的机会是非常低的。


### 如果bug没有被修复，该做什么


如果有变通方案，你能够绕过问题并完成你的任务，当然好了。你用不同的方式写你的代码，让你“跳过”问题，然后你做好了。那是问题的最幸运解决方法。

不幸的是，我不是一直都幸运的。当我在[Visual Watermark](http://www.visualwatermark.com/)工作的时候，我发现JDK试着呈现一些字体时会崩溃。它是在原生文本布局引擎某处的一个非法访问。JDK代码试图调用一个NULL对象的方法。

我在1.5年前向Oracle提交了这个问题。我没有期望它被快速解决，事实证明我自己修复才是正道。


#### 你应当能够重新build你在用的类库，否则就无视它


如果类库源代码是可以得到的，这就解决了两个问题。

第一，源代码对你调试问题有帮助。你能够逐步进入和跳出方法。监视变量和理解你使用的类库内部究竟发生了什么。

第二，它允许你快速build和使用类库修复后的版本。你不能对你的客户说“这个问题不能被修复是因为有个坏家伙”。你有失去他的高风险以及你能够从他身上获取的未来支付。


#### 有源代码不代表“开源”


很多框架供应商销售包含源代码的类库。例如，DevExpress提供了包含源代码的[完成认购](https://www.devexpress.com/Subscriptions/)。便宜的套餐没有源代码。我推荐你选择最高认购，因为价格差异并不能弥补源代码的缺失。单独一个问题带来的成本要比你节约的大。

然而，不是每个人都想公开源代码，甚至损害他们客户的需求。像[LeadTools](http://www.leadtools.com/)这样的供应商对你的每一次安装都要收费，但是仍然把你扔在不能自己修复问题的处境里。如果有其它选择的话，我宁可无视这些提议。

掌控你的app。使用带有源代码的类库。

原文地址：[http://nikitin.io/why-source-code-is-a-must/](http://nikitin.io/why-source-code-is-a-must/)
