---
author: viviworld
comments: true
date: 2014-01-25 02:55:31+00:00
layout: post
link: http://www.labazhou.net/2014/01/chrome-is-the-new-c-runtime/
slug: chrome-is-the-new-c-runtime
title: Chrome是新的C运行时
wordpress_id: 232
categories:
- 编程
tags:
- chrome
- chromium
- gyp
- ios
- windows
- xcode
---

跨平台app开发比以前更重要了。10年前，当你需要一个客户端应用程序时，只需要快速打开Visual Studio，根本不需要其他东西。随着 App化 成为Android、iOS、Windows和Mac上的主流，一名开发者又需要做什么呢？

web app有些时候是好的解决方案（除了有个叫做IE的小细节！）。

但是当你需要跨平台的、内建代码的功能和性能，该如何呢？你是一个由小团队和紧迫的deadline组成的创业公司吗？

好吧，在MobileSpan【注1】我们已经度过了两年，我们想分享一些方法。

我们选择集成[Chromium](http://www.chromium.org/Home)源代码来构建应用程序。

Chromium是Google Chrome的开源库。我的合伙创始人和我都是Chrome团队的前google员工，因此我们非常熟悉它，它对我们也是一种容易的选择。但是，你不必为了利用Chrome丰富的代码库而去花4年时间呆在google。


### 但是……我们不开发浏览器！


对我而言，为什么Chrome源代码对跨平台app开发非常有用呢？我不是要开发一个浏览器……

实际上，Chrome已经不仅仅是一个浏览器了。Chrome代码在性能、可靠性、跨平台兼容PC和iOS及Android设备上，做了大量的调优。

除此之外，Chrome团队已经为很多低端平台做了跨平台抽象。我们用这些代码做为我们构建业务逻辑的核心API，只用一点点努力就可以做出大量的跨平台app。

更重要的是------Chrome代码已经久经沙场，以及数亿级的安装量。当你想致力于公司的业务逻辑，而不是调试平台问题时，这是有很大不同的。

基本上，你能够像下面的结构图来组织你的代码，你只需写应用程序逻辑，让Chromium做繁重的工作。

[![chrome开发平台](http://www.labazhou.net/wp-content/uploads/2014/01/chrome-dev-platform.png)](http://www.labazhou.net/wp-content/uploads/2014/01/chrome-dev-platform.png)


### Chrome为什么如此优秀？


考虑到现代浏览器的部分，Chrome包括高性能、跨平台的实现：



	
  * Concurrency handling

	
  * Compression

	
  * Encryption

	
  * Certificate handling

	
  * Low-level socket interfaces

	
  * High-level protocol implementations like HTTP, HTTPS, FTP)

	
  * DNS resolution

	
  * Proxy handling

	
  * Complex disk caching

	
  * Cookie handling

	
  * ……还有更多


它让你做的工作是，充分利用这些优点来建立一个单一的、跨平台应用程序层。

Chrome代码还有其他意料不到的、更高级的好东东，比如：

	
  * Chrome远程桌面；

	
  * 完全的P2P（TURN，STUN,等）栈（Chrome远程桌面有用到）；

	
  * XMPP客户端（用到了Chrome Sync 和Chrome远程桌面）；




### 从哪里开始？




#### 第一件事：生成项目的合适工具


启动项目的第一步是生成你的平台下的合适项目文件（Visual Studio, Xcode等）。Chromium使用[GYP](https://code.google.com/p/gyp)以一种平台独立的方式来声明指定文件和项目设置。我强烈推荐一开始就用GYP，它为每个平台（Visual Studio解决方案和项目文件，XCode项目文件和Android .mk文件）生成项目文件。另外，GYP强大的依赖选项允许 各种Chromium项目文件所需的编译器和连接器设置 自动导入依赖于它们的项目中去。这大大减少了你自己编译的痛苦，以及当你更新checkout出来的Chrome源代码所带来的问题。


#### 大量的helper防止你的项目变得乱糟糟


一旦你开始程序部分，你会发现你需要各种helper类库，包括字符串操作、并发处理、同步、线程池、消息循环、日志、文件操作、定时器、共享内存管理等等。

如果你发现你开始写通用helper类或库，首先应该搜索一下Chromium源代码。找到你需要的类的机会是非常大的，并且它们经历了很好的彻底的单元测试。

Chromium源代码（位于src/base）的基本库提供了非常宽泛的跨平台工具，覆盖了上面提到的地方以及更多的地方。还有一些特定平台的helper，比如Windows Registry或iOS Keychain。

在MobileSpan，从Chromium源代码搜寻它们需要的helper已经变成了开发者的游戏。


#### 网络栈【注2】？


如果你不是开发Windows 3.1下的app，你还是有机会和某种服务器打交道。这可能涉及到简单的HTTP或HTTPS API调用，或底层socket调用等等。

Chromium的net库（位于src/net）是你的朋友。你能够找到一全套跨平台的HTTP和HTTPS栈，cookie处理代码，缓存，TCP和UDP套接字和套接字池，SSL认证处理，DNS解决方案，代理服务器解决方案……好的，你有了非常多的与网络相关的想法。


#### 加密


需要处理公钥私钥，加密数据存储隐私吗？crypto库（位于src/crypto）有时候是一个极好的跨平台库，它几乎能确保你找到加密或密钥管理例程。现在你对源代码的组织有了大概的了解。


#### XMPP, P2P, Protocol Buffers 等等


你在web浏览器里是不会期待找到这些东西的，但是Chromium包含了一个基于libjingle（位于src/jingle和src/remoting）构建的、可扩展的XMPP和P2P客户端库。如果你在代码里使用protocol buffers【注3】，那么GYP已经支持 .proto文件 了。仅仅把 .proto文件 加到你的GYP文件，它就会完成构建protoc编译器和生成wrapper code。它甚至对iOS项目也管用。


#### 测试


你的代码仅仅和你写的单元测试一样，对吧？虽然Chrome这部分不太严格，但是Chrome代码库中的GTest和GMock库部分提供了非常棒的框架，这用来写单元测试和mock你的C++类。所有的Chrome测试都用这些框架完成，因此你有一个能够激发灵感的、庞大的示例代码库。

GYP甚至为你的测试生成了平台适应的容器。例如，在iOS，它会自动生成一个iOS app来容纳你的测试，因此你可以在模拟器里运行。你仅仅在cc文件里写测试，然后把它们加到一个GYP文件，加上需要的依赖，你就有了跨平台单元测试。

在MobileSpan，我们实现了基于Chrome构建的、具备跨平台库的核心业务逻辑。有了这些基础库，我们为每个平台设计了一套UI。把我们的app应用到一个新平台 意味着 在新平台构建UI层，然后和跨平台客户端库绑在一起。


### 总结：集成


如果我听起来像一个Chrome粉丝的话，那是因为我本身就是。我们拥抱Chromium两年多了，我们发现它做为一个开发平台真的很好，节约了难以计算的工时。它允许我们真正重复使用写得很好的代码，更重要的是，在一些客户端平台做了良好测试的代码，我们得以集中精力开发一个多平台运行效果一致的、健壮的产品。


### 我将来要写的文章要点


本文只是Chrome源代码做为开发平台的肤浅说明。在下一篇文章我应该写什么呢？

包括下面的要点：



	
  * 深入特定的库，比如Network，Crypto等

	
  * 保持最新的Chromium源代码

	
  * 如何理智地fork（知道什么时候fork特定的代码）

	
  * checkout Chromium源代码的进程

	
  * 跨平台UI开发的更多细节


你鼓捣过Chrome的代码库或者用它构建一个酷酷的产品吗？在评论里告诉我们吧。

原文地址：[https://www.mobilespan.com/content/chrome-is-the-new-c-runtime](https://www.mobilespan.com/content/chrome-is-the-new-c-runtime)
注1：MobileSpan：指本文作者所在的公司。
注2：network stack：[http://www.chromium.org/developers/design-documents/network-stack](http://www.chromium.org/developers/design-documents/network-stack)
注3：Google Protocol Buffer 的使用和原理：[http://www.ibm.com/developerworks/cn/linux/l-cn-gpb/](http://www.ibm.com/developerworks/cn/linux/l-cn-gpb/)
