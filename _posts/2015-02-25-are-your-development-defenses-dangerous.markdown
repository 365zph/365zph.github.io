---
author: viviworld
comments: true
date: 2015-02-25 11:32:04+00:00
layout: post
link: http://www.labazhou.net/2015/02/are-your-development-defenses-dangerous/
slug: are-your-development-defenses-dangerous
title: 开发中的防御措施是危险的吗？
wordpress_id: 1639
categories:
- 测试
- 编程
tags:
- bug
- QA
- 程序员
- 自动化测试
- 阿金库尔战役
---

原文地址（original source）：[http://www.industriallogic.com/blog/are-your-development-defenses-dangerous/](http://www.industriallogic.com/blog/are-your-development-defenses-dangerous/)

为了说明防御是怎样让我们遭受危险的，让我们先回到600年前的阿金库尔战役【注1】。

在《Managing the Risks of Organizational Accidents》中，James Reason使用这场1415年英法战役，阐释了今天的高科技术防御是怎样让我们遭受危险的。

[![阿金库尔战役](http://www.labazhou.net/wp-content/uploads/2015/02/Battle-of-Agincourt.png)](http://www.labazhou.net/wp-content/uploads/2015/02/Battle-of-Agincourt.png)

在这场战役里，英国军人都是轻装，人数大约只有法国军人的五分之一。法国人有重装盔甲，可以保护他们抵御弓箭和长矛。在战斗中，凶险的地形让法国人的两个侧翼挤在一起。一旦他们到达射程之内，英国弓箭手就用密集的、一码长的、带有钢尖的箭射过来。很多法国人立即在这种攻击中牺牲了，而那些从受伤的战马掉下来的法国人，由于自己盔甲的笨重而无法站起来！英国人很快就赢取了胜利。


### 无法预见的危险


James Reason对这种问题做了如下总结：


<blockquote>“被设计成应对某种危险的防御，可以让他们的用户遭受其它种类的危险，通常无法被创建它们的人们预见到，甚至用户都意识不到。”</blockquote>


在软件开发中，团队的[自动化测试](http://www.labazhou.net/2015/01/increase-defect-detection-with-our-code-review-checklist-example/)保证了代码按照预期运行，避免程序员因疏忽而带来瑕疵。

那么这种防护措施是怎样让开发者和用户遭受危险的呢？

当自动化测试让开发者带有如下特点时，这种危险就出现了：



	
  * **自负**：开发者认为自动化测试检查了所有重要的地方，他们通常不会手动测试新的、或修改后的代码，然后一个瑕疵就带入了生产环境，从而伤害用户、延缓开发。

	
  * **疏忽**：当自动化测试无缘无故失败（“误报”）时，程序员通常很少会注意到这些失败，合理的失败没有被修复，代码被提交到生产环境，一个瑕疵引入了，从而伤害用户、延缓开发。

	
  * **恼怒**：当自动化测试与代码的实现逻辑耦合度较高时，测试常常在重构过程中失败，程序员被所有这些失败的测试激怒了，他们开始避免重构，结果软件设计变得越来越复杂和脆弱，进而造成开发延缓。

	
  * **受阻**：当自动化测试运行缓慢时，程序员在开发过程中就停止运行它们，瑕疵就溜进了代码，要么延缓开发、要么伤害生产环境中的用户。

	
  * **分心**：当自动化测试运行缓慢时，程序员在长时间的测试运行过程中，就开始分心了，失去了关注并最终导致效率低下。


这些危险听起来不陌生吧？哪一项是无法预见的？

在最好的情况下，人们从他们的开发防御中找到并移除所有危险。

对于自动化测试，这意味着：

	
  * 创建快速的、可靠的自动化测试

	
  * 根据情况，手动测试

	
  * 修复所有的误报

	
  * 解耦掉对于实现逻辑的测试

	
  * 频繁运行测试


优秀的开发中的防御措施会增加速度、削减压力，从来不会使得要保护的人们处于危险之中。

	
  * 注1：阿金库尔战役（Battle of Agincourt）发生于1415年10月25日，是英法百年战争中著名的以少胜多的战役。在亨利五世的率领下，英军以由步兵弓箭手为主力的军队于此击溃了法国由大批贵族组成的精锐部队，为随后在1419年收服了整个诺曼底奠定基础。这场战役成为了英国长弓手最辉煌的胜利，也是一场在战争史有重要影响的战役—以弓箭手作为主力对抗重装骑士的胜利。[http://zh.wikipedia.org/wiki/阿金库尔战役](http://zh.wikipedia.org/wiki/阿金库尔战役)


