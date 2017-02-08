---
author: viviworld
comments: true
date: 2014-01-17 05:59:39+00:00
layout: post
link: http://www.labazhou.net/2014/01/are-passwords-stored-in-memory-safe/
slug: are-passwords-stored-in-memory-safe
title: 密码存在内存里安全吗？
wordpress_id: 191
categories:
- 安全
tags:
- cpu
- dma
- hibernation
- linux
- ram
- windows
- 内存
---

问：

我刚刚意识到在任何语言里，当你把密码保存到一个变量里，它将以文本的形式存放在内存里。

我认为操作系统将发挥作用，禁止进程相互访问彼此分配的内存。但是我也认为这多少有些不是靠谱的做法。因此我想知道这是不是真正安全的，是否有更加安全的存储密码的方法，来确保外部进程不能访问它们。

我没有指定操作系统或者语言，因为我的问题是非常普遍的。这更像是一个计算机常识问题、而不是具体的问题。

答：

你点到了一个痛处……

从历史上讲，计算机是大型机，允许许多不同的用户在相同的物理机上建立会话和进程。类Unix系统（比如Linux），还有VMS和其相关亲戚（和包括所有NT、和此后的2000，XP, Vista, 7, 8…… 的Windows家族，），设计之初是为了支持大型机模型。这样，硬件提供权限级别。操作系统最重要的部分是内核，它以最高权限级别运行（是的，我知道对于虚拟化有些微妙），并管理权限级别。应用程序以较低级别运行，内核禁止它读、写其他应用程序的内存。应用程序按页（page，通常4或8KB）从内核获得RAM。如果一个应用程序试图访问另一个应用程序的页，内核就会阻止它，并且受到严重惩罚（"segmentation fault", "general protection fault"）。

当一个应用程序不再需要页（特别是在该应用程序还存在的时候）时，内核会控制该页，可能会分给另一个应用程序。现代操作系统在使用这些页的时候，会“清空”（blank）该页，这里的“清空”指“用零填充”，从而阻止数据从一个进程泄露到另一个进程。注意，Windows 95/98/Millenium没有清空页，泄露有时候会出现……但是，这些操作系统是针对单台机器的单个用户的。

当然，有很多绕过内核的方法：应用程序有一些方式来获取“足够的权限”（没有上面权限高的、同种类型权限）。Linux系统有[ptrace](http://linux.die.net/man/2/ptrace)()，内核允许一个进程通过ptrace()读写另一个进程的内存，此时这两个进程需要运行在同一个用户ID下，或者运行ptrace()进程的是“root”用户。相似的功能也存在于Windows。

底线是RAM里的密码没有操作系统允许的安全。按照定义，在进程内存里存储一些机密数据有个前提，就是你相信操作系统不会把数据给第三方。操作系统是你的朋友，因为如果它是敌人，那么你就失去了一切。

有意思的环节到了。既然操作系统负责进程的隔离，还是有很多人试着找到了穿透防护的办法。这里是他们找到的有趣的办法……

应用程序看到的“RAM”不是真正需要的“内存”。内核是假象的管理者，分配实际不存在的页。假象是通过通过磁盘上的专用空间来交换RAM内容，磁盘上的空闲空间是相当大的；这被称为[虚拟内存](http://en.wikipedia.org/wiki/Virtual_memory)。应用程序无需关心，因为内核会根据需要取回这些页（当然，磁盘比RAM慢很多）。不幸的后果是，一些数据，特别是位于RAM中的数据，使得RAM变成 数据被覆盖之前的 物理载体。尤其是当电源被切断时，它仍然呆在那里。当坏家伙搞走这台机器，随后就能获取数据了。或者机器退役后在eBay卖出，系统管理员忘记了彻底清除磁盘内容。

Linux提供了一个[mlock](http://linux.die.net/man/2/mlock)()的系统调用来阻止内核把某些特定的页发送到swap区。既然锁住RAM里的页能够大大减少其他进程获取RAM资源的情况，那么你需要一些权限（还是root）来使用这个功能。

恼人的地方在于，追踪真正保存在RAM里的密码必然是不太容易的。做为一个程序员，你是通过编程语言提供的抽象方式来访问RAM的。尤其是使用[垃圾回收](http://en.wikipedia.org/wiki/Garbage_collection_%28computer_science%29)的编程语言会明显地复制RAM里的对象（因为它对很多GC算法有帮助）。大多数编程语言就是这样被影响的（像Java, C#/.NET, Javascript, PHP……清单几乎没有尽头）。

[hibernation](http://en.wikipedia.org/wiki/Hibernation_%28computing%29)似乎为了复仇带来了同样的问题。本来，hibernation必须把整个RAM写回磁盘------包括mlock()涉及的页，甚至CPU注册的内容。为了避免hibernation泄露数据，你不得不采取像加密整个磁盘之类的猛烈的措施------这自然意味着只要你唤醒机器，就可以键入解除锁定的密码。

大型机模型假定它能够运行一些彼此友好的进程，且保持极好的和平和隔离。现代硬件加剧了这一难度。当两个进程运行在同一个CPU时，它们共享资源，包括缓存内存；内存访问比缓存之外的任何地方都要快，但是缓存大小十分有限。这催生了一个进程使用来自于另一个进程的[恢复密钥](http://www.daemonology.net/papers/htt.pdf)。使用其他类缓存的资源变体也有了，比如CPU里的分支预测（branch prediction）。随着对高度机密的、集中于密钥的研究，它能够真正应用于任何数据。

还有种情况，显卡能够做[直接内存存取](http://en.wikipedia.org/wiki/Direct_memory_access)（Direct Memory Access，DMA）【注1】。DMA是否不会被滥用去读写其他进程的内存 取决于 文档不全的硬件、闭源的驱动程序和内核是如何协作确保合适的访问控制的。我不会为此赌我一件上次穿过的衬衣的……

结论：是的，当你在RAM存放密码时，你是相信操作系统会确保机密的。是的，这个任务很艰巨，甚至在现代系统上是不可能的。如果你的数据高度机密，你就不应该使用大型机模型，也不要允许潜在友好的实体在你的机器上运行代码。（顺便说一句，这意味着托管的虚拟主机和云计算根本是不安全的。如果你对安全比较在意，请使用专有硬件。）

原文地址：[http://security.stackexchange.com/questions/29019/are-passwords-stored-in-memory-safe](http://security.stackexchange.com/questions/29019/are-passwords-stored-in-memory-safe)
注1：DMA：[http://zh.wikipedia.org/zh-cn/%E7%9B%B4%E6%8E%A5%E8%A8%98%E6%86%B6%E9%AB%94%E5%AD%98%E5%8F%96](http://zh.wikipedia.org/zh-cn/%E7%9B%B4%E6%8E%A5%E8%A8%98%E6%86%B6%E9%AB%94%E5%AD%98%E5%8F%96)
