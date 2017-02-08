---
author: viviworld
comments: true
date: 2016-03-09 13:24:40+00:00
excerpt: 程序员在填充 SQL 模板时，应该更加小心。应对 SQL 注入问题，只是需要在编程方面多加小心。很明显，这种方式算不上解决方案。
layout: post
link: http://www.labazhou.net/2016/03/solving-the-problem-of-sql-injection-requires-another-approach/
slug: solving-the-problem-of-sql-injection-requires-another-approach
title: 解决 SQL 注入的另类方法
wordpress_id: 3158
categories:
- 编程
tags:
- Brainfuck
- SQL
- 中缀表示法
- 欧拉表示法
- 波兰表示法
---


	
  * 原文地址（original source）：[https://bitcoinrevolt.wordpress.com/2016/03/08/solving-the-problem-of-sql-injection-requires-another-approach/](https://bitcoinrevolt.wordpress.com/2016/03/08/solving-the-problem-of-sql-injection-requires-another-approach/)

	
  * 原文作者（author）：eriksank





* * *





### 问题解读


我觉得，这个问题每年带来的成本可以高达数十亿美元了。本文就来谈谈，假定我们有如下 SQL 模板语句：

    
    select * from T where f1 = ‘{value1}’ and f2 = {value2}


现在我们需要根据用户输入值填充该语句：

    
    value1=hello
    value2=5


我们得到了下面的 SQL 语句，我们再提交给数据库：

    
    select * from T where f1=’hello’ and f2=5


问题在于，攻击者可以构造如下的用户输入值：

    
    value1=anything’ or 1=1 or f1=’whatever
    value2=5


拼接好的最终语句就变成了：

    
    select * from T where f1=’anything’ or 1=1 or f1=’whatever’ and f2=5


攻击者成功地改变了模板语句的语义。这种问题不单单发生在 SQL 上，还出现在通常使用模板的任何语言上，比如 HTML 和 shell 脚本。


### 常规解决方案的说明


SQL 是具备任意性和一致性的公理，token 和派生规则构成其公理化基础。要注意的一个词语是「任意性」。与 SQL 等价的公理化数不胜数。对于这种任意等价的表示，每一条合法的语句都能被准确地映射到 SQL 里的合法语句，其它语言亦然。在这种任意等价表示中，如果某语句是不合法的，那么它在 SQL 里也是不合法的。攻击者不可能构造出可以满足任何可能的、任意与 SQL 等价的规则。


#### 策略1：根据不同的派生规则，用另一种语法扩展模板语句




##### 例子1：前缀语言


SQL 使用中缀表示法[note]中缀表示法（或中缀记法）是一个通用的算术或逻辑公式表示方法， 操作符是以中缀形式处于操作数的中间（例：3 + 4）。与前缀表达式（例：+ 3 4）或后缀表达式（例：3 4 +）相比，中缀表达式不容易被电脑解析，但仍被许多程序语言使用，因为它符合人们的普遍用法。[https://zh.wikipedia.org/wiki/%E4%B8%AD%E7%BC%80%E8%A1%A8%E7%A4%BA%E6%B3%95](https://zh.wikipedia.org/wiki/%E4%B8%AD%E7%BC%80%E8%A1%A8%E7%A4%BA%E6%B3%95) [/note]。中缀表示法等价于 lisp 风格的前缀表示法[note]波兰表示法（Polish notation，或波兰记法），是一种逻辑、算术和代数表示方法，其特点是操作符置于操作数的前面，因此也称做前缀表示法。[https://zh.wikipedia.org/wiki/%E6%B3%A2%E5%85%B0%E8%A1%A8%E7%A4%BA%E6%B3%95](https://zh.wikipedia.org/wiki/%E6%B3%A2%E5%85%B0%E8%A1%A8%E7%A4%BA%E6%B3%95) [/note]。中缀与前缀：

    
    a OP1 b OP2 c <=> (OP1 a (OP2 b c))


a、b、c 是标识符或值，OP1、OP2 是操作符或功能。

前缀表示法的示例语句：

    
    (select * T (and (= f1  ‘{value1}’) (= f2 {value2})))


该语句是等价的。它们在语义上属于外延。自动把 SQL 的中缀表示法转换成前缀表示法或其它表示法，都不算问题了。然而，攻击者的注入在前缀语法方面就是不合法的：

    
    (select * T (and (= f1  ‘anything’ or 1=1 or a=’whatever’) (= f2 5)))


语法错误。攻击者想要的是：

    
    (select * T (or (= f1 ‘anything’) (or (=1 1) (and (= a ‘whatever’) (= f2 5)))))


这是不同的。攻击者的注入不能输出合法的前缀语言。


##### 例子2：欧拉表示法


另一个替代方法将数得着欧拉表示法了。从中缀表示法到欧拉：

    
    a OP1 b OP2 c <=> OP1(a,OP2(b,c))


例子中的语句：

    
    select( *,T,and(=(f1,'{value1}’),=(f2,{value2})))


而注入的语句将出现语法错误：

    
    select( *,T,and(=(f1,’anything’ or 1=1 or a=’whatever’),=(f2,5)))


攻击者本来是想写成：

    
    select( *,T,or(=(f1,’anything’,or(=(1,1),and(=(a,’whatever’),=(f2,5))))))


攻击者正在做错误的事情。他的注入根本就没有注意到所选的任意标记法。


##### 例子3：对象标记法（object notation）


还有一种替代方法，对象标记法。从前缀表示法到对象：

    
    a OP1 b OP2 c <=> a.OP1(b).OP2(c)


例子的代码：

    
    T.where(f1.=(‘{value1}’).and(f2.=({value2})).select(*)


注入再一次折戟于语法：

    
    T.where(f1.=(‘anything’ or 1=1 or a=’whatever’).and(f2.=5)).select(*)


我不再提供正确答案了，读者可以当做练习，看看攻击者应该写成什么样子。


#### 策略2：为 SQL 选择其它任意 token


keyword 常常是一门语言里的任意 token。重要的是它们在派生规则里的位置、而非它们的任意体现。你总是可以用其它 keyword 替换现有 keyword，并且来回转换。举个例子，我们可以将下面 SQL 语句中的 keyword 转换成我们姑且称为「任意的 brainfuck」：

    
    {“select“:”iph0ohKi”, “*“:”ieZoh4xa”, “from“:”aeZi5uja”, “where“:”OoJ4aX4n”, “=“:”eeQu2Zad”, “(“:”eiD5aera”,”)“:”Soo2uach”, “or“:”Ocaig5Es”}


为了论证起见，我们将把操作数映射为 半任意的结构化序列：

    
    T <=> @phai1Oa6@T@
    hello <=> @phai1Oa6@hello@


phai1Oa6 是任意选取的字符序列。对于当前情形，例子：

    
    select * from T where f1 = ‘{value1}’ and f2 = {value2}


变成了：

    
    iph0ohKi ieZoh4xa aeZi5uja @phai1Oa6@T@ OoJ4aX4n @phai1Oa6@f1@ eeQu2Zad ‘{value1}’ @phai1Oa6@and@ @phai1Oa6@f2@ eeQu2Zad {value2}


这是合法的、任意的 brainfuck 语言。经过注入之后，我们得到了：

    
    iph0ohKi ieZoh4xa aeZi5uja @phai1Oa6@T@ OoJ4aX4n @phai1Oa6@f1@ eeQu2Zad ‘anything‘ or 1=1 or a=’whatever’ @phai1Oa6@and@ @phai1Oa6@f2@ eeQu2Zad 5


你可以看到，它包含的 token 有 'or' 和 '='，它们在任意的 brainfuck 语言中是不合法的。我们的语法说，你必须这样使用：

    
    or <=> Ocaig5Es
    = <=> eeQu2Zad


这些 token 也不是操作数，因为它们将只能被视作：

    
    or <=> @phai1Oa6@or@
    = <=> @phai1Oa6@=@


换句话说，注入之后的语句就变得不合法、也不可用了。


#### 策略3：验证不变量


你数数下面模板语句例子中的 token 有几个？

    
    [1] select [2] * [3] from [4] T [5] where [6] f1 [7] = [8] ‘{value1}’ [9] and [10] f2 [11] = [12] {value2}


12 个。模板填充之后，总数必须仍然为 12，但是我们却看到了攻击者所引发的结果：

    
    [1] select [2] * [3] from [4] T [5] where [6] f1 [7] = [8] ‘anything’ [9] or [10] 1 [11] = [12] 1 [13] or [14] a [15] = [16] ‘whatever’ [17] and [18] f2 [19] = [20] 5


现在有 20 个 token 。违反这种不变量，就暴露了有问题的地方。同样适用于相同语句的表示，除了任意的、brainfuck 语言。模板的填充根本不可能导致 token 数量的变化。

事实上，你可以试着使用其它不变量，并在填充之后进行验证。攻击者必须和它们保持一致。


### 结论


有些人提倡，程序员在填充 SQL 模板时，应该更加小心。应对 SQL 注入问题，只是需要在编程方面多加小心。很明显，这种方式算不上解决方案。人们仍然在校验用户输入值方面出现错误，最终接受了带有恶意的用户输入值。换句话说，单凭我们所有人更努力地工作，是无法根本解决这种问题的。

真正的解决方案在于，[SQL 语句](http://www.labazhou.net/2015/08/beginners-guide-to-sql/)本身的任意性，并要求所有现存不变量都符合任意的等价结构的规则。无需程序员的干预，就能自动完成。

攻击者不得不符合一种未知的、任意的 brainfuck 语法的规则。想要符合一组未知的规则，将是难以解决的问题。因此，攻击者通常无法得手。
