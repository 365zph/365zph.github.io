---
author: viviworld
comments: true
date: 2015-12-04 14:06:59+00:00
excerpt: 我在喝醉以后的状态里，评论你的网站。我将寻找 bug、暗淡的用户体验风格、拙劣的文案，并从总体上评估你的网站
layout: post
link: http://www.labazhou.net/2015/12/the-user-has-sobered-up/
slug: the-user-has-sobered-up
title: The User 酒醒了
wordpress_id: 2851
categories:
- 杂项
- 职业
- 设计
tags:
- bug
- hacker news
- Trello
- 开源
- 想法
- 用户体验
---


	
  * 原文地址（original source）：[http://burntfen.com/2015-11-29/the-user-has-sobered-up/](http://burntfen.com/2015-11-29/the-user-has-sobered-up/)

	
  * 作者（author）：Richard Littauer（[@richlitt](https://twitter.com/richlitt)）





* * *



大概在六个月前，我产生了做一个网站的有趣想法，我完全预料到它是个笑话，我将分享给一些朋友，并很快被互联网忘掉。我就加入了在巴厘岛举办的 [Hacker Paradise](http://hackerparadise.org/)。我在那里的第一周，为了参加编程马拉松【注1】需要准备一个项目，因此我决定实现我的想法。我做了一个初级网站，对于风格或文案没有仔细推敲，当天下午就上线了。

想法非常简单：我在喝醉以后的状态里，评论你的网站。我将寻找 bug、暗淡的用户体验风格、拙劣的文案，并从总体上评估你的网站。域名很明了：[TheUserIsDrunk.com](http://theuserisdrunk.com/) 。

该网站得到了病毒式传播。在一小时内，我就登上了 Hacker News 头条，首日访问量就超过了 100,000 次。在一周内，点击大概有 30 万次。我还受到了 [FastCo](https://www.fastcodesign.com/3044455/reviewing-ux-designs-while-drunk-makes-way-more-sense-than-you-think)、[Tech.co](http://tech.co/heres-why-its-important-to-design-like-the-user-is-drunk-2015-03)、[Gizmodo](http://gizmodo.com/i-paid-a-ux-expert-100-to-get-drunk-and-evaluate-gizmo-1693902126)、[VWO](https://vwo.com/blog/drunk-review-worlds-easiest-ab-testing-tool/) 和 [Hubspot](https://blog.hubspot.com/marketing/hubspot-website-review-userisdrunk) 的采访。几乎与此同时，我开始收到订单。我把价格从 $50 提高到了 $500，以确保高到某一点，人们就不会下订单了。他们没有停止的迹象。

今天，我要宣布，我将关闭未完成的订单。

我乐于在本文分享这一过程以及整个体验中、我最喜欢的部分；专门喝酒是什么感受；我就特权所遇到的严重问题；我觉得是时候关闭该网站的原因；以及接下来的规划。


### 在喝醉状态下，评估 UX


The User Is Drunk 网站提供的服务，貌似和它名字涵义没有直接关联。实际上，我不是一名「用户」；也不是幼稚的人，让你在 fiverr.com 上付费；更不是朋友，你只是要求我看看你的测试版网站。我是全栈开发者，对评估网站的 UX/UI 富有经验，评估最多的是我在纽约和旧金山做为团队一员时所开发的网站。The User Is Drunk 网站很容易就被定性为「UX 独立评论员喝醉了」，附上下面一行字：「我会喝醉，假装我是正常用户，尽我所能地把你需要注意 UX 地方的建议提供给你。」这个服务一直被吹捧为「Richard 将会喝醉，并尽量保持一个良好状态，但是会脚踏两只船，一边是滑稽评论员，另一边是机敏的观察员。」

需要澄清一下，「The User Is Drunk 网站」不是一个彻底的新奇想法。因为还有一个人之前有过类似的想法：[Will Dayble](http://willdayble.com/)。毫无疑问，我是从他那儿才听到了这个词语，尽管如此，我当时并不知道这个想法的出处，只是觉得它是可以用在该行业里的一个普通想法。很可能我要多谈谈我的恍惚，而非还在发展中的 UX 状态。从 UX 角度看，关于醉酒用户的有意思之处，存在一些原因。我可以在这里全部列出来，但是 Hubspot 的 Austin Knight 根据我的服务、就醉酒用户的测试写过[一篇相当精彩的文章](http://austinknight.com/writing/ux-insights-from-a-drunk-guy/)，比我要说的话更有表现力。

我评论网站的过程是这样的。我常常和朋友们一起喝酒。在晚上某个时刻，我将离开 20 分钟，启动我的电脑。我通常把 10 分钟时间花在一个网站上------有时候，我会用 20 分钟，有时候则短到 5 分钟。 我用 Trello 【注2】组织各种材料。用 [ScreenMailer](https://www.screenmailer.com/) 传送视频，对于某些特定场景，我用 QuickTime 录制非固定的视频。然后，我把视频给到我的一个作家朋友 [David Young](http://davidfolgeryoung.com/)，他把我的初稿输出为排版精美的 PDF（最初由 [Simon](https://medium.com/u/5da5f67aece) 设计），我再将其发送给客户。David 绝对是把好手，我为他的文案编辑花费的每一美元都物有所值。他听我语无伦次的说话，一听就是数小时，竟莫名其妙地整理清楚了。

最后，我发送给客户的就是一份 PDF，列出了我发现的网站问题------bug、不好的风格、拙劣的文案等------还有一份清单，他们立即就能实施并改善网站。我还附加一份视频截图，以及我浏览他们网站的视频链接。如果他们喜欢并同意，我就把他们视频的链接放在我的网站。当时的视频总数达到 36 个。我可能总共评估了大约 50 个不同的网站。

实际的视频是主要交付的东西。有时候，它们真的对客户有帮助。我甄别 bug、找到他们不清楚、但已经存在的网站功能，指出哪个地方的文案可以写得更好。我收到了不错的反馈，偶尔地，我会碰到回头客。有时候，视频的用处还有其它理由------比如，他们想得到曝光。我相当肯定，Mathbreakers.com 并不清楚他们作为我的第一个客户而从我的网站得到了多少流量（很多）。有相当一部分客户，总的出发点就是想看看我能在他们网站上搞出什么，因为他们觉得，当我喝醉时，我是一个相当有意思的家伙。有时候，我的评论对于涉及到的每个人完全无用。我稍后再细谈这一点。


### 关于专门喝酒


住在巴厘岛和泰国，意味着喝醉不会太花钱、困难或出格。和我同行的有 30 多个朋友，每个晚上都有人要出去逛街。貌似很多人都喜欢看到我在酒局中间离开 10 分钟，跌跌撞撞在某个网站上浏览。我和朋友达成一项交易，因为我不想独自喝酒：如果我在评估某个网站，我将给每个人买酒喝。我对他们的要求就是，你懂的，陪我出去。他们多数人觉得，这种举动十分有趣，非常乐于奉陪。总有很多人愿意去喝酒。

当我首次把网站提交到 Hacker News 时，一条评论很快被顶了，它是：


<blockquote>酒精中毒可就惨喽 :(</blockquote>


一大拨 HN 评论员指出，这不是酒精中毒，之后，该评论就被删除了，更不要说很多人度过了快乐的时光（我不敢肯定我是否认同）。我希望评论员能够留下这条评论。尽管它貌似奇怪，但是，对我而言，这条评论第一次让我后退一步、诚实地思考我在做的事情。刚才说过了，我根本就没想到这个想法能得到病毒式传播。我当做玩笑在做。突然之间，有了合约，我被迫去喝酒。感谢这条评论让我有所思考。

我很快做了一些事情。首先，我在网站上添加了大大的免责声明。然后，我澄清了，在喝酒期间所要担负的责任，还有，关于在什么时间为客户做评估，我不做任何保证。一些人邮件中询问我，他们的评估什么时候做；对于这些情况，我通常只是把他们放到队列里。这让减轻了很大的喝酒压力。大概在第一个月里，我每隔几天就需要喝醉一次。我觉得，绝对没人愿意这样做的，不管什么理由。

我本来体重偏瘦。在这次冒险的开始阶段，我要喝两瓶啤酒，我没有开玩笑。我朋友不止一次建议，让我假装喝醉。我从来没有采纳，因为我不用多麻烦就能喝醉，假装喝醉会显得不诚实。我有个习惯，第二天要保持最佳效率，因为我讨厌宿醉，我喜欢工作。我的主要安排包括脂肪含量高的丰盛早餐、无糖的印尼餐、大量咖啡和长跑。如果你担心第二天可能要宿醉，那么，我强烈建议在睡了几个小时之后的拂晓，跑五公里。酒精会通过汗液排出体外，你就能保持健康，最初几公里的痛苦很快就会让位给极好的、自然产生的内啡肽快感【注3】。注意多饮水。

（我不想跑题，但是跑步的确很好。在热带炎热中跑步时穿过印尼稻田；黎明前在泰国海滩，地平线上出现捕虾船和闪电风暴，你旁边的幽灵蟹正在海浪里穿梭；我无法用言语表达这种美丽。比较而言，喝酒就惨透了，但是跑步是无法替我买单的。）

几个月之后，我的忍耐程度超出了极限，日常效率降低了。我做了调整，每周只「工作」一次，这样，我就不再偶尔喝酒了。幸运的是，我的价格水平此时已经高到客户难以接受了。

7 月份，我搬到了波士顿。十年来，这是我首次住在本土的新英格兰【注4】，我的社交团体也发生了根本变化------多数情况，和我出去的是家人、而非数字化旅行一族。由于我用更多时间和家人待在一起，因此我就没有太多喝醉的机会了。很快，我发现难以在晚上找到一起喝酒的人，这意味着我不得不规划未来几周的事情。目前的状态是对我身体好很多，但是总体上，我在业余项目投入少、在工作方面投入多。

如果喝酒变成了工作，你就能很快体会到喝酒有多痛苦。举个例子：酒精有镇静作用，常常试着保持良好状态会让人疲倦。有时候，我对人们网站的评论本质上没有多大用处或滑稽，常常是因为那晚我状态不佳。有一次，我觉得我在评估过程中有几分钟在唱歌。我不为此感到沾沾自喜。

酒也是昂贵的，因为时间和金钱。对我而言，这尤为恰当。有时候，我评估有问题的网站，就不得不一遍遍地浏览。多数情况，我的客户认为这很有趣，尤其是我发送邮件之后，我在邮件中精简地说明有问题的地方。不管怎么说，你是怎样做到让一个喝醉的人更有效率呢？有时候他们发现这一点儿也不好笑------毕竟，我有偿提供有价值的服务。我花在网站上的时间总量不同，这取决于我找到要点评材料的能力------不总是很容易------以及我当时有多疲惫或厌倦。关于我是怎样喝醉、或情绪如何，如果我能够站在这里，老实地对你说，我是如何做到标准化的，那么，要么我在撒谎、要么我不是人类（请慎重看待）。好在我站不到这里，这就是一部分喝酒的涵义。

酒精遮挡了判断力。有时候我的评论太白痴，有时候我觉得，做为评论者，我太过刻薄。我曾用大量时间阅读文章，并学习如何给出建设性和非建设性的批评。世事维艰，我希望能做得更好。酒精除了明显地伤害肝脏，还能导致危险状况。值得欣慰的是，我觉得还没有人曾被 The User（有时候朋友会这样喊我）伤害过，但是有过几次骑行，如果再来一次，我看你不愿意那样做了。


### 审视我的特权


我在 tweet 里讨论 The User Is Drunk，在早期我注意到一个现象：我的好朋友几乎不感兴趣，JavaScript 社区也几乎没有成员向我谈起过它，尽管我把自己视作该社区的一部分。有一种可怕的沉默。起初我分析，原因在于 The User 和 Javascript、node 或类似代码的东东关系不大。经过一通思考，我意识到，我对于其它一些地方感到惭愧：炫耀我的特权。很少有人对我大声喊出来；我真希望很多人喊过。

设想一下，如果我不是白人、异性恋、顺型男【注5】，会怎样。如果我是一名非洲裔美国人，The User Is Drunk 还能得到很多媒体铺天盖地的报道吗？如果我是名女性呢？如果我二者兼而有之呢？如果我来自印尼，就像创办之初我每天看到的绝大多数人一样，不是一名受过教育的、来自康涅狄格州的上中层阶级的人，又会怎样呢？

上面这些句子都是疑问，因为我还没有回答过。我真的明白，如果我是少数派的一员，将根本无法得到同样数量的媒体曝光；如果有，那么评论区域一定充斥着诽谤和侮辱的论调。我们都见过这种情景，因此我这里就无需为你提供某些潜在的例子了。因为我是一名白人，人们更容易分享我的网站，并津津乐道。

就这样过了几个月，我自己发现了更多的问题。比如，如果我不是异性恋、而是公开的同性恋，会怎样呢？我的性取向真的重要吗？当我在东南亚远足野营时，我发现了这个事实是在炫耀我的机动性和独立性，以及我是来自资本主义、战争贩子和殖民帝国（看看你，美国）的一个产品吗？我和这种传统串通一气了吗？

很快就到了最糟糕的问题，上面已经提到过了：如果我真的嗜酒，会怎样？我开始怀疑，我是否有本领去做很多人做不到的事情------过度饮酒。

有些奇怪的家伙，他们能记住第一次喝酒时的情景，我就是这种人。刚好在我 18 岁生日那天的下午 3:33，我想喝酒，仅仅因为这是合法的。我喝健力士啤酒【注6】，我讨厌它，那天晚上第一次喝醉，我也讨厌那样子。我还能数得清我在大一喝醉的次数，主要原因在于喝酒是一种巨大的象征，我被抚养时受到的保护太多了。

（注：我认为我不是嗜酒者，如果你乐意，我更愿意快乐地坐下来，和你认真地谈谈我。请保持联系，我听着呢。）

当我在朋友中间提出这些问题时，很多人对我说，「我对自己太苛刻了」、或「想太多了」。但是我没有在网站上回答这些问题、也没有过分关注它们，我只是在强行保持现状「只要你是白人，就可以喝酒、还可以调侃喝酒。」我还信奉喝酒文化，尤其是喝酒的技术文化，是个不错的事物。

它也不好。能够和你的同事或社区享受喝酒的乐趣，不是既定事实，而是一种特殊待遇，不是每个人都能负担得起、同意喝、喜欢喝、或可能会喝。我认识一些人，因为他们不喝酒，就和团队融合得不好。我还认识一些年轻人无法享受聚会，因为会场有酒。

我认识一些人，他们在和喝酒斗争着。酒精中毒是真实的，且让人生厌、有害和野蛮。

我试着让我的特权淡出视野，我在网站添了几行字。我对自己说，「确实------但是，事实上，你是一个健康的、有才干的、26 岁的技术男，你能这样做。那么，你为什么不做呢？找到乐趣，过你自己的生活。重新审视你自己，但是不要为此道歉。」

我仍然在争论，我在做的事情对不对。我的一些朋友坚决被归在了「不对，这样不好」的类别，还有一些朋友最后没有被归入此类别。意见有分歧，才让我们成为人类。

我在这里提出这些问题，是因为我觉得，讨论与提及它们要比找到答案更重要，也不是因为孤立地提出这些问题就能赦免我可能曾经犯下的所有罪恶或危害。我唯一能做的就是重新审视我的特权。我的某些方式是错误的，但愿我没有伤害到别人。技术作为一种文化，想不出错是根本不可能的。我们唯一能做的就是让其变得更好，作为一种文化，需要重新审视我们的特权。

你们当中有些人可能知道，后来我和朋友 Scotty Allen 和他的妈妈 Pam 一起启动了 [TheUserIsMyMom.com](http://theuserismymom.com/) 。尽管它没有伟大的商业成功，但是 The User Is My Mom 获得了巨大的流量，还见诸 Motherboard、Wired 和 CNBC 等网站。关于它是歧视残障人士者、还是男性至上主义者，我们也提出了一些类似的疑问。对于这两种情况，就我个人而言，我想断然否决，因为 Pam 想自己做，这是她的选择。但是，我们表述的方式或许可以更好一些，我不敢肯定，处于争议之中会是最好的选择。


### 美好的地方


阅读本文的后半部分可能没那么有趣（它们写起来也没多大意思）。关于运营 The User Is Drunk 的日常情况，我不想给出错误的表达。大部分情况下，这是一种非常享受的体验。我度过了一段快乐的时光。

最酷的一个情景是，当我见人时，有人会提起 TheUserIsDrunk.com，我听到最多的一句话是「哦，那个人就是你呀！？」时不时地出现，我都答道「对，是我，一般般了」，非常让我受用。我还经常在网上看到引用，比如 Designer News 顶部的这条：

[![design news](http://www.labazhou.net/wp-content/uploads/2015/12/dn-news-600x197.jpeg)](http://www.labazhou.net/wp-content/uploads/2015/12/dn-news.jpeg)

毫无疑问，我最为得意的评论是评估 [jeffreypicard.com](http://jeffreypicard.com/)。Jeff 是我喜欢的人。他的网站没有 CSS，他付费给我，是因为他想看看我能折腾出什么。我笑得太难听了，[这里是我的评估视频](https://www.screenmailer.com/v/sXyhHiYTcauAQqI)。

另一些出彩的评论包括我对 meh.com 的[评论](https://www.screenmailer.com/v/aqUEFaIwIjbFGME)，我没有养狗，却买了小狗的玩具；我对 weeklyfilet.com [评论](https://www.screenmailer.com/v/MacCNd8UnNtlqx4)时，我是如此地喜欢他们的产品，以致于我提到了，David Bauer 和我应该成为朋友（此后我们就在 Facebook 和 Twitter 交了朋友，更多是为了搞笑）；我对 [drsquatch.com](https://www.screenmailer.com/v/tmtT6Yyf7UagZ7w) 评论时，觉得这个网站值得记住，主要是因为他们的网站非常优秀，产品也很棒。他们送给我一些肥皂，味道绝对让人称奇------嗯，我很认真地说，你应该停下手头的工作，去他们那儿买一块香皂。

我和我的赞助商 BREWPUBLIK 度过了一段绝对快乐的时光。BREWPUBLIK 是北卡罗来纳州非常不错的公司，他们把精心挑选的酒送到你门口。我曾经去拜访过他们，团队优秀且工作非常努力。怎么赞美他们都不为过（当然，我不是有偿替他们说话）。


### 我为什么关闭了网站


我刚才列举了我关闭 The User Is Drunk 网站的诸多原因，但是我想扼要重述一遍。

它没有盈利，或者不能变成盈利项目，或者无法扩大规模，这些都不是原因。我考虑过所有这些因素，针对醉酒评论，肯定存在一个可持续的商业模型。The User Is Drunk 还帮我很快还清了信用卡债务，我为此感到非常开心，在我人生当中，我第一次有了结余，真的很棒。醉酒评论的财务状况和减少的需求不是我写本文的理由。

主要原因在于，我不想再专门喝酒了。当初和现在的社区环境不同了，我不想喊朋友和我出去喝酒，尽管我知道有财务收益。你可以说我疯了，我的一些朋友也这样说我（尤其有人说，「把利润分给我们一部分，我们就干」。当然你也疯了，傻瓜）。

我还能够说，我已经为我支持的每个人都提供了价值。我觉得这不都对，也不都起到了正向作用。我不想只是给人们一个产品------我想让我认识的每个人都变得优秀，一直这样下去。那也是我的做人方式。The User Is Drunk 是一次有趣的经历，但是我认为它不太成功；有几次，我让客户失望了，有几次在我发了视频之后，却没有收到回复邮件，我觉得我可能有过过河拆桥。我讨厌过河拆桥，我憎恨自己让人们失望。既然我不能标准化我该怎么喝酒、以及我在醉酒状态该给人们提供多少价值，因此，我打算尝试做其它事情。


### 下一步规划


如本文所言，我不再做喝酒评估网站的事情了，所以，我打算尝试并专注于提供更好的、清醒的评论。如果你需要任何 [UX/UI](http://www.labazhou.net/2015/09/what-s-the-difference-between-ux-and-ui/) 评估，请联系我。我乐于被聘用。

你或许注意到了上面提到的「定期的」和「关闭了未完成的订单」。这意味着，如果你真的想索取一份喝醉的 Richard 视频，请给我发邮件。我不再为付费客户做网站了，不过，如果我喜欢你的网站，我觉得我能帮到你、且帮助你的网站更棒------恩，或许我会看看能否在偶尔的夜出之后，为你提供一些评论。这样做，应该有助于我更好地控制生活和产品的质量，这会让我------还有你------更快乐。

现在，我打算更多地专注于开源项目。我仍然忙于 [Beagle](https://github.com/BeagleLab/beagle/)，它是一个 Chrome 扩展，为 PDF 和 HTML 做注解的工具，我一直和 MIT Media Lab 共同开发，让科学变得更好。我还想更多地致力于 [IPFS.io](https://ipfs.io/)，它是分布式 web，我觉得它会严重地改变我们使用互联网的方式。

我还想写更好的奇幻文学【注7】，爬更大的山，欣赏更多艺术，跑马拉松，当志愿者帮更多人，享受深夜阅读的温馨和清晨的神清气爽。如果你有兴趣关注我的未来状况，了解我已有的和正在思考的项目------我这里提供了一份小巧的 newsletter: [https://tinyletter.com/richlitt](https://tinyletter.com/richlitt)

这就是未来，一起欢呼吧！


### 注释

* 注1：编程马拉松（英语：hackathon，又译为黑客松），又称黑客日（hack day）、黑客节（hackfest）或编程节（codefest），是一个流传于黑客（hacker）当中的新词汇。[https://zh.wikipedia.org/wiki/%E9%BB%91%E5%AE%A2%E6%9D%BE](https://zh.wikipedia.org/wiki/%E9%BB%91%E5%AE%A2%E6%9D%BE) 
* 注2：Trello 是由Fog Creek Software开发的一款免费的网络应用程序。Trello的基本形式是“列表的列表”，它可以用作1980年代流行的丰田供应链管理方式看板管理的工具，也可用于维护各种用途的列表或清单形式的资料。[https://zh.wikipedia.org/wiki/Trello](https://zh.wikipedia.org/wiki/Trello) 
* 注3：内啡肽（endorphin），亦称安多酚或脑内啡、脑内吗啡[1]，是一种可于动物体内自行生成的类吗啡生物化学合成物。“跑步者的愉悦感”（runner's high）是指当运动量超过某一阶段时，体内便会分泌脑内啡。长时间、连续性的、中量至重量级的运动、深呼吸也是分泌脑内啡的条件。长时间运动把肌肉内的糖原用尽，脑内啡便会分泌。这些运动包括跑步，游泳，越野滑雪，长距离划船，骑单车，举重，有氧运动舞或球类运动（例如篮球，足球或美式足球）。[https://zh.wikipedia.org/wiki/%E5%86%85%E5%95%A1%E8%82%BD](https://zh.wikipedia.org/wiki/%E5%86%85%E5%95%A1%E8%82%BD) 
* 注4：新英格兰（英语：New England），当地华人常称之为“纽英伦”，是位于美国大陆东北角、濒临大西洋、毗邻加拿大的区域。新英格兰地区包括美国的六个州，由北至南分别为：缅因州、新罕布什尔州、佛蒙特州、麻萨诸塞州、罗德岛州、康涅狄格州。麻萨诸塞州首府波士顿是该地区的最大城市以及经济与文化中心。[https://zh.wikipedia.org/wiki/%E6%96%B0%E8%8B%B1%E6%A0%BC%E8%98%AD](https://zh.wikipedia.org/wiki/%E6%96%B0%E8%8B%B1%E6%A0%BC%E8%98%AD) 
* 注5：顺性男（Cis Male或Cis Man），即出生时的生物性别是男性，自己也认为自己是男性。以顺性别为标准看待社会的世界观被称作“顺性别主义”（cissexism）。[https://zh.wikipedia.org/wiki/%E9%A0%86%E6%80%A7%E5%88%A5](https://zh.wikipedia.org/wiki/%E9%A0%86%E6%80%A7%E5%88%A5) 
* 注6：阿瑟·健力士公司（Arthur Guinness Son & Co.）是一家由阿瑟·健力士（Arthur Guinness）于1759年在爱尔兰都柏林建立的一家酿酒公司。酿酒厂最著名的产品是一种黑色的司陶特啤酒（stout，属于黑啤酒，黑啤，或波特啤酒），名为健力士（Guinness）。[https://zh.wikipedia.org/wiki/%E5%81%A5%E5%8A%9B%E5%A3%AB](https://zh.wikipedia.org/wiki/%E5%81%A5%E5%8A%9B%E5%A3%AB) 
* 注7：奇幻文学是指文学类的奇幻作品，主要表达于奇幻小说。广义上含有奇幻要素的文学作品也包括在内，玄幻小说、武侠小说与古代流传的童话、神话、民间传奇故事，并依此衍生了奇幻色彩的歌剧、电影、剧本、RPG、动漫等。[https://zh.wikipedia.org/wiki/%E5%A5%87%E5%B9%BB%E6%96%87%E5%AD%B8](https://zh.wikipedia.org/wiki/%E5%A5%87%E5%B9%BB%E6%96%87%E5%AD%B8) 
