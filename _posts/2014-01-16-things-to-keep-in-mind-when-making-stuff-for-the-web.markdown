---
author: viviworld
comments: true
date: 2014-01-16 07:50:50+00:00
layout: post
link: http://www.labazhou.net/2014/01/things-to-keep-in-mind-when-making-stuff-for-the-web/
slug: things-to-keep-in-mind-when-making-stuff-for-the-web
title: web开发收集
wordpress_id: 186
categories:
- 编程
- 网络
tags:
- aws
- javascript
---

下面是在做web项目时试着牢记于心的、动态更新的清单。有些是逻辑上的，有些是个人喜好。

我尽量遵守这里面的规则。


### Design/UI





	
  * 保持持久和灵活的最好方法就是不要一开始就放太多东西。你不得不固定到你最先想要断开的长度。

	
  * 确保你想分享的app具有唯一URL的状态正确。有必要时再用hash。假定某人会从地址栏直接复制URL，而不是从你的“Share this！”插件。

	
  * 每页有超过两种字体时，你需要一个非常好的理由。

	
  * 不要使用小尺寸字体，对于正文文本的行间距要大方些。

	
  * 不要放置很小的点击目标。假定某人是用指头去碰某个图标，而不是鼠标。

	
  * 冗余是一种有用的设计技巧。标签+图标，颜色+宽度，等。

	
  * 拥抱垂直方向的滚动，不要打破它。基于滚动的动画是恼人的。禁止把web变成一本立体书【注1】。

	
  * 不要重度依赖悬停效果来提高趣味性。即使大部分人有鼠标，要求你的用户继续一个寻宝游戏【注2】是让人讨厌的。

	
  * 如果input需要是数字，那么使用“number”类型的input，这样移动设备能够显示合适的键盘。

	
  * 使用XHR请求的下载指示器，即使它们总是很快。你从来不知道用户那边如何慢，或如何断开的。用户应当知道下载是否出问题了。

	
  * 移动设备上的浏览器，滚动条经常不好辨认。检查页面在哪些地方切断，然后确保把 “下面还有更多”设计得明显些。

	
  * 不要打破浏览器zoom（想全屏的地图是一个例外）。

	
  * 不要太依赖声音（包括画外音）。很多用户处于公共场合，即使他们有头戴式耳机，要求他们取下来或戴上去也是比较麻烦的。

	
  * 文字就是文字，不要在在图片上出现文字。

	
  * 确保可点击的东西就是可点击的。它们应当使用 cursor: pointer，具有hover状态，如果它们是文本，它们应该和其他文字保持距离。

	
  * 如果可能请避免lightbox。

	
  * 不要让你的基于位置的应用 必须有 用户的位置。要准备好他们说不。通常，如果你有一个非常个人化的应用，考虑一下，你能给不想谈论个人隐私的人们展示什么有趣的东西。

	
  * 不要马上给人20个相同有趣的东西。在他们疲劳之前，集中一个在前面展示。

	
  * Small multiples reflow easily.（译者注：词句不好翻译）

	
  * web设计不是比比看谁有最少的空的像素。留白非常有利于吸引用户注意力。不要挤到一起。

	
  * 限制文本块最大宽度到某个值，比如900px。太宽就不容易浏览了。

	
  * 不要使用Flash。




### 图像/图表





	
  * 假定人们不喜欢看说明。

	
  * 把legend【注3】尽可能放在它们描述的图表旁边。

	
  * 给x轴、y轴加说明，并显示单位。

	
  * 早些使用线上数据。如果用不了，就使用历史数据或其它有代表性的数据。肉眼观察随机测试数据会给你带来困惑。

	
  * 当显示随时间变化的数据时，要用面积图或线图，除非你有不用的理由。

	
  * 当比较多个类别的数据时，要用条形图或柱状图，除非你有不用的理由。

	
  * 当比较一组数据的两个变量时，要用散点图，除非你有不用的理由。

	
  * 当显示一个分布时，要用柱状图或分布曲线。

	
  * 不要用3D图表。

	
  * 不要随意处置y轴，当心数值范围。

	
  * 不要期望人们能够辨别出气泡尺寸或透明度在数字范围的微小差异。

	
  * 不要在范畴规划（categorical scehma）上使用多于3到4种的颜色。如果你有更多的范畴，你很可能需要使用 用颜色来区分 之外的方式。

	
  * 配色的时候要考虑到色盲用户。在选取色值范围时，可以使用[Colorbrewer](http://colorbrewer2.org/)之类的东西。

	
  * 幻灯显示或列表要带上“查看全部”选项。更好的方式是，刚开始就带上“查看全部”而不是需要太多的点击。

	
  * 刚开始用渐变是有趣的，然而通常让人讨厌。如果你不是在渐变里显示一个持续的对象，就不要用。

	
  * 使用[Leaflet](http://leafletjs.com/)来处理地图。

	
  * 不要制作人口地图。

	
  * 世界地图考虑使用罗宾森投影（Robinson projection，注4）。美国地图考虑使用亚尔勃斯投影（ Albers projection，注5）。不管用什么地图，要留意你选择投影方式的失真情况。




### HTML/JavaScript





	
  * 指定charset，可能是utf-8.

	
  * 指定doctype，可能是（我不知道有使用任何其他类型的好理由）

	
  * 包含描述的社会化媒体标签。

	
  * 把站点script脚本放到body的后面。

	
  * 如果有些东西每次都借助JavaScript用相同的方式来渲染，考虑静态化。

	
  * 合并、精简script脚本，以最小化页面大小和请求次数。

	
  * 为资源使用解释性的子文件夹（css/, js/, images/)。

	
  * 在JS类库文件里包含版本号。

	
  * 缓存重复使用的jQuery和D3选择器：



    
    $("div#sidebar").html("Don't do");
    $("div#sidebar").html("this");
    
    var $sidebar = $("div#sidebar");
    
    $sidebar.html("Do this");
    $sidebar.html("instead");





	
  * 驼峰式与小写？Tab与空格？连字符与下划线？选择一种方式并保持一致性 要比你选择哪一种 重要得多。

	
  * 不要热衷持续更新。数据真的需要秒级的更新频率吗？

	
  * 不要在生产环境里面留下控制台debug信息。




### 数据处理





	
  * 逐步提炼、转换你的原始数据。使得这一过程可重复。如有可能，使用Makefiles或shell脚本。

	
  * 给数据文件取个有意义的名字。geocoded-20131206.tsv, 而不是 data.tsv。

	
  * 在最终展示的时候要连接到数据源。解释你的方法论，特别要解释清楚你分析的局限和不足。

	
  * 如果可以的话，不要使用太复杂的正则表达式。使用多步操作，你会省去很多麻烦。

	
  * 调整并简化 地理数据文件（geodata），保留合适的空白。世界地图不需要精确到英寸的数据。

	
  * 以JSON或TSV格式存储数据。

	
  * 尽可能使用简单的文本文件，如果不是有必要，就避免数据库开销。

	
  * 确信你知道数据集代表无法获得的值的方式。它可能是一个空格，一个破折号、一个星号，或其他符号。一些地方使用999或99.999代表无法取得的数字。

	
  * 缓存你删除的页面，当你误操作时，你不至于从头开始。

	
  * 当心C的4种情况：字符编码，大小写，弯引号和空格。



    
    "Côte d'Ivoire" //damn it
    "Cote d’Ivoire" //crap
    "cote d'ivoire" //whoops
    "Côte d'Ivoire " //what the?
    "Ivory Coast" //COME ON




### 站点配置





	
  * 尽可能静态化。如果不能静态化，用[Varnish](https://www.varnish-cache.org/)之类的软件缓存。

	
  * 不要随意改变 [Cool URL](http://www.w3.org/Provider/Style/URI.html)。

	
  * URL要短、解释型、小写。

	
  * 使用http://domain.com/， 而不是 www.domain.com，但是要配置 www. 跳转。

	
  * 清空POST数据，使其不能通过刷新重新提交。

	
  * 尽量不要直接依赖外部API。使用一个中间层，当API挂掉的时候，你的网站仅仅是数据更新不及时，而不是打不开了。

	
  * 试想你的页面仅仅是用户打开的众多tab中的一个，请使用短的、描述性的页面title和favicon。

	
  * 尽可能压缩图片，使用合适的格式，你不需要真正丰富的、无损的、体积巨大的小icon和缩略图。




### 服务器配置





	
  * 不要在脚本文件存放凭据，要用环境变量。

	
  * 准备一个可恢复的计划，测试其可用。

	
  * 记录详细的日志，定期存放日志文件。

	
  * 关注服务器相关情况和任务，便于很快rebuild。确保一个干净的AMI或等价东东。

	
  * 如果你在用AWS，至少有一个非AWS的撤退方案。

	
  * 使用一台开发用的服务器。

	
  * 不要依赖浏览器嗅探【注6】。检测相关功能的支持。如果你做了很多，你很可能得到很多乐趣。

	
  * 如果你在用框架，确保冗长的错误信息在生产环境不会出现。




### 一般过程





	
  * 对项目最终形式的不确定性要保持开放。准备好逃生路线和心中的备选方案，你有可能走到死亡的尽头或者数据不配合。

	
  * 项目之初就形成小组，想增加功能的成员应该和大家一起讨论，如果可能，就让大家的位置挨在一起。

	
  * 充足的测试时间。参与游击式测试【注7】的人们并不属于项目，在他们放松之前，你不要给测试者一堆预先说明（真正用户也应该有什么说明）。

	
  * 不要花太多时间设计非静态事物的静态模型。尽可能快地从纸上过度到编码。图表软件只是做图表用的。

	
  * 决定给予不同种类的用户多大的关注度要求你首先得了解你的用户。理解他们是谁，他们想要什么，他们用什么浏览器，什么设备等。当决定哪种资源投入到选取的不同脚本了，才能开始。

	
  * 花时间写好文档。详细说明依赖和安装。在你的例子中使用真实情况的脚本和变量名，而不是 foo 和 bar 的随意的东东。


原文地址：[https://github.com/veltman/principles](https://github.com/veltman/principles)
注1：pop-up book:[http://en.wikipedia.org/wiki/Pop-up_book](http://en.wikipedia.org/wiki/Pop-up_book)
注2：Scavenger hunt：[http://en.wikipedia.org/wiki/Scavenger_hunt](http://en.wikipedia.org/wiki/Scavenger_hunt)
注3：legend标签：[http://www.html5china.com/manual/html5/html5_legend.htm](http://www.html5china.com/manual/html5/html5_legend.htm)
注4：罗宾森投影（Robinson projection），[http://zh.wikipedia.org/zh-cn/罗宾森投影](http://zh.wikipedia.org/zh-cn/罗宾森投影)
注5： Albers projection，[http://zh.wikipedia.org/wiki/亚尔勃斯投影](http://zh.wikipedia.org/wiki/亚尔勃斯投影)
注6：Browser sniffing：[http://en.wikipedia.org/wiki/Browser_sniffing](http://en.wikipedia.org/wiki/Browser_sniffing)
注7：Guerrilla test：参考《游击式可用性测试的艺术 》[http://www.alibuybuy.com/posts/84038.html](http://www.alibuybuy.com/posts/84038.html)
