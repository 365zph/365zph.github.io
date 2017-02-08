---
author: viviworld
comments: true
date: 2014-12-05 02:46:43+00:00
layout: post
link: http://www.labazhou.net/2014/12/5-steps-to-protect-mobile-apps-from-attacks/
slug: 5-steps-to-protect-mobile-apps-from-attacks
title: 保护移动应用免遭攻击的5个步骤
wordpress_id: 1398
categories:
- 安全
tags:
- APP
- apple
- bug
- ios
- OWASP
- SSL
---

原文地址（source）：[http://www.drdobbs.com/security/5-steps-to-protect-mobile-apps-from-atta/240169330](http://www.drdobbs.com/security/5-steps-to-protect-mobile-apps-from-atta/240169330)

苹果CEO库克在公司的全球开发者大会上指出，注册的移动应用开发者已经超过了九百万，较去年增长了47%。有更多的个人把他们的技能和创新带到了这个行业，虽然这是值得激动的，但是开发者和新应用的猛增也带来了日益增长的恶意工具的威胁。

对于你们开发者而言，有必要熟悉最新的安全实践。这有助于你维护自己的声誉，让你把精力放在开发有创新的app上，而不是因疏忽所导致的、用户数据被连累的潜在事故上。

很多开发者错误地认为移动领域对于威胁是有免疫力的。这种错误的安全意识导致一些开发者减少了预防措施的投入，导致严重的信息破坏，比如今年早些时候的[Fandango app](http://www.pcmag.com/article2/0,2817,2455703,00.asp)。真实情况是，app安全和web安全一样重要。移动app是一家企业安全领域的切入点，确保这扇大门得到有效防护的责任，落到了开发者肩头。

甚至用心良苦的开发者也不擅长必要的用户保护措施。我经常听到使用非常抽象的术语讨论安全。开发者认为，“我已经确保我的app是安全的了”，但是很多人不知道那意味着什么、或可用的资源有哪些。

我喜欢分享保护app的五个步骤，这是我推荐给开发者的：



	
  1. **重新思考安全，并融入到开发中**。我看到的、经常犯的一些错误，集中在把安全隔离在流程中的单独一步。安全还应该是整体的、系统化的。当开发者试图在开发结束时混乱拼凑安全计划时，缺口常常就打开了。我还经常看到，很多开发者在他们代码的安全部分做得非常不错，但是他们忽略了后退一步，以审视整个代码库。

	
  2. **了解基础知识**。早期重要的一个步骤是学习基础的安全威胁。开放网页应用安全计划（OWASP）的[前10项移动风险](https://www.owasp.org/index.php/Projects/OWASP_Mobile_Security_Project_-_Top_Ten_Mobile_Risks)是价值连城的资源。它详细列出了10种对于移动应用最危险的安全威胁。每年都会更新，我们应该定期参考一下。这对于新手尤其重要。它或许是基础的，但是遵循OWASP的建议，你可以把应该采取的措施与其并行使用。

	
  3. **使用行之有效的方案**。不要重复发明轮子。所有主流的操作系统都有NIST认证的加密框架，它们已经经过专家严格检验了。试图自己开发框架的开发者，经常面临易于攻破的结局。

	
  4. **保护好已存储数据（data at rest）**。已存储数据的处理是个脆弱的地方，尤其在你收集一些敏感数据时。让你的存储数据免受攻击,有很多选择，比如尽可能早地删除数据、在生产环境关闭不需要的数据、以及实施一种不对称加密的方案。后者确保了已存储数据是安全的，因为能够解密这些数据的私钥从来不会真正出现在设备上。

	
  5. **执行证书锁定（certificate pinning）**。[苹果在iOS和OS X上的问题](http://www.zdnet.com/apples-goto-fail-tells-us-nothing-good-about-cupertinos-software-delivery-process-7000027449/)和“goto fail”的bug是所有开发者应该吸取的教训。这个bug绕过了SSL认证、而没有验证证书是可信任的。使用SSL固然重要，如果你不能确信你的证书，那还是不够的。你需要确保你真正验证了返回到资源的证书，[以避免请求过程中的任何攻击](http://www.labazhou.net/2013/12/websites-that-can-self-defend-against-attackers/)。


随着智能手机和平板变成我们首选的屏幕，移动应用上的攻击也在增长。如果你的下一个app没有正确地规划，即使它获得了划时代的成功，也是无关紧要的。对安全地开发保持警惕，保护的不只是使用你app的人，还有你自己的声誉和职业前景。
