---
author: viviworld
comments: true
date: 2016-02-29 08:15:18+00:00
excerpt: Figma 没有使用路径（path）之类的工具，它基于矢量网络（vector networks）构建，这是我们的叫法，它和路径在后端兼容，但是提供了更多的灵活性和操控
layout: post
link: http://www.labazhou.net/2016/02/introducing-vector-networks/
slug: introducing-vector-networks
title: 小谈矢量网络
wordpress_id: 3125
categories:
- 设计
- 软件
tags:
- Figma
- 卷绕数
- 矢量网络
- 笔画
- 贝塞尔曲线
---


	
  * 原文地址（original source）：[https://medium.com/figma-design/introducing-vector-networks-3b877d2b864f](https://medium.com/figma-design/introducing-vector-networks-3b877d2b864f)

	
  * 原文作者（author）：Evan Wallace（[@evanwallace](https://twitter.com/evanwallace)）



* * *






在我合伙创建 [Figma](http://figma.com/) 之前，我做游戏开发，而非设计。我记得，当第一次邂逅现代矢量编辑工具时，我有多么吃惊。很多交互都被破坏了，你为什么不能直接操控一些东东呢？为什么有连接和未连接的东东只在特定情况下正常运行呢？[我们做到最好了吗](http://www.labazhou.net/2015/10/giving-the-users-what-they-want/)？

我们知道，今天使用的钢笔工具是[在 1987 年被首次推出](https://www.youtube.com/watch?v=xv3xl2B6yUs)的，从那以后，一直没有大的变化。当我们打算为 Figma 开发矢量编辑工具集时，我们决定尝试新工具。Figma 没有使用路径（path）之类的工具，它基于矢量网络（vector networks）构建，这是我们的叫法，它和路径在后端兼容，但是提供了更多的灵活性和操控：

[caption id="attachment_3133" align="alignnone" width="768"][![一个 action 中的矢量网络](http://www.labazhou.net/wp-content/uploads/2016/02/1-r1gof0PNNWj1kpQsIp8Ivw.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/1-r1gof0PNNWj1kpQsIp8Ivw.gif) 一个 action 中的矢量网络[/caption]

在我们首次实现矢量网络之后，我们做了一系列用户调研来优化概念。我们惊奇地发现，很多人甚至没有注意到矢量网络和路径之间的差别。这个工具刚好能够按照人们期望的方式使用。然而，当他们回过头，试着使用其它工具时，的确发现了差别所在。对于我们已经发现的亮点，观察并向我们求证，尤为耗时。


### 笔画（Strokes）


为了理解矢量网络，需要首先理解路径。一条路径是从一个端点到另一个端点的、一系列直线和曲线。你可以把一条路径看成笔式绘图仪之类的设备可能需要遵循的一连串指令。把笔头放下来，四处拖拽，再抬起来。

[caption id="attachment_3128" align="alignnone" width="1000"][![把路径看做笔式绘图仪](http://www.labazhou.net/wp-content/uploads/2016/02/1-fNbtOlHkI1E_BfrUaThFCQ.jpeg)](http://www.labazhou.net/wp-content/uploads/2016/02/1-fNbtOlHkI1E_BfrUaThFCQ.jpeg) 把路径看做笔式绘图仪(Photograph by Tomasz Sienicki)[/caption]

矢量网络改善了路径模型，支持任意两点之间的直线和曲线，不要求它们都汇合起来组成单一链。这有助于呈现最好的两个方面：纸上的哪个点容易被连接上；当绘制时，哪个几何图形更易于操纵。矢量网络使得分割和重新组合几何图形更加容易。可在任何地方、删除任何几何图形，也可在其它任何地方连接到任何几何图形。笔画的样式和连接样式在矢量网络里表现自然，哪怕某个点有着 3 条多的线。这不适应于路径的情形，因为把三条线连在单一点的路径，是不可能用到的。

[caption id="attachment_3126" align="alignnone" width="768"][![矢量网络支持标准的笔画和笔画连接样式](http://www.labazhou.net/wp-content/uploads/2016/02/1-PxChJlNJWli3Do9k2ppczg.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/1-PxChJlNJWli3Do9k2ppczg.gif) 矢量网络支持标准的笔画和笔画连接样式[/caption]


### 弯曲


对于现有的矢量网络编辑工具，我们有另一种直接操纵的改善方式。现在的矢量图基于[贝塞尔曲线](https://vimeo.com/106757336)[note]在数学的数值分析领域中，贝塞尔曲线（英语：Bézier curve）是电脑图形学中相当重要的参数曲线。更高维度的广泛化贝塞尔曲线就称作贝塞尔曲面，其中贝塞尔三角是一种特殊的实例。[https://zh.wikipedia.org/wiki/%E8%B2%9D%E8%8C%B2%E6%9B%B2%E7%B7%9A](https://zh.wikipedia.org/wiki/%E8%B2%9D%E8%8C%B2%E6%9B%B2%E7%B7%9A) 译者注：该词条页面中的动态插图有助于理解矢量图[/note]，它们具有两个被称为控制处理的额外点，一个点表示曲线本身开始的位置，另一个控制曲线的弯曲程度，有点儿像金属丝向磁铁弯曲的程度。改变曲线的形状，相当于拖拽空间中的控制处理，而非直接拖拉曲线。

我们最初尝试了一些功能强大的曲线类型，以提供更大的控制和形状功能，但最终发现，保持后向兼容与已有矢量数据才有意义。这也是路径和矢量网络均使用相同曲线类型的原因。除了拖拽和控制处理，Figma 的弯曲工具（对应于 OS X 上的 command 键）支持直接拖拽曲线。该编辑器将为你自动识别控制处理的摆放位置：

[caption id="attachment_3127" align="alignnone" width="768"][![弯曲工具随意拖拽曲线](http://www.labazhou.net/wp-content/uploads/2016/02/1-J7-SIlkTIeirqMBToahUUQ.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/1-J7-SIlkTIeirqMBToahUUQ.gif) 弯曲工具随意拖拽曲线[/caption]


### 填充


矢量引擎的另一项工作，就是用颜色填充曲线之间的区域。目前所有的矢量引擎用到了难以理解的概念，卷绕数[note]平面上的闭曲线关于某个点的卷绕数，是一个整数，它表示了曲线绕过该点的总次数。卷绕数与曲线的定向有关，如果曲线依顺时针方向绕过某个点，则卷绕数是负数。[https://zh.wikipedia.org/wiki/%E5%8D%B7%E7%BB%95%E6%95%B0](https://zh.wikipedia.org/wiki/%E5%8D%B7%E7%BB%95%E6%95%B0) [/note]，以此填充曲线之间的区域。它使用路径在既定位置卷绕的次数，以决定该位置在形状的内或外。总次数取决于你最初画的曲线的方向（顺时针或逆时针），和直觉尤为背离，因为没有哪一款矢量编辑器会真正向你展示曲线的行进方向。

[caption id="attachment_3131" align="alignnone" width="1500"][![按照非零环绕规则，填充取决于曲线方向](http://www.labazhou.net/wp-content/uploads/2016/02/1-Dyp1KVaHUQN1WtjYnrzs_w.png)](http://www.labazhou.net/wp-content/uploads/2016/02/1-Dyp1KVaHUQN1WtjYnrzs_w.png) 按照非零环绕规则，填充取决于曲线方向[/caption]

Figma 中的填充没有使用令人费解的概念，而是自动填充所有的封闭空间：

[caption id="attachment_3132" align="alignnone" width="768"][![封闭区域被自动填充](http://www.labazhou.net/wp-content/uploads/2016/02/1-2Oi7tJtWQlcRGf4Y2ps8rQ.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/1-2Oi7tJtWQlcRGf4Y2ps8rQ.gif) 封闭区域被自动填充[/caption]

如果你以后想增加孔洞，直接单击对应区域就行，无需担心曲线的方向：

[caption id="attachment_3129" align="alignnone" width="768"][![油漆桶工具（Paint Bucket tool）就是任何封闭区域的填充开关。](http://www.labazhou.net/wp-content/uploads/2016/02/1-_3EyhWTUL5C6aWuy5EqR1g.gif)](http://www.labazhou.net/wp-content/uploads/2016/02/1-_3EyhWTUL5C6aWuy5EqR1g.gif) 油漆桶工具（Paint Bucket tool）就是任何封闭区域的填充开关。[/caption]

让填充正常运行，成了最有难度的地方。我们尝试了一些不同的方式来表示填充，但是一直碰到问题，即：为了创建孔洞，而要求用户明确地操作负空间（negative space），往往让你难以理解。控制区域开关的工具成为最终可行的方案。


### 重新审视矢量编辑


重新发明一种与路径同等基础的东东，是十分艰难的。我们采用的解决方案貌似明显，但是在开发过程中却有很多死胡同和实存要素[note]英伽登所说的存在论则是对观念内容的先天研究，观念指关于存在－实体的观念，它由实存存在论、形式存在论、实质存在论组成。 其关键概念是“实存的要素”(Existential Moments)。这些要素决定着一个对象的存在方式，是实在的、观念的还是“纯粹意向性的”。 [http://ar.newsmth.net/thread-ad82fde0fd37d.html](http://ar.newsmth.net/thread-ad82fde0fd37d.html) [/note]，也有很多次，我们考虑在所有工作完成之后再考虑止损、以及只做路径。为了让矢量网络更完美，我们还有大量工作去做，但是我们对于矢量网络所呈现的方式感到满意，能够把它推到设计师面前，我们感到非常兴奋！
