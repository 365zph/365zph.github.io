---
author: viviworld
comments: true
date: 2015-01-20 03:24:55+00:00
layout: post
link: http://www.labazhou.net/2015/01/four-valid-ways-to-write-degrees-fahrenheit-in-html/
slug: four-valid-ways-to-write-degrees-fahrenheit-in-html
title: 用HTML书写华氏温度的4种有效方式
wordpress_id: 1553
categories:
- 编程
tags:
- HTML
- 排版
- 温度
- 阅读
---

原文地址（original source）：[http://robb.weblaws.org/2015/01/19/degrees-of-freedom-four-valid-ways-to-write-degrees-fahrenheit-in-html/](http://robb.weblaws.org/2015/01/19/degrees-of-freedom-four-valid-ways-to-write-degrees-fahrenheit-in-html/)

我在我的创业公司[食品安全评分网站](http://eaternet.io/)上班，编写过滤导入文本的代码，比如下面的文本：


<blockquote>DELI DISPLAY COOLER HOLDING CREAM CAKE AT 44.6F BUT LOWER CORNER OF UNIT HOLDING FOODS @ 39F</blockquote>


我们决定在尽可能不改变内容的前提下，使其[易于阅读](http://www.labazhou.net/2014/08/how-we-read/)。因此，过滤后的文本应该有优化的大小写、标点符号和排版：

[![用HTML书写华氏温度的4种有效方式](http://www.labazhou.net/wp-content/uploads/2015/01/degrees-fahrenheit-text.png)](http://www.labazhou.net/wp-content/uploads/2015/01/degrees-fahrenheit-text.png)

有意思的地方在于温度。首先，我翻了翻样式指导，因为我意识到我甚至不知道温度应该怎样加注标点；比如，内部应该有空格吗？[美国国家地理学会的样式手册](http://stylemanual.ngs.org/)非常适合我。它规定在最终数字和度数符号之间[没有空格](http://stylemanual.ngs.org/home/T/temperatures)：


<blockquote>F是华氏温度的缩写：32°F（没有空格，也没有标点符号）</blockquote>


我随后找到了四种不同的、用HTML书写度数的有效方式，它们都产生了同样的结果：
<table border="1" >

<tr >
策略
代码
截图
</tr>

<tbody >
<tr >

<td >华氏温度度数的HTML实体
</td>

<td >#&8457;
</td>

<td >![1](http://www.labazhou.net/wp-content/uploads/2015/01/degrees-fahrenheit-4.png)
</td>
</tr>
<tr >

<td >F带有普通F的度数符号的HTML实体
</td>

<td >&deg;F
</td>

<td >![2](http://www.labazhou.net/wp-content/uploads/2015/01/degrees-fahrenheit-4.png)
</td>
</tr>
<tr >

<td >华氏温度字符的Unicode度数
</td>

<td >℉
</td>

<td >![3](https://dogweather.files.wordpress.com/2015/01/3.png?w=216)
</td>
</tr>
<tr >

<td >带有普通F的Unicode度数符号
</td>

<td >°F
</td>

<td >![4](https://dogweather.files.wordpress.com/2015/01/4.png?w=213)
</td>
</tr>
</tbody>
</table>
注意到第四种选择看着最优，且最容易在HTML代码里识别到。这正是我想要的。
