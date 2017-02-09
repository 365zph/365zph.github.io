---
author: viviworld
comments: true
date: 2015-09-28 23:21:15+00:00
excerpt: AWS 或许最适合迁移到云。GCP 或许更适合新的、基于容器的应用程序。这是一场持久战。
layout: post
link: http://www.labazhou.net/2015/09/aws-vs-google-cloud-flexibility-vs-operational-simplicity/
slug: aws-vs-google-cloud-flexibility-vs-operational-simplicity
title: AWS 和 Google 云：灵活性 VS 操作简单性
wordpress_id: 2565
categories:
- 编程
- 软件
tags:
- Amazon
- api
- aws
- Bigtable
- cassandra
- GCP
- newsletter
- PaaS
- SaaS
---


	
  * 原文地址（original source）：[https://medium.com/@davidmytton/aws-vs-google-cloud-flexibility-vs-operational-simplicity-dca4324b03d4](https://medium.com/@davidmytton/aws-vs-google-cloud-flexibility-vs-operational-simplicity-dca4324b03d4)

	
  * 作者（author）：[https://twitter.com/davidmytton](https://twitter.com/davidmytton)





* * *



对于我在 Medium 的第一篇文章，我想重新回顾一个理论，我在 2015-4-15 号的一封电子邮件 newsletter 写过------《[AWS 不同于 Google 云平台](http://us10.campaign-archive1.com/?u=5dfb7b5de8e42c2633c06b3a8&id=36227f3963)》------并且，我添加了自己的理论，即 container（容器）是怎样成为 Google 云平台策略的核心。


### 核心理论


表面看，AWS 和 GCP（Google 云平台）非常相似，但是，它们的产品设计方法，实际上有着很大的不同：



	
  * **AWS：灵活性**。它们提供了很宽泛的复杂功能，支持你在自己的数据中心复制你已有的任何东西。范围包括，控制低层次网络和计算，提供多种关键的基础产品，比如日志、监控、访问控制和负载均衡；还有应用程序级别的服务，比如搜索、电子邮件收发、文件共享和数据库。这取决于正确使用它们的开发者。

	
  * **Google 云平台**：操作简单性。它们提供了和 AWS 同样种类的产品（尽管有很多不同），但是在它们的使用方式、隐藏那些他们认为应该不需要考虑的选项方面，却有着特有的观点。Google 有这方面经验，它们可以替你用最好的方式处理大部分工作。




#### 例子：价格


为了描述这些不同，最好的方式就是浏览一下定价方式。

Amazon 给你的选择相当宽泛：按需、预留（指定区域、操作系统、使用以及根据市场售卖预留）和市场竞价（最低的价格和多样化定价）。然后，还有其它基于成本的使用，比如 I/O 费用、容量大小的费用、提供的 IOPS【注1】，以及选择预留的容量。

与之相反，Google 仅仅根据你的使用，对实例成本、自动化「sustained usage」打折，给出了一种价格，然后以很大的折扣、但有限周期来选择独占实例。磁盘根据容量大小定价，并给出了可预测的性能，可线性扩展。数据存储对每个节点给出了有保障的吞吐量，因此你能够随着成本按比例增加性能。

Amazon 是最**灵活**的，给你足以宽泛的可变因素，让你最大化优化、计算出最优成本效益的、按需与预留（需要一些预付款）的组合，而 Google 定价非常**简单**，主要根据你现在需要的规模，并按需线性增长。


#### 例子：数据库


Google 因其 [Bigtable](https://en.wikipedia.org/wiki/BigTable) 服务而知名。描述了这项技术的论文，导致了诸如 Cassandra 和 HBase 的产品。Amazon 也有类似技术，它发布了 [Dynamo](https://en.wikipedia.org/wiki/Dynamo_%28storage_system%29)（Cassandra 也从中吸收了一些思想），因其产生的产品有 Riak 和 Aerospike。

Google Cloud Bigtable 和 Amazon 的 DynamoDB 是等同的云平台。前者只是最近才上线，但只是根据每个节点和存储容量模型简单定价。每个节点都能处理一定数量的 QPS，当你为额外的性能而增加更多节点时，价格会线性增长。与之相反的是，DynamoDB 定价是基于提供的吞吐量（读和写分离），单位是「capacity units」，按照每小时 + 索引的数据存储 + 可选功能，比如跨区域复制和流。还有预留的功能和网络费用。

Amazon 给你更多的**灵活性**来选择功能，根据你的计算精确到你所需的能力。Google 喜欢问你需要哪种规模、多少数据，然后给出**简单**的价格，可被线性预测到。


### 哲学渊源


我觉得，这些不同方法可以做这样解释，即产品的内在来自哪里。

Google 已经建立了一套内部平台。所有公共服务都是 Google 工程师本来就要构建的 Google 服务的产品化的版本。规定的目标就是，Google 工程师不需要知道数据保存在哪儿、需要提供多大的吞吐量、也不需要数据中心怎样处理复制……它们只是在消费一个 API，让 Google 软件在他们可信赖工程师的支持下，在背后处理所有东东。这是一种真正的平台即服务（PaaS），Google 想把你看成是一名 GCP 客户，每个客户都处于同样的位置，相信 Google 明白，什么是最好的。这是一种**[操作简单性](http://www.labazhou.net/2014/09/simple-technology-hard-not-easy-angularjs-nosql/)**------仅仅上马就可以开发你的应用。

Amazon 更多是建立一个产品范围，以取代你的数据中心。当你自己运行时，你有着**全部的灵活性**，并掌控一切。Amazon 貌似认为，你不应该处理真正低层次的工作，比如数据中心能力、环境、网络设备等，但是当它透过 API 时，它仍然能够暴露很多选项。Amazon 的 VPC 产品以及给予你的选择，显示了软件定义网络的实现哲学。你更好地明白你的应用，你应该有灵活性使之最优化。


### 该如何应用到容器


Google 正在推进容器大会，[Kubernetes 和开放格式](http://us10.campaign-archive1.com/?u=5dfb7b5de8e42c2633c06b3a8&id=578876abd2)，因为容器将是关于「应用如何被部署」的未来。如果潜在的基础设施不重要，容器能够被随处放置和运行，那么区别就在于它们消费的服务上了。

Google 正试图为你做出最重要的决定，因此其服务将达到同行一流水平。有了一整套 IaaS/SaaS 产品，你可以只根据规模和数据大小要求的**简单**计算，就可以消费了，它最终让 GCP 成为运行你应用的最好场所。这适用于运行容器本身------Google 处理部署、提供请求的资源和冗余。上传容器，开搞即可。

Amazon 在运行容器技术方面经验较少，而 Google 是先驱。Amazon 现在或许赢了，但是当 GCP 成熟时，它们的赌注是，容器将完全可移植，GCP 将是更加令人信服的方案，它是基于应用来运行容器的最佳场所。


### 哪种方式更好？


Amazon 是最大的提供商，但是 Google Cloud 目前已经出现了，在 18-24 个月就会爆发真正的竞争力。问题在于：开发者愿意要完整的**灵活性**，还是愿意让扩展数据库和跨数据中心网络得以解决、并将其做为平台的一部分，使得操作上**简单**。

PaaS 一直都深受欢迎，不过在扩展上通常价格昂贵。当你有更多控制时，你可以更好地优化。但是以前，Google 和 Amazon 在打价格战，这项服务和垄断的应用程序平台一直是分开算的。

如果你消费所有可提供的服务，那么云环境通常更加便宜，因此，迁移它们自己数据的客户，更愿意维持这种灵活性。但是，新开发的应用程序没有所有这些遗留需求。它们更倾向于使用限制、而非试着把已有应用程序迁移到上面。

我觉得这种区别十分重要，我们愿意继续看到 AWS 和 GCP 发布的功能，在**灵活性**和**简单性**方面的区别。AWS 或许最适合迁移到云。GCP 或许更适合新的、基于容器的应用程序。这是一场持久战。


### 注释

* 注1：IOPS（Input/Output Operations Per Second）是一个用于电脑存储设备（如硬盘（HDD）、固态硬盘（SSD）或存储区域网络（SAN））性能测试的量测方式，可以视为是每秒的读写次数。和其他性能测试一様，存储设备制造商提出的IOPS不保证就是实际应用下的性能。[https://zh.wikipedia.org/wiki/IOPS](https://zh.wikipedia.org/wiki/IOPS)
