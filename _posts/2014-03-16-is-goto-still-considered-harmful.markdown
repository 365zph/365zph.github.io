---
author: viviworld
comments: true
date: 2014-03-16 23:21:42+00:00
layout: post
link: http://www.labazhou.net/2014/03/is-goto-still-considered-harmful/
slug: is-goto-still-considered-harmful
title: goto仍然被视作有害的？
wordpress_id: 434
categories:
- 编程
tags:
- apple
- bug
- GCC
- github
- goto
---

Apple最近的安全漏洞被追踪到一个伪造的goto。但是它仍然没有解决关于其用法的争论。

如果你是程序员，阅读了最近关于Apple安全传输（他们的SSL/TLS实现）的严重安全漏洞的辩论，那么你或许注意到了Apple源代码错误发生的地方有些奇怪。它充满了goto语句。

Apple已经开源了安全传输代码。我们不知道这在被找到的bug中发挥着什么作用，但是一旦修复被公布，源代码的可获得性使得找到特定bug变得容易了。

这个有错误的[C语言文件](http://twimgs.com/ddj/images/article/2014/0314/AppleGoToError.html)行数长达1970行，它包含了47个goto语句。更原初的语言，比如老的BASIC实现，就依赖goto，因为没有goto，他们就缺乏足够的控制结构。在CS101，你被告知goto是一种丑陋的东东，它打破了逻辑控制流。像C这样的功能强大的语言包含了goto，仅仅用在当没有goto逻辑就变复杂的状况下，做为一种避免准备。这或许就是发生在有bug的Apple函数SSLVerifySignedServerKeyExchange：

    
    static OSStatus SSLVerifySignedServerKeyExchange(…)
    {
      …
     
        if ((err = SSLFreeBuffer(&hashCtx)) != 0)
            goto fail;
     
        if ((err = ReadyHash(&SSLHashSHA1, &hashCtx)) != 0)
            goto fail;
        if ((err = SSLHashSHA1.update(&hashCtx, &clientRandom)) != 0)
            goto fail;
        if ((err = SSLHashSHA1.update(&hashCtx, &serverRandom)) != 0)
            goto fail;
        if ((err = SSLHashSHA1.update(&hashCtx, &signedParams)) != 0)
            goto fail;
            goto fail;
        if ((err = SSLHashSHA1.final(&hashCtx, &hashOut)) != 0)
            goto fail;
     
      …
     
    fail:
        SSLFreeBuffer(&signedHashes);
        SSLFreeBuffer(&hashCtx);
        return err;
    }


我从该函数删除了很多代码以提高可读性。错误就在两个连续的行 goto fail; 。我根本没有说这个程序是使用了goto才导致错误的。很明显，错误是一个简单的、粗心的编辑错误，该错误在语法上仍然正确，因此没有产生错误。你能够轻松地不用goto来实现同样的功能。

但是goto怎么了？像Apple这种认真的公司的程序员实际上是如此频繁地使用goto吗？好像是这样。在Github搜索“goto fail”会返回数百万条结果。

为了对这些程序员公平起见，在C里，goto和其他少数的禁忌语句，像switch结构里的break，没有明显的区别。这样，小心使用goto实际上能够让代码更干净。另一个通常被给的、把goto做为一种代码手动优化的方式的理由是缺乏论据的。

我问了Jeff Law和Jason Merrill关于他们对goto的看法，两人都在Red Hat，是GCC指导委员会的成员。Jason Merrill很快驳斥了关于程序员能够或应该为性能手动优化代码的任何观点：

“正如Donald Knuth在其论文 [用goto语句进行结构化编程](http://cs.sjsu.edu/~mak/CS185C/KnuthStructuredProgrammingGoTo.pdf) 所说的，‘……过早优化是所有罪恶的根源。’为了清晰而编程更加重要，因为你知道在你的代码里，什么是危险的区域，尤其是现代优化器和性能测评工具要比在1974年写论文的Donald Knuth所能获得的任何东西要强大得多；他的关于使用goto的有用优化的大部分例子对于现代编译器来说，都是例行转换。”

Jason Merrill认为Apple代码的goto是为了清晰：“通常，本地级别的微优化不是我们推荐的，除非验证了代码是危险的情况，这时候微优化才被证明是有价值的。大多数情况下，清晰是胜过微优化的。

我怀疑，GCC和大部分现代编译器在内部把源代码转换成了一系列的基本块（最大组的连续[insns](http://gcc.gnu.org/onlinedocs/gccint/Insns.html)，它可以被流控制的变化或标签结束。）。对于大多数优化阶段，块之间的所有控制转换都被控制流日程代表了。这意味着结构良好的代码 与 充满goto的意大利面条式的代码 对于编译器是没有区别的。最终，控制流的所有变化都被转换成流程图的边界，编译器把它们优化成了最好的扩展可能。在编译器里相对晚了些，流程图里的边界明确地再一次变成了控制流指令的象征。”

Jeff Law也认为Apple使用goto是“像是更加得体地清洁，而不是优化。你应该在很多代码里看到同样的风格，在从函数返回之前cleanup（尤其是释放内存，在这个代码片段里就是这种情况）是必须的。C++对这种cleanup风格有着巨大的更好的支持。GCC的C编译器也支持‘cleanup’属性，它把相似功能带给了C代码”。

因此禁止goto不是完全理性的。看看SSLVerifySignedServerKeyExchange函数------你怎样不用goto来组织？它实际上更清晰吗？在那个程序里，goto仅仅用来跳出长长的流逻辑，而不是循环。从while或for循环中间跳出来对于goto或许是另外一种情况，因为你可能更难证实那些循环结构的正确性。

即使有时候明白了使用goto，要学到的更重要的教训是关于最近二十年里语言变得有多完美。【对我而言，这里学到的教训是在提交代码之前能够静态地检查你的代码。 ------Ed】编译器优化的优势，和摩尔定律一起，允许我们使用比C好得多的、管理cleanup和划分逻辑的语言。不是Apple应当用Python重写安全传输，而是每个人应当仔细考虑C固有的危险，既然它的性能必要性不是那个样子。

原文地址：[http://www.drdobbs.com/architecture-and-design/is-goto-still-considered-harmful/240166595](http://www.drdobbs.com/architecture-and-design/is-goto-still-considered-harmful/240166595)
