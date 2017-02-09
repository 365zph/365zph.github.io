---
author: viviworld
comments: true
date: 2014-02-12 09:02:26+00:00
layout: post
link: http://www.labazhou.net/2014/02/the-number-one-dev-killer/
slug: the-number-one-dev-killer
title: 第一名开发杀手
wordpress_id: 271
categories:
- 编程
tags:
- javascript
- MailChimp
- nodejs
- php
- rails
- Wasabi
- 编程
---

[caption id="attachment_272" align="alignnone" width="350"][![One of those days?](http://www.labazhou.net/wp-content/uploads/2014/02/rage.gif)](http://www.labazhou.net/wp-content/uploads/2014/02/rage.gif) One of those days?[/caption]

我经常发现我着迷于现代技术。我的意思是，我们经历了计算机从像建筑物大小 发展到 相等计算能力的、小到能放进口袋。50年（我让你决定，对于我们大部分人使用计算机看猫的照片、在网上沟通，是不是会感到悲哀）。这是一个印象深刻的壮举，特别在考虑到地理名词在50年里几乎没有什么变化。

然而，最常让我着迷的是人们以及他们与新技术互动（和创造！！）。我沉浸在开发文化里，开始一次又一次地看到相同的模式，试着了解是什么让一些项目（尤其是人们彼此隔离地工作方式）不能得到发展，又是什么让一些项目如此成功。因此今天我想写一个故事来描述这一点，在我看来，开发者生产效率的巨大杀手。


### 关于邮件列表的故事


你认识这个家伙吗？

[caption id="attachment_273" align="alignnone" width="300"][![mailchimp](http://www.labazhou.net/wp-content/uploads/2014/02/mailchimp.jpg)](http://www.labazhou.net/wp-content/uploads/2014/02/mailchimp.jpg) mailchimp[/caption]

至少看起来面熟，对吧？它是[MailChimp](http://mailchimp.com/)邮件猩猩【注1】。这个家伙如何？

[![赫尔墨斯，希腊神](http://www.labazhou.net/wp-content/uploads/2014/02/hermes.jpg)](http://www.labazhou.net/wp-content/uploads/2014/02/hermes.jpg)

他是赫耳墨斯【注2】，希腊信使。但是如果你不是一个神学爱好者，那么MailChimp吉祥物Freddie【注3】很可能在现代环境里比赫尔墨斯更具意义。怎么样？让我给你讲个故事来解释一下吧。

由于我的blog已经有了一些流量，收到了大量读者邮件，因此我想得到一个邮件列表。你知道，这没有什么难度，仅仅是一封email，每次发送给用户，通知他们我这周做了什么。我应该做什么呢？

我可以使用MailChimp，绝对可靠，被足够多的人们比如[Andrew Chen](http://andrewchen.co/)和[Patrick McKenzie](http://www.kalzumeus.com/)验证过，对我而言应该足够好了。但是我做了什么？就像一个“合格的”黑客，我开始自己写（除了写一个牛逼的项目，我有点儿害怕人们可能知道我在用MailChimp。我不知道为什么，我猜想我只是有某种古怪的DIY癖）。它将被叫做赫尔墨斯，用Express/Node.js实现，我完全陷进去了。仅仅因为我想重新发明MailChimp而不是去做更重要的事情，或需要花时间的小事情。

我做了很多（跳过一些）：

    
    function sendSingleMail(subject, to) {
        getSignupEmailTemplate({
            to: to
        }, function(html) {
            mailgun.sendRaw("Nathan LeClaire <nathan.leclaire@gmail.com>", [to.email],
                'From: nathan.leclaire@gmail.com' +
                '\nTo: ' + to.email +
                '\nContent-Type: text/html; charset=utf-8' +
                '\nSubject: ' + subject + '\n\n' +
                html,
                function(err) {
                    if (err) console.log("there was an email error", err);
                    else console.log("successfully sent email to " + to.email);
                }
            );
        });
    }
    
    function getSignupEmailTemplate(context, callback) {
        var tmpl = jade.renderFile("views/signup-email.jade", context, function(err, html) {
            if (err) {
                console.log("error rendering jade template");
            } else {
                callback(html);
            }
        });
    }
    
    function main(conn) {
        var subscribers = r.db("hermes").table("subscriber");
        app.post("/email_signup", function(req, res) {
            var email = req.body.email;
            subscribers.insert({
                email: email,
                name: "",
                subscriptionConfirmed: false
            }).run(conn, function(err, result) {
                if (err) {
                    console.log("[ERROR] failed to insert email from someone... ", err);
                    res.json({
                        success: false
                    });
                } else {
                    sendSingleMail("Hi! I hear you'd like to subscribe to my blog.", {
                        email: email
                    });
                    res.json({
                        success: true
                    });
                }
            });
        });
    
        app.listen(3001);
    }


以前我对自己说：“你有必要或你闲着没事？为什么你不去做让你的blog和其他项目更加成功的、相对容易些的事情呢？[检查死链接](http://github.com/nathanleclaire/checkforbrokenlinks)仍然没有部署！虽然它评价不好，我知道我是对的。


### 启发


因此我咬紧牙关使用MailChimp。你能够在网站左侧看到我的”劳动“成果，事实上我非常高兴我决定用它、而没有自己写邮件管理系统。

为什么？因为我用MailChimp省下了时间，不需要开发原始的次品，我就可以花更多的时间去做其他更有价值的事情。这样，我预期和希望的用户邮件的大量涌入一直没有真正出现，在写这篇文章时，我的邮件列表总共只有两个人 :D（我和我女朋友，虽然我正为提高人数而努力着）。我很高兴todo list上有更少的重要事情，即使我没有花大把时间在马上获取奖金的事情上，我也不觉得失败（虽然我认为将来是这样）。我得到了很多益处，包括数据分析和一个非常棒的web UI，付出的小代价是注册表单上的一小块MailChimp logo。加入吧！

回头看看Freddie和赫尔墨斯的对决吧，为什么使用一个不可信的牌子 / 当你使用一个身经百战的老朋友，粗略的开源产品？

我要表达的观点，如果你还没有猜到，那就是开发人员（我以前就是这样）时常因[非我原创](http://en.wikipedia.org/wiki/Not_invented_here)【注4】而痛苦地谋杀他们潜在的生产力。我们中有些人应该遇到过倔强的、反对框架的程序员，他们总是坚持他们自己能够做得更好，甚至是借助今天开发可获得的工具这一荒谬的法宝？有多少客户端JavaScript MV*框架由于其作者不满足于简单地提高现存解决方案而存在？我知道它是简单的目标，但请允许我列出一些：



	
  * Angular

	
  * Backbone

	
  * Meteor

	
  * React

	
  * Flight

	
  * Singool.js

	
  * Knockout

	
  * Sammy.js

	
  * Ember.js

	
  * Maria

	
  * Terrific Composer

	
  * Rivets.js

	
  * Synapse

	
  * Ractive


好吧.

虽然他在稍微不同的上下文里说话，我感到Keith Perhac在《[Kalzumeus Software Podcast](http://www.kalzumeus.com/2012/05/18/kalzumeus-podcast-ep-2-with-amy-hoy-pricing-products-and-passion/)》巧妙地击败了这个想法：


<blockquote>真的，我认为有一个……它不只是Hacker News群体，不只是Slashdot群体，不只是techie群体，它有太多的人。我认为抵制者的时间比钱多，老实讲才会这样子。

老实讲，因为，如果我有大量时间，如果我有一份朝九晚五的工作，我有固定收入每天有固定的大把时间，并且，我需要时间跟踪软件，我很可能在周末写我自己的软件，因为在这一点上，我的时间比钱多。

对于试着运营或开始他们的事业的人，他们的钱比时间多。不是因为他们赚了大把的钞票，而是因为他们的时间更有价值，由于他们有很多其他的事情要做。</blockquote>


这好像是至理名言。人们能够、且应该少关注重复发明轮子的事情，多关注他们的核心价值提案。

注意，我大部分讨论是基于为自己工作的独立开发者、或小的协作团队的前提，而不是大型前沿组织，比如在Joel Spolsky[这篇文章](http://www.joelonsoftware.com/articles/fog0000000007.html)讨论的那种，他在文中赞同“非我所创”。我同意他的大部分观点（非现成的web服务器曾经和Google的一样快，这是他们的业务优点），但是我也认为支持NIH（非我原创）有些危险。不是说Joel有责任发现每个人的最大兴趣点什么的，而是我对他从来没有经历过公司咬紧牙关投资太多资源去重复发明轮子的业务状况。毕竟，是他发明了Wasabi【注5】，一个专门的Visual Basic行话（dialect），参看他的未来商业伙伴Jeff Atwood的[这篇文章](http://www.codinghorror.com/blog/2006/09/has-joel-spolsky-jumped-the-shark.html)：


<blockquote>FogBugz用Wasabi编写，一个非常高级的、功能性编程的、带有闭包、Lambda、类似Rails的Active Record的语言（dialect），它能够编译成VBScript, JavaScript, PHP4 or PHP5。Wasabi是一门私有的、in-house语言，由我们最好的一名开发者编写，特别为开发FogBugz做了优化；Wasabi编译器用C#编写。</blockquote>


它或许是为Fog Creek工作的，但是很多古怪的技术决定都终结于为人们工作（比如[把PHP转换成C++](http://www.hhvm.com/blog/)）。你想维护那个代码库吗？


### 对立面


当然，对立面同样有害，我想描述一种人，你我都知道描述这一点。我想，如果你是技术社区的重度参与者，或许你会找到熟悉的这个人。

这种人对技术充满激情。事实上，他们对技术如此有激情，以致于他们非常相信这是他们可能遇到的每个问题的一剂万能药。他们把重要性放在理论上的手淫和”纯洁“上，而不是执行和发布，他们跳跃于各个框架而从来不会投入任何实际的精神重活。他们是一个经常出现的”Hello Worlder“，一直追随热门的新东西。

他们可能嘲笑PHP或Rails程序员忙于把事情做完而没有去听和关心。他们也有探索和学习的激情，这是好的，只是他们缺乏知识和领悟能力。这和有志于创办自己公司的人类似，但是缺乏找到好的产品/市场定位的实践深度。他们或许试着解决没人碰到的问题，或让技术选择规定业务方向而不是另一种方式。

我多多少少是这种人。这种人和身边有这种人的人没有两样。我认为一个人应当羞于成为这种人，也应该羞于成为一个NIHSer（自我原创）。在我看来，你应该对事物保持开放心态，不要让你的自尊导向为一名与团队在一起感到快乐的开发者。剧透警告：你不是100%正确。

结论

继续前行吧，兄弟姐妹们。仅仅把想法放到用合适的工具做合适的事情上，把事情快速做完，而不是学习最新、最热的东东（它或许带来更多的头痛）。运行MySQL做为唯一数据库的box，如果需要、前端就只用jQuery，开发一个iOS应用而不是用PhoneGap和AngularJS编写的HTML5应用，这都没有关系。工具适应需要，把事情做完（尤其在你创办公司之初）。

下周之前，保持漂亮的互联网！哦，已经订阅了我的邮件列表。你在这里杀了我。

原文地址：[http://nathanleclaire.com/blog/2014/02/08/the-number-one-dev-killer/](http://nathanleclaire.com/blog/2014/02/08/the-number-one-dev-killer/)
注1：MailChimp：[http://www.baike.com/wiki/MailChimp](http://www.baike.com/wiki/MailChimp)
注2：赫耳墨斯：[http://zh.wikipedia.org/wiki/Hermes](http://zh.wikipedia.org/wiki/Hermes)
注3：Freddie：[http://mailchimp.com/about/brand-assets/](http://mailchimp.com/about/brand-assets/)
注4：非我所创或NIH综合症（英文：Not Invented Here Syndrome）：[http://zh.wikipedia.org/zh-cn/非我所創](http://zh.wikipedia.org/zh-cn/非我所創)
注5：Wasabi：[http://stackoverflow.com/questions/1003359/what-is-wasabi](http://stackoverflow.com/questions/1003359/what-is-wasabi)
