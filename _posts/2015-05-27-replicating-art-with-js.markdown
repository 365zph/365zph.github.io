---
author: viviworld
comments: true
date: 2015-05-27 02:32:04+00:00
excerpt: 它貌似能够用 JavaScript 复制。我花了一些时间观察，决定使用最简单的方法------带有少许改动的、某种正弦函数。对于资源库，我打算用平常的
  JS。
layout: post
link: http://www.labazhou.net/2015/05/replicating-art-with-js/
slug: replicating-art-with-js
title: 用 JS 复制艺术
wordpress_id: 2106
categories:
- 编程
tags:
- hit-testing
- javascript
---


	
  * 原文地址（original source）：[http://jsart.co/11/replicating-art-with-js/](http://jsart.co/11/replicating-art-with-js/)

	
  * 作者（author）：[https://twitter.com/kodisha](https://twitter.com/kodisha)





* * *



今天我发现了一副美丽的绘画，经过一番研究，我找到了名字和作者。

[![jsart_infinite_dots-756x1024](http://www.labazhou.net/wp-content/uploads/2015/05/jsart_infinite_dots-756x1024-756x1024.png)](http://www.labazhou.net/wp-content/uploads/2015/05/jsart_infinite_dots-756x1024.png)



	
  * **YAYOI KUSAMA**

	
  * Infinity-Dots [HOFS], 2014

	
  * Acrylic on canvas

	
  * 130.3 x 97 cm


（顺便说一句，可以浏览[相同作品集的其它作品](http://ocula.com/art-galleries/victoria-miro-gallery/artists/yayoi-kusama/)）

看起来真的不错，更重要的是，它貌似能够用 [JavaScript](http://www.labazhou.net/2014/01/7-javascript-tips-to-make-you-feel-smarter/) 复制。

我花了一些时间观察，决定使用最简单的方法------带有少许改动的、某种正弦函数。对于资源库，我打算用平常的 JS。


### 细节


首先，让我们放大、看下图片本身的细节。

[![Screen-Shot-2015-05-25-at-4.53.57-PM](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-25-at-4.53.57-PM.png)](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-25-at-4.53.57-PM.png)

我们能够注意到：



	
  * 稍微扭曲的圆

	
  * 它们有边界

	
  * 越小的圆，扭曲得越多


本图或许给你留下这是一副“简单的”复制品，但不尽然。看下所有这些点，它们从来没有重叠。

甚至它看起来有一些像正弦波的主风格，它更像是艺术家用大量点做的纵向条纹，然后只是耐心地填充了其余部分（我的看法，或许我完全错了）。我做了少量测试。我现在明白了，为了达到几近完美的复制，我将不得不引入某种 hit-test【注1】，或者保留事先画好的点的位置。

我不想这样做，我想做一些类似于我能做的事情，只使用简单命令和纯粹的 JS。


### 结果


开干，我尝试了一些简单方法，下面是结果：

[caption id="attachment_2110" align="alignnone" width="443"][![刚开始，没有经验的尝试，用了简单的正弦函数。](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-25-at-8.14.56-PM-e1432602099240.png)](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-25-at-8.14.56-PM-e1432602099240.png) 刚开始，没有经验的尝试，用了简单的正弦函数。[/caption]

很明显这行不通，我尝试不覆盖圆，但是空隙太大了：

[![Screen-Shot-2015-05-26-at-1.37.05-AM](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-26-at-1.37.05-AM.png)](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-26-at-1.37.05-AM.png)

在接下来的截图里，我对空间做了尝试，只是当心不让圆重叠：

[caption id="attachment_2112" align="alignnone" width="604"][![更好的结果，但是仍然离原作品相差甚远。](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-26-at-2.11.09-AM-e1432602645865-1024x697-1024x697.png)](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-26-at-2.11.09-AM-e1432602645865-1024x697.png) 更好的结果，但是仍然离原作品相差甚远。[/caption]

最后，加上一点点扭曲，变成了：

[caption id="attachment_2115" align="alignnone" width="604"][![Screen-Shot-2015-05-26-at-2.51.26-AM-1024x706](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-26-at-2.51.26-AM-1024x706-1024x706.png)](http://www.labazhou.net/wp-content/uploads/2015/05/Screen-Shot-2015-05-26-at-2.51.26-AM-1024x706.png) 不太完美，但足以接近。全是代码的功劳。[/caption]

这是真正有趣的试验，即使我做不到在细节上做好复制，但是你能够用几行代码就能搞出某些真正好看的图像，这会给人留下深刻的印象。在我们的例子中，下面是输出最终图片的所有代码：

    
    var canvas = document.getElementById('replica');
        var ctx = canvas.getContext('2d');
    
        var circle = function(radius, x, y) {
    
            ctx.fillStyle = '#b50024';
            ctx.strokeStyle = '#771522';
            ctx.beginPath();
            ctx.arc(x, y, radius, 0, Math.PI * 2);
            ctx.stroke();
            ctx.fill();
            ctx.closePath();
    
        };
    
        var lastX = 0;
        var fix = 0;
        var width = 500;
        var height = 677;
        for (var i = 0; i < width; i += 2) {
    
            var x = i / (width / 150);
            var radius = 6 / (3 * (Math.exp(Math.sin(x))));
    
            lastX = lastX + radius + radius + 3;
    
            for (var j = 4; j < height; j += 2) {
    
                var randOffset = ( 0.7 * radius) * Math.random();
                var deviation = j / (height / 10 * (2 *  height / j ));
                var dOffset = Math.cos(j/(height/4)) * ((3.4 + (1.4 * (j/height)))
                        * Math.exp(Math.cos(deviation))) * (1.5 + (2 * ((3.2 * (i / width)) )
                        * Math.exp(Math.sin(deviation))));
    
                if (j % 12 === 0) {
                    if (radius >= 3.4) {
                        circle(radius, lastX - dOffset, j + randOffset);
                    }
    
                } else {
                    if (radius < (6 * Math.random())) {
                        circle(radius, lastX - dOffset, j + randOffset);
    
                    }
                }
            }
        }


本例的完整源代码，还可以点击在线 [demo](http://jsart.co/content/art-replica/)。

这是一次不同凡响的尝试。下次我将挑选一些不同的（但是同样有挑战性的）的例子，并尽量做同样的事情。

**更新：**

用户 blackle 在评论里留下了更好的实现，她的结果更加完美！

[![orKSxcH](http://www.labazhou.net/wp-content/uploads/2015/05/orKSxcH-1024x727.jpg)](http://www.labazhou.net/wp-content/uploads/2015/05/orKSxcH.jpg)

太棒了！你可以访问她的 [demo](http://www.blackle-mori.com/stuff/replicate-art-with-js/)。



* * *






	
  * 注1：In computer graphics programming, hit-testing (hit detection, picking, or pick correlation) is the process of determining whether a user-controlled cursor (such as a mouse cursor or touch-point on a touch-screen interface) intersects a given graphical object (such as a shape, line, or curve) drawn on the screen. [http://en.wikipedia.org/wiki/Hit-testing](http://en.wikipedia.org/wiki/Hit-testing)


