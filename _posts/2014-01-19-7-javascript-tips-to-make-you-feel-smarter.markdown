---
author: viviworld
comments: true
date: 2014-01-19 09:13:49+00:00
layout: post
link: http://www.labazhou.net/2014/01/7-javascript-tips-to-make-you-feel-smarter/
slug: 7-javascript-tips-to-make-you-feel-smarter
title: 7种JavaScript技巧使你更聪明
wordpress_id: 200
categories:
- 编程
tags:
- javascript
- jquery
- prototype
- zalgo
---

## 让其他人恶心你




### 1.总是颠倒逻辑


让我们从一个小优化开始，目的是为了使得非常简单的操作看起来复杂些。

    
    if (x && y) { … } // bad
    if (!(!x || !y)) { … } // good




### 2.在你的变量名字里使用扩展的unicode字符


编译好的软件一旦发布成产品，它必须是一个黑盒。这对JavaScript来说是不可能的。如果有人想彻底搞懂你的JavaScript代码，他们仅仅需要打开浏览器控制台、加一些断点就能看到对象的状态。

对象属性的名称，改用非规则字符串，来阻碍他们的进展。

    
    var foo = function (person) {
    // stuff happens
    
    // perhaps a breakpoint is added here
    
    // or they attempt to log the object
    console.log(person);
    }
    var person = {};
    person[‘\t’] = ‘Nicholas’;
    person[‘\b’] = ‘Male’;
    person[‘\r’] = ‘Programmer’;
    person[‘\f’] = ‘Lover’;


当你试图去查看变量时，会看到如下情景：

[![t1](http://www.labazhou.net/wp-content/uploads/2014/01/t1.png)](http://www.labazhou.net/wp-content/uploads/2014/01/t1.png)

当你试着在控制台输出log时，会看到：

[![tu2](http://www.labazhou.net/wp-content/uploads/2014/01/tu2.png)](http://www.labazhou.net/wp-content/uploads/2014/01/tu2.png)

用同样的技巧把[Zalgo](http://nl.wikipedia.org/wiki/Zalgo)文本合并到你的代码

[![tu3](http://www.labazhou.net/wp-content/uploads/2014/01/tu3.png)](http://www.labazhou.net/wp-content/uploads/2014/01/tu3.png)


### 3.补习你的三角学


在我从大学退学以前，老师常常说数学和编程是多么地紧密相关。根据经验，我发现不是这回事儿。事实上，我开始觉得，老师是为了骗学生来上课。好吧，是时候好好利用学生欠下的严重债务了。

不要用

    
    if (!val) { … }


而要用

    
    Math.floor(.5 + ((Math.cos(val)*.5)))


仅当val是2pi的整数倍时，它才会返回true。你甚至不需担心val不是一个数字。真没有关系。实际上，也不再有关系了。


### 4.利用JavaScript的仁慈


有多少次你在一个if语句该用等号操作符的时候而意外地使用了赋值操作符？这是非常恼人的，因为它不会报错、仅仅把程序带到不可意料的境地。

    
    function foo (x) {
    if (x=true) {
    // no matter what value is
    // passed in for x, this
    // will always execute
    }
    }
    foo(false);


看你代码的人看到这里，会想当然地认为这是你代码的错误。但是，我们没有错误，因此这个人就会受到惩罚。“修复”它将带来不希望的后果。


### 5.不用十进制


用八进制初始化一个数字很容易被误认为是十进制；仅仅在第一个数字使用‘0’。

    
    var i = 27 // 27
    var j = 027 // 23


你的同事或许责怪你正犯下不可饶恕的错误，但是你要坚持八进制更快，因为所有的位本来就是以8为一组的。


### 6.空白不是毛病；除了它有用的情况


每个人都知道JavaScript里的空白和分号不过是多余的，是吗？错！不要这样想当然。

    
    (function () {
    var a=1,
    b=2,
    c=3
    d=4,
    e=5,
    f=6;
    }());
    console.log(d,e,f); // 4,5,6


上面的例子，我们“少”了一个逗号。如果代码都在一行，我们不会犯错。但是既然不在一行，编译器将在 c=3 之后附加一个分号。这导致d，e，f声明为全局变量。现在可以随时使用这些变量了，包括分离的文件。

再一次，如果有人注意到这种情况，并试着修改，这将潜在地破坏了所有不相关的代码部分，而不是规范代码，他们很可能只有回退修改了，足以证明你更聪明。


### 7.富有创新


编程就是创新，创新就是模仿别人。不要害怕偷代码和想法，或者责备其他人偷你的。比如，你知道jQuery是完全模仿Prototype的吗？是的。

Nicholas Ortenzio【注1】在练习倒背字母表，以防万一。

原文地址：[https://medium.com/cool-code-pal/a1286881aed7](https://medium.com/cool-code-pal/a1286881aed7)
注1：Nicholas Ortenzio 就是本文的作者，最后一句话的意思应该是：很少有人倒背字母表，如果你倒背了，你会显得比其他人聪明。
