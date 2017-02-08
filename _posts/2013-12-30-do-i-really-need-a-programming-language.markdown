---
author: viviworld
comments: true
date: 2013-12-30 00:15:10+00:00
layout: post
link: http://www.labazhou.net/2013/12/do-i-really-need-a-programming-language/
slug: do-i-really-need-a-programming-language
title: 我真的需要一种编程语言吗？
wordpress_id: 103
categories:
- 编程
tags:
- lisp
- 程序员
- 编程
- 黑客
---

老板想让我在产品里增加按季节打折的功能，做为一个灰常棒的黑客，我选择C来写必要的逻辑：

    
       if (price > 100) {
            return 10;
        }
        else {
            return 5;
        }


但是等一下，我们的IT部门不会批准这种低级的东东。它需要用VB.NET实现……

    
        If price > 100 Then
            Return 10
        Else
            Return 5
        End If


我的高智商对这种状况表示愤怒，很快我明白这两种语言只是中间步骤，真正的目标是把它们转换成可执行的指令。

语法分析器会从我的代码中搜寻语言设计师所认为重要的符号。C分析器寻找花括号，VB.NET则寻找关键词。

这些符号还可以配置到代表用来执行的逻辑的语法树：

    
                       (  if  )
                        /  |  \
                       /   |   \
                ( > ) ( 10 ) ( 5 )
                 / \
                /   \
        ( price ) ( 100 )


然后我乐了：首先有我想表达的逻辑，其次不管我用什么语言，结果总是相同的语法树。

因此，我真的需要一种编程语言吗？或许我仅仅用树来编码就可以一起避免那些问题。要是有人可以把树缩减成数行代码该多好……

如果我以圆括号限定的列表来表示一个父节点和其子节点，会是什么样子？用P1代表父节点，C1和C2是它的子节点，最终它们表示为 （P1 C1 C2），也可以加入递归。

然后我这样写代码：

    
        (if (> price 100)
            10
            5)


然后，我意识到我正在用LISP。

原文地址：[http://ayudasystems.tumblr.com/post/71327185334/do-i-really-need-a-programming-language](http://ayudasystems.tumblr.com/post/71327185334/do-i-really-need-a-programming-language)
