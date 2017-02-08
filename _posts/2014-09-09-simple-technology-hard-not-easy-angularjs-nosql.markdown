---
author: viviworld
comments: true
date: 2014-09-09 14:07:00+00:00
layout: post
link: http://www.labazhou.net/2014/09/simple-technology-hard-not-easy-angularjs-nosql/
slug: simple-technology-hard-not-easy-angularjs-nosql
title: 为什么越简单的技术对于开发人员越难
wordpress_id: 1043
categories:
- 编程
- 软件
tags:
- Airbnb
- Amazon
- AngularJS
- aws
- DBA
- javascript
- NoSQL
- Redshift
---

## 简单 != 容易


从Amazon Web服务到[AngularJS之类的web框架](http://readwrite.com/2014/02/06/angular-backbone-ember-best-javascript-framework-for-you)，便利性[驱动着](http://readwrite.com/2012/12/20/cloud-convenience-checkmates-concerns)世界上最好的技术。但是，更加快速地、变得有效率的“便利性”，经常伴随着一个隐藏的价格标签：为了变得真正有效率，你将不得不花些功夫。

伟大的技术经常貌似简单，新手们直觉上不需要太多努力就可以“学习”。当人们认为他们已经掌握了这门技术、而他们真正做的所有工作相当于是一个“hello world”程序的等价物时，问题就出现了。在你归咎于这个工具之前，你往往需要投入时间以正确地使用它。


### 关于AngularJS的“复杂感受”


让我们用AngularJS做例子。AngularJS是一个[web应用程序框架](http://en.wikipedia.org/wiki/Web_application_framework)------JavaScript代码类库、模板和其它软件的集合，目的是让开发人员更加容易地开发动态网页或web app。

正如[Anand Mani Sankar建议](http://anandmanisankar.com/posts/angularjs-best-parts/)的，问题在于AngularJS入门容易，简单掩盖了框架的力量：


<blockquote>[AngularJS]通过抽象了很多内部的复杂度，而只暴露程序开发人员关心的东东，大大简化了应用程序的开发过程。</blockquote>


听起来这是一项伟大的工作，它也让新手们在完成第一个“hello world”应用程序后，就觉得掌握了这套系统：


<blockquote>AngularJS旅程会产生复杂的感受。学习曲线与其它JS框架有着很大的不同。进入的门槛非常低。但是，当你开始深入的时候，学习曲线突然变得陡升了。</blockquote>


Sankar然后引用了[Ben Nadel关于AngularJS旅程的幽默描述](http://www.bennadel.com/blog/2439-my-experience-with-angularjs-the-super-heroic-javascript-mvw-framework.htm)：

[![AngularJS的学习曲线](http://www.labazhou.net/wp-content/uploads/2014/09/angularJS-study-feelings.png)](http://www.labazhou.net/wp-content/uploads/2014/09/angularJS-study-feelings.png)

当然，一些人被卡在了谷底。比如，George Butiri从Google搜索到了很多关于“[The reason Angular JS will fail](http://okmaya.com/2014/03/12/the-reason-angular-js-will-fail/)”的文章。Butiri解释道，AngularJS实际上相当难，没有给出太多专门的例子来解释为什么是这样子，至少超过了“因为我更喜欢jQuery。”


### 太容易失败了


很多最好的技术都是这样。它刚开始时简单，不过如果你想真正掌握它，你将不得不投入大量时间。一些人开始势头很好，发现了复杂，然后抱怨这门技术没有永远地保持出乎意料的好。

对不起，真正的技术不是那样运转的。它总是需要努力，如果不能以正确的方式运行，就会失败。

看看[NoSQL数据库](http://readwrite.com/2013/03/25/when-nosql-databases-are-good-for-you)，我在这个世界花了太多的时间。

NoSQL对于新手而言，无论是MongoDB、HBase还是Cassandra，喜欢[兜售它的无模式特性](http://stackoverflow.com/questions/3856222/whats-the-attraction-of-schemaless-database-systems)（schema-less）。关系型数据库的旧世界需要僵硬的模式而且狂热！在NoSQL的新世界，定义数据结构的模式消失了，DBA们消失了，规则消失了！真简单！！

当然，这完全是胡扯。正如我的同事[Asya Kamsky喜欢说的](http://www.kamsky.org/stupid-tricks-with-mongodb/nosql-nodba)，“NoSQL != NoDBA.”（NoSQL与“没有数据库管理员”不是一回事儿。）


<blockquote>NoSQL不代表“没有DBA”。如果有人试图这样说服你，他们很可能要向你推销什么。这不意味着你有一个具有“DBA”头衔的团队或人员------然而，如果你有一个数据库，无论它是关系型，还是非关系型，那么一定有人担任“DBA”角色------如果他们不知道他们做的事情，那么在问题出现之前，一大堆工作将不会完成或被考虑到。</blockquote>


浏览关于NoSQL数据库、AngularJS或大部分你喜欢的技术方面的文章，我保证，如果不是大部分，也有很多是由那些感觉受欺骗的人写的，技术没有按照这种用户想要的方式运行，因为他们没有真正的投入。的确，有时候是技术失败了。多数情况则是令人触目惊心的。

但是，当技术没有神奇地减掉我们需要的工作时，我们常常在抱怨。


### 杠杆越少，幸福越多？


从这两者得到好处的一种方式就是通过可管理的服务，比如Amazon web服务的[Redshift](http://docs.aws.amazon.com/redshift/latest/mgmt/welcome.html)。Redshift是一个运行在云端的、完全管理的数据仓库。“完全管理”意味着它更容易使用，但是它也意味着用户失去了他们可能在Teradata或另一种企业数据仓库中的一些把手和杠杆（the knobs and levers）。

然而，这恰恰就是问题的关键。

正如AWS数据科学的总经理Matt Wood最近告诉我的，Redshift和其它AWS服务致力于通过移除复杂让用户易于使用。给用户更少的“杠杆”意味着AWS也给他们更少的失败方式。当然，技巧是在产品简单与用户控制之间找到平衡。

例如，Airbnb对Redshift刚开始是如何容易[感到洋洋得意](http://nerds.airbnb.com/redshift-performance-cost/)，但是随后就需要一些折衷（和投入）：


<blockquote>我们面临的第一个挑战就是模式迁移。即使Redshift是基于Postgres 8.0的，“微妙的”不同仍然足够大，强迫你用Redshift的方式工作。我们尽量自动化模式迁移，但是问题比我们最初期望的更大，我们认为它超出了试验的范围。在Redshift里，索引，时间戳类型，数组，不被支持，这样你需要在你的模式里排除它们，或找到变通方案。</blockquote>


无论如何，Airbnb投入了努力，看到了至少五倍的性能提升和巨大的成本节约。起步容易，但是也值得继续投入。

也有很多伟大的软件，它们看起来使用简单。为了走出对于任何伟大技术的新手状态，你将不得不有目的地使用，你将不得不投入时间和努力来掌握它。

可以有免费的软件，但没有免费的午餐。

原文地址：[http://readwrite.com/2014/09/08/simple-technology-hard-not-easy-angularjs-nosql](http://readwrite.com/2014/09/08/simple-technology-hard-not-easy-angularjs-nosql)
