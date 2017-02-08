---
author: viviworld
comments: true
date: 2016-01-21 23:51:05+00:00
excerpt: 今天我们要讨论 CSS 中的一些有用的技巧。混合模式、渐变边框、currentColor、单选、复选按钮的样式、@Supports等
layout: post
link: http://www.labazhou.net/2016/01/22-essential-css-recipes/
slug: 22-essential-css-recipes
title: CSS 的 22 个必备技巧
wordpress_id: 3025
categories:
- 编程
tags:
- chrome
- css
- currentColor
- firefox
- safari
- unicode
- 视口
---


	
  * 原文地址（original source）：[http://ipestov.com/22-essential-css-recipes/](http://ipestov.com/22-essential-css-recipes/)

	
  * 作者（author）： Ilya Pestov（[@ipestov](https://twitter.com/ipestov)）





* * *



大家好！今天我们要[讨论 CSS 中的一些有用的技巧](http://www.labazhou.net/2015/10/things-to-avoid-when-writing-css/)。开始吧……


### 混合模式


[![CSS 混合模式](http://www.labazhou.net/wp-content/uploads/2016/01/blend-600x181.jpg)](http://www.labazhou.net/wp-content/uploads/2016/01/blend.jpg)

目前，Firefox 和 Safari 开始支持混合模式，就像 Photoshop 一样。Chrome 和 Opera 也支持，只是有些差异。看例子：

你可以创建不同的样式。下面是示例代码：

    
    .blend {
        background: #fff;
    }
    .blend img {
        mix-blend-mode: darken; 
    }


[在线尝试一下 CSS 混合模式和滤镜](http://ilyashubin.github.io/FilterBlend/)！


### 渐变边框


[![CSS 渐变边框](http://www.labazhou.net/wp-content/uploads/2016/01/gradients-600x199.jpg)](http://www.labazhou.net/wp-content/uploads/2016/01/gradients.jpg)

如今，你可以在边框里使用渐变了。非常简单，只要用较小的 z-index 设置伪元素就可以了：

    
    .box {
      margin: 80px 30px;
      width: 200px;
      height: 200px;
      position: relative;
      background: #fff;
      float: left;
    }
    .box:before {
          content: '';
          z-index: -1;
          position: absolute;
          width: 220px;
          height: 220px;
          top: -10px;
          left: -10px;
          background-image: linear-gradient(90deg, yellow, gold);
    }


你可以在[这里](https://jsfiddle.net/4qypuono/)找到所有例子。使用 background-clip 和 background-origin [也可以做到](http://codepen.io/anon/pen/jEOGJe)。在美好未来的某一天，border-image 属性也会被所有浏览器支持，实现方法如下：

    
    .box {
        border-image: linear-gradient(to bottom, #000000 0%, #FFFFFF 100%); 
        border-image-slice: 1; /* set internal offset */
    }




### z-index 支持过渡


[![627e4e0da85e419fa53ce6c0552caec5](http://www.labazhou.net/wp-content/uploads/2016/01/627e4e0da85e419fa53ce6c0552caec5.gif)](http://www.labazhou.net/wp-content/uploads/2016/01/627e4e0da85e419fa53ce6c0552caec5.gif)

你可能不知道，但是 z-index 的确支持过渡了！它不会在每一步去改变值，因此你会认为，它不会产生过渡。但是，它真的支持！这里有个[不错的例子](http://zomigi.com/demo/z-index_transition.html)。


### currentColor


我们可以用它检测当前颜色值，这样我们就不必多次定义它。

当和 SVG icon 一起使用时最有帮助，它随着父级元素颜色的改变而改变。通常，我们的做法如下：

    
    .button {
      color: black;
    }
    .button:hover {
      color: red;
    }
    .button:active {
      color: green;
    }
    
    .button svg {
      fill: black;
    }
    .button:hover svg {
      fill: red;
    }
    .button:active svg {
      fill: green;
    }


不过，我们可以用 currentColor 实现：

    
    svg {  
      fill: currentColor;
    }
    
    .button {
      color: black;
      border: 1px solid currentColor;
    }
    .button:hover {
      color: red;
    }
    .button:active {
      color: green;
    }


关于伪元素的代码：

    
    a {  
      color: #000;
    }
    a:hover {  
      color: #333;
    }
    a:active {  
      color: #666;
    }
    
    a:after,  
    a:hover:after,  
    a:active:after {  
      background: currentColor;
      ...
    }




### object-fit


你还记得有时候你需要为图片设置 background-size 吗，因为它会解决很多问题。现在你可以使用 object-fit，webkit 支持它，很快也会被 Firefox 支持。

    
    .image__contain {
      object-fit: contain; 
    } 
    .image__fill {
      object-fit: fill; 
    }
    .image__cover {
      object-fit: cover; 
    }
    .image__scale-down {
      object-fit: scale-down;
    }


[![CSS object-fit](http://www.labazhou.net/wp-content/uploads/2016/01/825f90c6d7be4043bfe465616e85570b.jpg)](http://www.labazhou.net/wp-content/uploads/2016/01/825f90c6d7be4043bfe465616e85570b.jpg)

[示例](http://codepen.io/CSSKing/pen/XJEZeG)。


### 单选、复选按钮的样式


我们不使用任何图片，来给某个复选按钮设置样式：

    
     <input type="checkbox" id="check" name="check" />
     <label for="check">Checkbox</label>



    
    input[type=checkbox] {display: none;}
    
    input[type=checkbox] + label:before {  
        content: "";
        border: 1px solid #000;
        font-size: 11px;    
        line-height: 10px;
        margin: 0 5px 0 0;
        height: 10px;
        width: 10px;
        text-align: center;
        vertical-align: middle;
    }
    
    input[type=checkbox]:checked + label:before {  
        content: "\2713";
    }


[![CSS 单选、复选按钮的样式](http://www.labazhou.net/wp-content/uploads/2016/01/3c49d0bd93ce48fc97bc2cea812158db.jpg)](http://www.labazhou.net/wp-content/uploads/2016/01/3c49d0bd93ce48fc97bc2cea812158db.jpg)

你可以看到，伪元素和伪选择器 :checked（IE9+）表现正常。在上面的示例代码中，我们隐藏了原始的复选按钮，用我们自己的代替。当被勾选时，我们通过 content 显示一个 Unicode 字符。


<blockquote>CSS 和 HTML 用到的 Unicode 字符不同。在 CSS 中，开头是反斜杠，然后跟上十六进制的字符，而在 HTML 中，它是十进制的，形如 &#10003; 。</blockquote>


我们还可以给复选按钮加上动画：

    
    input[type=checkbox] + label:before {  
        content: "\2713";
        color: transparent;
        transition: color ease .3s;
    }
    input[type=checkbox]:checked + label:before {  
        color: #000;
    }


下面是单选按钮的动画：

    
    input[type=radio] + label:before {  
        content: "\26AB";
        border: 1px solid #000;
        border-radius: 50%;
        font-size: 0;    
        transition: font-size ease .3s;
    }
    input[type=radio]:checked + label:before {  
        font-size: 10px;    
    }


[![CSS 单选、复选按钮的样式-动画](http://www.labazhou.net/wp-content/uploads/2016/01/0b47f606c78746b0bbe14f50567f4222.gif)](http://www.labazhou.net/wp-content/uploads/2016/01/0b47f606c78746b0bbe14f50567f4222.gif)

你可以在[这里](http://unicode-table.com/)找到完整的 Unicode 清单，试着[鼓捣下代码](http://codepen.io/anon/pen/CdzwB)吧。


### CSS 中的 counter


不是每个人都知道 counter 可以在 CSS 中设置：

    
    <ol class="list">  
        <li>a</li>
        <li>b</li>
        <li>c</li>
    </ol>



    
    .list {
        counter-reset: i; //reset conunter
    }
    .list > li {
        counter-increment: i; //counter ID
    }
    .list li:after {
        content: "[" counter(i) "]"; //print the result
    }


我们在 counter-reset 属性中定义了一个任意 ID 和初始值（默认为 0）。你可以在 counter-increment 中设置另一个数字，它定义了计数器的步长。

比如，counter-increment: i 2 将只显示偶数。


### CSS 高级计数器


你还可以累加被用户选中的复选按钮：

    
    <div class="languages">  
      <input id="c" type="checkbox"><label for="c">C</label>
      <input id="C++" type="checkbox"><label for="C++">C++</label>
      <input id="C#" type="checkbox"><label for="C#">C#</label>
      <input id="Java" type="checkbox"><label for="Java">Java</label>
      <input id="JavaScript" type="checkbox"><label for="JavaScript">JavaScript</label>
      <input id="PHP" type="checkbox"><label for="PHP">PHP</label>
      <input id="Python" type="checkbox"><label for="Python">Python</label>
      <input id="Ruby" type="checkbox"><label for="Ruby">Ruby</label>
    </div>  
    <p class="total">  
      Total selected:
    </p>



    
    .languages {
      counter-reset: characters;
    }
    input:checked {  
      counter-increment: characters;
    }
    .total:after {
      content: counter(characters);
    }


我们累加 input:checked 的值，并显示出来，[参看例子](http://codepen.io/CSSKing/pen/QwMLzd)。

[![CSS 高级 counter](http://www.labazhou.net/wp-content/uploads/2016/01/021ceed507c24b66a8a8c1438800ebd3.gif)](http://www.labazhou.net/wp-content/uploads/2016/01/021ceed507c24b66a8a8c1438800ebd3.gif)

你还能开发出一个小型计算器呢：

    
    <div class="numbers">  
      <input id="one" type="checkbox"><label for="one">1</label>
      <input id="two" type="checkbox"><label for="two">2</label>
      <input id="three" type="checkbox"><label for="three">3</label>
      <input id="four" type="checkbox"><label for="four">4</label>
      <input id="five" type="checkbox"><label for="five">5</label>
      <input id="one-hundred" type="checkbox"><label for="one-hundred">100</label>
    </div>  
    <p class="sum">  
      Sum 
    </p>



    
    .numbers {
      counter-reset: sum;
    }
    
    #one:checked { counter-increment: sum 1; }
    #two:checked { counter-increment: sum 2; }
    #three:checked { counter-increment: sum 3; }
    #four:checked { counter-increment: sum 4; }
    #five:checked { counter-increment: sum 5; }
    #one-hundred:checked { counter-increment: sum 100; }
    
    .sum::after {
      content: '= ' counter(sum);
    }


运行原理一样。这里有在线 [demo](http://codepen.io/CSSKing/pen/vEeMey) 和[文章](http://codersblock.com/blog/fun-times-with-css-counters/)。

[![css 小型计算器](http://www.labazhou.net/wp-content/uploads/2016/01/b432dc730aa3454797029c45bafbf5a1.gif)](http://www.labazhou.net/wp-content/uploads/2016/01/b432dc730aa3454797029c45bafbf5a1.gif)


### 没有图片的菜单图标


你还记得需要使用「三明治」图标的频率吗？

[![「三明治」图标](http://www.labazhou.net/wp-content/uploads/2016/01/1e63d058f36040a7977bde88dea61c6e.jpg)](http://www.labazhou.net/wp-content/uploads/2016/01/1e63d058f36040a7977bde88dea61c6e.jpg)

至少有 3 种方法来绘制：


#### 1.shadow



    
     .shadow-icon {
       position: relative;
       }
       .shadow-icon:after {
         content: "";
         position: absolute;
         left: 0;
         top: -50px;
         height: 100%;
         width: 100%;
         box-shadow: 0 5px 0 #000, 0 15px 0 #fff, 0 25px 0 #000, 0 35px 0 #fff, 0 45px 0 #000;
         }




#### 2.渐变



    
    .gradient-icon {
        background: linear-gradient(to bottom, #000 0%, #000 20%, transparent 20%, transparent 40%, #000 40%, #000 60%, transparent 60%, transparent 80%, #000 80%, #000 100%);
    }




#### 3.UTF-8


你可以只粘贴这个标准符号：☰ （Unicode: U+2630, HTML: &#9776;）。你可以调整其颜色或尺寸，因此它没有其它方法灵活。

[看例子](http://codepen.io/CSSKing/pen/cozBq)。

你还可以使用带有伪元素的 SVG、图标字体或边框。


### @Supports


CSS 有一些称之为 supports 的新表达式。如你所见，它可以检测浏览器是否支持所需选项。不是所有浏览器都支持它，但是你可将其用作简单的检查。

    
    @supports (display: flex) {
        div { display: flex; }
    }
    
    /*You can check prefixes*/
    @supports (display: -webkit-flex) or (display: -moz-flex) or (display: flex) {
        section {
            display: -webkit-flex;
            display: -moz-flex;
            display: flex;
            float: none;
        }
    }




### visibility: visible


把 visibility: visible 的区块设置为 visibility: hidden，你对此有何看法？

    
    .hidden {
      visibility: hidden;
    }
    .hidden .visible {
      visibility: visible;
    }


你或许认为所有元素都将被隐藏，实际上，除了子元素显示之外，父元素将隐藏所有元素。请看 [demo](http://codepen.io/CSSKing/pen/lxBfk)。


### position: sticky


[![CSS position: sticky](http://www.labazhou.net/wp-content/uploads/2016/01/f1c9b59f550146fe900f5a785037106f.gif)](http://www.labazhou.net/wp-content/uploads/2016/01/f1c9b59f550146fe900f5a785037106f.gif)

我们已经发现了一个新特性，现在你可以创建 "sticky" 的区块了。它们和 fixed 区块表现一样，但是不会隐藏另一个区块。[你最好看下这里](http://codepen.io/CSSKing/pen/yyMGPJ)。目前，只有 Mozilla 和 Safari 支持，但是你可以用如下方式实现：

    
    .sticky {
      position: static;
      position: sticky;
      top: 0px;
    }


我们将会在支持的浏览器里得到一个 sticky 区块，而在其它浏览器里得到一个普通区块。特别有利于移动网站，因为你需要创建一个可移动区块且不影响其它元素。


### 新尺寸


最近，世界上找到了一种新方式，用来描述不同物体的尺寸。比如：



	
  * vw（视口宽度）：视口宽度，单位：1/100。

	
  * vh（视口高度）：视口高度，单位：1/100。

	
  * vmin 和 vmax：二者都是相对于视口的宽度或高度，但前者总是相对于大的那个，后者总是相对于小的那个。


有意思的是，大部分现代浏览器都对它们支持很好，你可以随意使用。我们为什么需要它们呢？因为它们让所有的尺寸更简单了。你不必定义父级元素尺寸的百分比或其它东东。看个例子：

    
    .some-text {
        font-size: 100vh;
        line-height: 100vh;
    }


[![视口尺寸的单位](http://www.labazhou.net/wp-content/uploads/2016/01/242036191864f7959df87c8dfeb30f36.gif)](http://www.labazhou.net/wp-content/uploads/2016/01/242036191864f7959df87c8dfeb30f36.gif)

或者，你在屏幕中央放置一个美丽的弹窗：

    
    .blackSquare {
        background: black;
        position: fixed;
        height: 50vh;
        width: 50vw;
        left: 25vw;
        top: 25vh;
    }


这貌似是很酷的解决方案。请参考来自 Codepen 的[例子](http://codepen.io/CrocoDillon/pen/fBJxu)。

在使用这个特性时，存在一些劣势：



	
  * IE9 应该使用 vm 而不是 vmin。

	
  * iOS7 上的 vh，存在一些 bug。

	
  * vmax 还不被完全支持。




### 文本修饰


我们用数行代码就能改变选中文本的颜色：

    
    *::selection {
        color: #fff;
        background: #000;
    }
    *::-moz-selection {    
        /*Only Firefox still needs a prefix*/
        color: #fff;
        background: #000;
    }


除了定义选中文本的颜色，还能定义阴影和背景。


### 触摸设备上的块滚动


如果页面存在一些内部滚动的区块，那么除了添加 overflow: scroll / auto，还要添加这行代码：

    
    -webkit-overflow-scrolling: touch;


问题在于，移动设备浏览器对于 overflow: scroll 属性支持不够好，会滚动整个页面而不是期望的区块。-webkit-overflow-scrolling 修复了这个问题。你可以将其添加到你自己的项目中，看看效果。


### 使用硬件加速


有时候你的动画能够减慢用户电脑。为了阻止这种情况，你可以针对特定区块使用加速：

    
    .block {
        transform: translatez(0);
    }


你可能感受不到变化，但是浏览器理解，这个元素应该被看做三维，然后开启加速。如果针对 will-change 属性的具体设计，没有提供正常支持，这种方法就不太建议了。


### 类命名用 Unicode 字符


你可以在如下代码看到使用 Unicode 字符做类名：

    
    .❤ {
        ...
    }
    .☢ {
        ...
    }
    .☭ {
        ...
    }
    .★ {
        ...
    }
    .☯ {
        ...
    }


只是开个玩笑。尽量不要在大项目中使用，因为不是每一台电脑都一定支持 UTF-8。


### 百分比表示的垂直边距


事实上，垂直缩进是根据父元素的宽度、而非高度计算出来的。我们创建两个区块：

    
    <div class="parent">  
        <div class="child"></div>
    </div>



    
    .parent {
        height: 400px;
        width: 200px;
    }
    .child {
        height: 50%;
        padding-top: 25%;
        padding-bottom: 25%;
        width: 100%;
    }


理论上，应该根据高度来填充父元素的，不过，我们看看结果：

[![CSS百分比表示的垂直边距](http://www.labazhou.net/wp-content/uploads/2016/01/e5571ec5936d482c93f0187c97b2dee2.jpg)](http://www.labazhou.net/wp-content/uploads/2016/01/e5571ec5936d482c93f0187c97b2dee2.jpg)

你应该记住，百分比是根据父元素的宽度计算出来的。


### Firefox 下的 button 边距


Firefox 还没有自身方法来计算 button 的边距。貌似奇怪，但是你可以手动添加。

[![Firefox 下的 button 边距](http://www.labazhou.net/wp-content/uploads/2016/01/e137ef627a479a0a71402de85b906738.jpg)](http://www.labazhou.net/wp-content/uploads/2016/01/e137ef627a479a0a71402de85b906738.jpg)

还可以这样修复：

    
    button::-moz-focus-inner,  
    input[type="reset"]::-moz-focus-inner,  
    input[type="button"]::-moz-focus-inner,  
    input[type="submit"]::-moz-focus-inner {  
        border: none;
        padding:0;
    }




### Color + Border = Border-Color


不是每个人都明白，除了为任何对象定义文本颜色，还可以定义其边框颜色：

    
    input[type="text"] {  
        color: red;
        border: 1px solid;
    }


[![CSS：Color + Border = Border-Color](http://www.labazhou.net/wp-content/uploads/2016/01/a913e9c061034f2aa749ee3f52fb760f.gif)](http://www.labazhou.net/wp-content/uploads/2016/01/a913e9c061034f2aa749ee3f52fb760f.gif)


### 流金岁月


如果你仍然不得不支持 IE7 等类似情况，那么，你可以用一个笑脸来定义其 hack：

[![css 的类名](http://www.labazhou.net/wp-content/uploads/2016/01/css-smile.png)](http://www.labazhou.net/wp-content/uploads/2016/01/css-smile.png)

很酷，对吧？
