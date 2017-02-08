---
author: viviworld
comments: true
date: 2015-01-09 01:40:38+00:00
layout: post
link: http://www.labazhou.net/2015/01/using-nosql-wrong-reason/
slug: using-nosql-wrong-reason
title: 你在以错误的原因看待NoSQL数据库吗？
wordpress_id: 1503
categories:
- 编程
tags:
- MongoDB
- NoSQL
- PostgreSQL
- SQL
---

原文地址（source）：[http://maurizioturatti.com/blog/2015/01/06/using-nosql-wrong-reason/](http://maurizioturatti.com/blog/2015/01/06/using-nosql-wrong-reason/)

[![PostgreSQL与MongoDB的性能评测](http://www.labazhou.net/wp-content/uploads/2015/01/MongoDB_26_v_Postgres_94_Performance.png)](http://www.labazhou.net/wp-content/uploads/2015/01/MongoDB_26_v_Postgres_94_Performance.png)

我最近看到一篇报道，在某些条件下，[PostgreSQL在很多重要地方胜过MongoDB](http://blogs.enterprisedb.com/2014/09/24/postgres-outperforms-mongodb-and-ushers-in-new-developer-reality/)，这让我想起了关于数据存储选择方面的、不同选项背后的理论，特别是在SQL和NoSQL解决方案之间的天真比较------不幸的是，这一幕经常发生。

上面的评测由EnterpriseDB创建，EnterpriseDB是开发PostgreSQL的商业公司（因此测评可能会有一点儿偏见……），除了这个明显的事实，我已经注意到PostgreSQL是让人惊奇的产品，在这一点上，我推荐它作为亟待解决的、大部分数据存储问题的、最佳方案之一。有着非凡性能需求的知名企业都正[在PostgreSQL上投入巨大](http://gotocon.com/berlin-2013/presentation/Why%20Zalando%20trusts%20in%20PostgreSQL)。

然而，我这里的观点稍微不同：我自问，大多数公司是否正确地看待着“NoSQL”解决方案、以及性能需求是否已经成为他们急需考虑的。比如，让我们看看MongoDB词条在维基百科上的解释，它是我这些天经常在用的、一种数据库：


<blockquote>MongoDB是一种跨平台的面向文档的数据库。作为一种NoSQL数据库，MongoDB没有采用传统的基于表的关系型数据库结构，而是钟情于带有动态模式的类JSON文档（MongoDB称之为BSON），使得特定类型的应用程序里的数据集成更容易、更快速。</blockquote>


我想刻意强调句子中的“特定类型的应用程序里”，因为这恰恰就是我要说的：你不能仅仅因为性能就抛弃关系型数据库、转而采用面向文档的数据库，因为这是愚蠢的动机：一个调优的[SQL](http://www.labazhou.net/2014/06/why-you-still-need-sql/)数据库[每秒处理的事务能够超过14000条](http://pgeoghegan.blogspot.it/2012/06/towards-14000-write-transactions-on-my.html)，因此如果你超过了这个量级，说明你已经在一流的公司里了，有着首要的扩展需求：恭喜！

相反，


<blockquote>当实体大部分与树形结构相关，且关系模型持续被迫地创建join或重度反规范化关系而超越了其合理性时，文档数据库就是优于关系型数据库的更好的解决方案。</blockquote>


在这种情况下，数据模型符合上面的约束，那么面向文档结构有能力比关系型模型创建更少的、与面向对象设计不匹配的现象。据我们所知，所有重要的关系型数据库模式创建了大量的与对象模型相关的属性，这就是饱受诟病的[对象关系阻抗不匹配](http://en.wikipedia.org/wiki/Object-relational_impedance_mismatch)（Object-relational impedance mismatch）问题。面向对象的系统通常是树状结构，它比其它模型能够更好地适应文档数据库，[图数据库](http://en.wikipedia.org/wiki/Graph_database)【注1】除外，很明显，图数据库实现了一个图的大部分通常表现。

在SQL领域之外，我总是建议不要低估你和团队正在失去大部分久经考验的工具和专长，你们每天都在不自觉地应用着。我看到过很多人费力地从NoSQL仓库抽出非常基本的信息，而这些信息用关系型数据库就可以容易地实现，主要是因为多年来人们都是这样做的。那么，NoSQL数据库在管理事务上，和“正统的”关系型数据库相比，有着很大的不同：用[最终一致性](http://en.wikipedia.org/wiki/Eventual_consistency)(Eventual Consistency)和[幂等服务](http://soapatterns.org/design_patterns/idempotent_capability)(Idempotent Services) 设计应用程序，你知道意味着什么吗？

我不是说你不应该采用新技术，因为[我和公司已经为此做了很多](http://restheart.org/)，但是我的最终建议是：


<blockquote>采用适合你的领域模型（domain model）【注2】的数据存储方案，不要过早地性能伪优化：[你可能在尽量解决错误的问题](http://www.azarask.in/blog/post/the-wrong-problem/)。</blockquote>





	
  * 注1：图数据库也可称为面向/基于图的数据库，对应的英文是Graph database。图数据库的基本含义是以“图”这种数据结构存储和查询数据，不是存储图片的数据库。图数据库的基本存储单元为：节点、关系、属性。[http://zh.wikipedia.org/wiki/%E5%9B%BE%E6%95%B0%E6%8D%AE%E5%BA%93](http://zh.wikipedia.org/wiki/%E5%9B%BE%E6%95%B0%E6%8D%AE%E5%BA%93)

	
  * 注2：领域模型可以被看作是一个系统的概念模型，用于以可视化的形式描述系统中的各个实体及其之间的关系。领域模型记录了一个系统中的关键概念和词汇表，显示出了系统中的主要实体之间的关系，并确定了它们的重要的方法和属性。因此，对应于用例所描述的动态视图，领域模型提供了一种对整个系统的结构化的视图。领域模型的一个好处是描述并限制了系统边界。[http://zh.wikipedia.org/wiki/%E9%A2%86%E5%9F%9F%E6%A8%A1%E5%9E%8B](http://zh.wikipedia.org/wiki/%E9%A2%86%E5%9F%9F%E6%A8%A1%E5%9E%8B)


