---
author: viviworld
comments: true
date: 2015-02-10 09:07:58+00:00
layout: post
link: http://www.labazhou.net/2015/02/principles-of-an-ideal-database-client/
slug: principles-of-an-ideal-database-client
title: 理想数据库客户端的准则
wordpress_id: 1619
categories:
- 编程
tags:
- github
- MongoDB
- nodejs
- ORM
- Redis
- superjson
- 数据库
- 混合持久化
---

原文地址（original source）：[http://lapwinglabs.com/blog/principles-of-an-ideal-database-client](http://lapwinglabs.com/blog/principles-of-an-ideal-database-client)

当我们在构建[Gittask](https://gittask.com/)时，注意到了一些抽象漏洞【注1】，尤其是在我们的数据库客户端。我们不得不编写一些样板来处理类型转换和反转。这促使我围绕这个问题想了很多：


<blockquote>理想的数据库客户端应该是什么样子？</blockquote>


数据库客户端有着各种类型和大小。一些用起来不太爽，一些相当有爱。不幸的是，我已经发现所有的数据库客户端在不同的地方存在欠缺。下面是我认为的理想数据库客户端的特点。


## 理想数据库客户端的准则


根据我的看法，理想数据库客户端将有下列特点：



	
  * 无损序列化和反序列化
进去的数据和出来的数据，应该是完全一致的。如果做不到，那么数据就根本不应该放进去。

	
  * 混合持久化（Polyglot Persistence）
你的数据库客户端应该能够与不同的后端数据库交流。

	
  * 跨数据库的原子事务
你的数据库客户端应该能够跨数据库连接在一起进行写操作，当管道中的任何地方失败时，应该能够回滚。


让我们具体深入每个准则：


### 无损序列化和反序列化


作为开发人员，我们不必对数据库如何处理数据感到担忧。这是抽象漏洞，非常容易出错。

我们的数据库或数据库客户端应该对保持这些数据结构的完整性负起责任。当你保存一个Date对象时，你应该期望回头还能得到一个Date对象。

序列化和反序列化步骤应该是独立的，但是被理想的数据库客户端使用着。可能存在一些情况，你不会使用这个客户端做数据获取，但是你仍然想让数据正确地被装箱（cast）。

我编写了superjson，做为首次尝试，使用Node.js来解决这个问题。


### 混合持久化


数据库环境在过去的十多年里增长巨大。每个新的数据库相较于其它数据库，有着某些优势，但是它们做了某种折衷。

事实上，CAP定理【注2】告诉我们，不可能拥有完美的数据库，我们需要根据应用程序来选择哪种折衷是可接受的。

带有这些约束的工作场景符合[Martin Fowler](https://twitter.com/martinfowler)推广的[混合持久化](http://martinfowler.com/bliki/PolyglotPersistence.html)思路。混合持久化的思路是指，你应该根据工作选择合适的数据库，这样我们就能两者兼得了。

我们的数据库客户端应该这样做，它应该能够与很多不同的数据库交流。在代码层面看起来是这样的：


<blockquote>Client(mongo(details)).put(key, value);
Client(redis(details)).get(key);</blockquote>




### 原子事务


你应该能够跨数据库定义原子事务。很多数据库针对各自的情况有着原子事务的途径，但是在混合持久化的世界，这还不够好。

比如，当你创建一个用户，通常你执行两次数据库写操作：


<blockquote>Save the user data
Save the user session (这样相当于登录了)</blockquote>


你应该在相同的数据库里操作这两步，那么你正在以牺牲性能或查询灵活性为代价。符合这种任务的、通常的混合持久化是用Mongo存储用户数据、用Redis存储用户session。

这些写操作是原子的，这是十分重要的。如果其中一个写操作失败了，你的应用程序将处于不合法的状态，如果在运行这些命令时出现了错误，我们需要数据库客户端“回滚”变化。最简单的方法就是生成快照，如果失败了，就回滚到旧的快照。在代码实现上，看起来是这样的：


<blockquote>client.atomic()
.db(mongo).put('user', obj)
.db(redis).put('session:' + sid, obj.id)
.run(fn);</blockquote>


在每次写操作之前，理想的客户端将知道当管道某处出现错误时，如何倒退回去。


### 关于ORM


我在[使用](https://github.com/LearnBoost/mongoose/)和[开发](https://github.com/modella/modella)ORM上花了大量时间，我现在敢肯定它们都是抽象漏洞，随着你的应用程序的增长，它们带来的害处将大于好处。

Laurie Voss在2011年的博客中谈到过为什么[ORM是反模式的](http://seldo.com/weblog/2011/08/11/orm_is_an_antipattern)。这篇博文仍然有着重要意义。

我认为，你应该根据提供的优秀standalone数据校验资源库（我推荐[rube](http://github.com/lapwinglabs/rube)）和我们的理想数据库客户端来充分利用ORM的优势。

然后你借助适合工作的最佳工具，以高效的方式来编写你自己的model。


### 关于数据库提供的独特特性


你或许觉得奇怪：某些数据库比其它数据库有着更多的特性。编写一个客户端，它还能利用某种数据库的独特特性，你该怎么做？

我相信所有数据库操作都可以归结为一些低层次的操作：


<blockquote>- client.get(key)
- client.put(key, value)
- client.del(key)
- client.select(collection) (or "database", "table", "sublevel", etc.)
- client.atomic() (初始化一个原子事务)</blockquote>


我想，理想的数据库本身要支持这些操作，但是能够被扩展为某种数据库的独特特性（通过信号）。代码表现为：


<blockquote>var client = Client(mongo(details));
client.put(key, value);
client.mongo.query(query)</blockquote>


`clinet.mongo`将很容易定位到那些mongo独一无二的特性。这让你的数据库更加可交换（interchangeable）。因此如果我们把主要的数据库变更为LevelDB，那么我们的mongo相关的查询将变成：


<blockquote>var client = Client(leveldb(details));
client.put(key, value);
client.mongo.query(query);</blockquote>




### 一起开发


理想的数据库还没有被构建好。现在，它是一系列高级想法，它们应该被应用到这个客户端里。我正在号召社区帮助制定出细节，并贯彻执行。

如果你有兴趣参与或跟进，我已经在[Github](https://github.com/lapwinglabs/yurt)建立了一个仓库，名称暂定为Yurt。

和平时一样，如果你喜欢我们做的工作，或者想关注我们学习的东西，请关注Twitter：[@lapwinglabs](https://twitter.com/lapwinglabs)。



	
  * 注1：抽象漏洞定律（The Law of Leaky Abstractions）是一个有关程式的定律。最早是由Joel Spolsky在其部落格中提出，其定义为“所有非不证自明的抽象概念，都有某种程度的疏漏”。[http://zh.wikipedia.org/wiki/%E6%8A%BD%E8%B1%A1%E6%BC%8F%E6%B4%9E%E5%AE%9A%E5%BE%8B](http://zh.wikipedia.org/wiki/%E6%8A%BD%E8%B1%A1%E6%BC%8F%E6%B4%9E%E5%AE%9A%E5%BE%8B)

	
  * 注2：在理论计算机科学中，CAP定理（CAP theorem），又被称作布鲁尔定理（Brewer's theorem），它指出对于一个分布式计算系统来说，不可能同时满足以下三点。详见 [http://zh.wikipedia.org/wiki/CAP%E5%AE%9A%E7%90%86](http://zh.wikipedia.org/wiki/CAP%E5%AE%9A%E7%90%86)


