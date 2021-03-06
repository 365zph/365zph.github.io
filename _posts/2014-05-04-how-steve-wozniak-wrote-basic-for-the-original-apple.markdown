---
author: viviworld
comments: true
date: 2014-05-04 14:47:57+00:00
layout: post
link: http://www.labazhou.net/2014/05/how-steve-wozniak-wrote-basic-for-the-original-apple/
slug: how-steve-wozniak-wrote-basic-for-the-original-apple
title: Steve Wozniak如何从零做起为早期苹果写BASIC的
wordpress_id: 629
categories:
- 编程
tags:
- apple
- basic
- Breakout
- FORTRAN
- RPN
- 乔布斯
- 比尔盖茨
---

[![steve-wozniak](http://www.labazhou.net/wp-content/uploads/2014/05/steve-wozniak.jpg)](http://www.labazhou.net/wp-content/uploads/2014/05/steve-wozniak.jpg)


<blockquote>为了[庆祝BASIC的50周年](http://bit.ly/1koOQMm)，Steve Wozniak【注0】写了一些回忆录，关于这门受欢迎语言的首次体验，以及他如何从零做起为苹果I和苹果II电脑创立自己的BASIC。一个难以置信的壮举！</blockquote>


在1967年或1968年，我是高中的一名毕业班学生，我们的电子学老师（我生活中很多教学名声中最好的老师）安排我到桑尼维尔（西尔韦尼亚）的一家公司给电脑编程，因为我已经全部掌握了学校的电子学课程。McCollum先生每年为具备电子学能力的学生做这样的事情，找到当地有工程师和项目的公司让高中生去积累一些经验。我在这台IBM电脑上学习用FORTRAN编程。

我最初体验BASIC是在高中的同一年。我们学校还没有电脑，除了GE，我猜的，引进了带有modem的终端来做他们的分时业务。我们很少的数学好的学生被给几页的指令，我们用BASIC写一些非常简单的程序。我觉得对于上手，这是一门非常简单、易于学习的语言，不过那个终端仅仅在我们学校放了几天。我们的数学班主任要求我写一页，说明为什么我认为拥有这个终端对于学校是一件好事。我的确写了一页，关于逻辑思考和解决问题的，但是学校没有跟进调查分时程序。

在我大学几年里，我的高级编程语言属于科学的类型，FORTRAN、PL-1、Algol。当然我也在大学以及自己独立的时候用很多汇编语言做了大量的编程。

在Homebrew电脑俱乐部，我们被成堆的书包围，我喜欢称之为‘圣经’。一本是Ted Nelson写的《电脑革命/梦幻机器》，描述了以书面形式链接到下一步事物的意义的未来世界。他的想法就像科幻小说，但是我们都知道它们是技术上可实现的，我们都提倡这种看待未来电脑的方式。另一本‘圣经’是一本书《BASIC的101个游戏》。我是一个电脑游戏粉丝，知道如果我有一台属于我自己的电脑，我会打算敲入所有这些游戏并玩一遍。根据我自己感觉的判断，我猜测这将是发起一场家用电脑革命的关键所在。我的非商人特点阻止我去讨论市场和财务。

我不确切知道一台真正的电脑需要做的、电脑为公司做的大量财务工作，电脑以高价卖给了公司。那些是值得花钱的电脑。我所知道的一切就近在咫尺。我模拟了HP的芯片设计和逻辑设计，以及工作在计算器上。我的电脑将不得不那样做。我的电脑也要不得不玩游戏。至少那时候我确定我的电脑可能能够做那些价格昂贵电脑做的重要事情，只是那时候我不敢肯定。

游戏的关键是BASIC。比尔盖茨那会儿在电子学爱好者的世界之外还不出名。我们俱乐部的每个人都知道他在为Intel微处理器写BASIC。我意识到，让我的电脑变得优秀（受欢迎）的关键是包含一个高级语言，它一定是BASIC。使用FORTRAN编程的工程师们不会是发起一场家用电脑革命的力量。


### 学习语言，写一个BASIC解释器


问题是我还不了解BASIC，只有来自于3天的高中经验，它有行号。因此某天深夜我找到HP上的一本BASIC手册，开始阅读，并就该语言的命令做了笔记。需要一提的是，我生命中从来上过一节编写编译器（或解释器）的课程。但是我的朋友Allen Baum送给我了关于这个主题的、MIT课本的影音拷贝，因此我可以声称我在MIT受过教育，哈哈。我在大学的第二年，我坐在数学分析课堂上，尽量教自己如何开始写一个FORTRAN编译器，却不知道编写编译器的技术。回到这个回忆里，我开始为我的6502微处理器写以行读取用户敲入的、用于分析和错误检查的字符的代码。

我了解语法图（Syntax Chart），就为这个BASIC建立了一份。我不知道HP BASIC与DEC BASIC是截然不同的，后者是《BASIC的101个游戏》书中用到的，是比尔盖茨编写的。我认为所有BASIC是相同的，但是HP的BASIC在遇到字符串时出现了极大的不同。我完成了我的语法图（Syntax diagrams ），它们是完整的。但是我脑子里想，如果我为6502创立第一个BASIC的话，我将成为一个明星，我能够在爱好者世界里有一点儿名气，就像比尔盖茨一样。为了节约一些时间，我跳过了浮点数字（带小数点的数字）只是为了节约数周时间，这样就更有机会成为在6502上开发出BASIC的第一人。你或许往回看，且看到了我在Apple II的ROM里包含了浮点运算程序，但是我从来没把它们放在BASIC里。当你手动编码（负担不起分时账目）时，在不得不位于固定位置的中间层结构做出修改是比较困难的。

[![breakout-on-integer-basic](http://www.labazhou.net/wp-content/uploads/2014/05/breakout-on-integer-basic.jpg)](http://www.labazhou.net/wp-content/uploads/2014/05/breakout-on-integer-basic.jpg)

我不知道编译器。但是我知道栈，以及用栈把表达式转化成RPN【注1】的东东。事实上，我们的HP计算器使用RPN。在考虑如何写这种语言时，我想到了我自己的技能、而不是书本中的东东。我用上了称之为名词和动词的栈（操作数和操作符）。我把标记放在我的语法图里，但是里面的每个操作符都有一个数字，对应到它在这个256字节或512字节表（我忘了）里。第41个操作数的操作符代码是#41。

我还有个针对每个操作符两种优先级的列表。一个是高于其它操作符的优先级。例如，+操作符将会引起*操作符首先发生。但是我需要第二张表，用于阻止处理像圆括号之类操作符的入栈操作。我不知道我是否在一个正确的栈上，但是它运行正常，做了我需要的事情。它不必从书中来。

我喜欢描述在Homebrew电脑俱乐部的这种BASIC。我从来没有看到我的名字被印出来，因此我没有得到‘比尔盖茨’的名声，但是我在俱乐部出名了。这甚至发生在Steve Jobs看到我的电脑出现之前。接下来的时间我只是不得不为那些数字操作符编写一个又一个的程序。每次俱乐部会议，我都多一些完全工作的命令。

在我的苹果II上，视频内存和电脑内存，同样的还有微处理器，每秒修改或许一百万（夸大了）个数字，将改变为每秒修改一百万屏幕上的字节。Atari arcade游戏那时候还是硬件，但是现在游戏能够做为软件实现了，使用6502机器语言编程。BASIC是一门解释型语言。在执行过程中，BASIC仔细查看每个语句的单个字符，再决定做什么。结果它可能比机器语言慢100或1000倍。但是有一天我产生了好奇，你是否能够只在BASIC里写个移动对象的程序，看看它们是否像真实动画那样移动。

我已经在硬件上为Atari设计了游戏《Breakout》【注2】。我想知道我是否能够用BASIC实现这个简单的有动画的街机游戏？我知道我能够用机器语言编写。既然这是我自己的BASIC，我找到语法图，加入命令来标示颜色、画水平和垂直的线条。随后我搜索芯片手册，选择在一个芯片上有4个定时器（555种定时器）的芯片。我使用一些软件来读取平台距离电位器的位置，根据你调节刻度位置来改变反弹的刻度。一旦我安装了这些机制（为新的BASIC附加东东烧了新的EPROMS），我坐下来写了一些简单的FOR循环，用不同的颜色标示砖块。我必须在几分钟内尝试30种颜色组合。然后我加了平台、分数和球。我能够调节程序参数来改变球的速度和角度。顺便地，我认为是时候增加1位（bit）声音的扬声器了，因为当球撞击到砖块上时，你需要听到声音，等等。

[![乔布斯和沃兹尼亚克](http://www.labazhou.net/wp-content/uploads/2014/05/jobs-and-Wozniak.jpg)](http://www.labazhou.net/wp-content/uploads/2014/05/jobs-and-Wozniak.jpg)

我把Steve Jobs喊到我的公寓看看我的成果。我向他演示了更改像砖块颜色之类的东西是多么地容易和迅速。最重要的是，在半小时里我尝试了这个游戏更多的变量，比我能在这个硬件过去10年里做的还要多。Steve和我都意识到这是多么地重要，因为动画游戏（街机模式）能够用软件实现了。更重要的是，用BASIC意味着任何年龄段的任何人都能够编写游戏。

我按顺序保存了大约50个关于我的所有BASIC设计工作的资料。每一个都标记为GAME BASIC。因此你能够看到我的领导是从哪里来的。

原文地址：[http://gizmodo.com/how-steve-wozniak-wrote-basic-for-the-original-apple-fr-1570573636](http://gizmodo.com/how-steve-wozniak-wrote-basic-for-the-original-apple-fr-1570573636)



	
  * 注0：斯蒂芬·盖瑞·沃兹尼亚克（Stephen Gary Wozniak），[http://zh.wikipedia.org/wiki/斯蒂夫·沃兹尼亚克](http://zh.wikipedia.org/wiki/斯蒂夫·沃兹尼亚克)

	
  * 注1：RPN，[http://zh.wikipedia.org/wiki/逆波兰表示法](http://zh.wikipedia.org/wiki/逆波兰表示法)

	
  * 注2：[http://zh.wikipedia.org/wiki/Breakout_(遊戲)](http://zh.wikipedia.org/wiki/Breakout_(遊戲))


