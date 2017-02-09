---
author: viviworld
comments: true
date: 2015-05-21 07:58:29+00:00
excerpt: 对于编程而言，这种自我批评的意义需要检测出在设计、代码、过程和行为中的低效和反效果的模式。这就是对反面模式【注1】的理解为什么对于任何程序员都非常有用的原因。本文基于我遇到它们的频率以及花费多长时间才能消除它们引起的破坏做了反面模式的讨论
layout: post
link: http://www.labazhou.net/2015/05/nine-anti-patterns-every-programmer-should-be-aware-of-with-examples/
slug: nine-anti-patterns-every-programmer-should-be-aware-of-with-examples
title: 每个程序员都应注意的 9 种反面模式
wordpress_id: 2056
categories:
- 编程
tags:
- bug
- java
- 优化
- 单元测试
- 反面模式
---


	
  * 原文地址（original source）：[http://sahandsaba.com/nine-anti-patterns-every-programmer-should-be-aware-of-with-examples.html](http://sahandsaba.com/nine-anti-patterns-every-programmer-should-be-aware-of-with-examples.html)

	
  * 作者（author）：[https://twitter.com/sahand_saba](https://twitter.com/sahand_saba)





* * *



某种健康的自我批评对于专业和个人成长是至关重要的。对于编程而言，这种自我批评的意义需要检测出在[设计](http://www.labazhou.net/2014/08/why-as-a-developer-you-should-care-about-design/)、代码、过程和行为中的低效和反效果的模式。这就是对反面模式【注1】的理解为什么对于任何程序员都非常有用的原因。本文基于我遇到它们的频率以及花费多长时间才能消除它们引起的破坏做了反面模式的讨论，通过我发现的反复出现的、粗略地组织起来。

讨论到的某些反面模式和认知偏误有些共通的地方，或由它们直接引起的。在我们本文继续之前，关于[认知偏误的相关链接](http://en.wikipedia.org/wiki/List_of_cognitive_biases)也被提供了。维基百科也有不错的认知偏误词条供你参考【注9】。

在开始之前，我们要切记，教条式思考阻碍了增长和创新，因此把下面的列表做为一套指南、而非一成不变的规则。如果我错过了你认为重要的东东，请在下面的评论留言！

反面模式的清单包括：



	
  1. 不成熟的优化

	
  2. 单车车库【注2】

	
  3. 分析瘫痪（Analysis paralysis）

	
  4. 上帝类【注3】

	
  5. 害怕新增类

	
  6. 内部平台效应（Inner-platform effect）

	
  7. 魔术数字和字符串【注4】

	
  8. 目标管理【注6】

	
  9. 无用的（幽灵）类【注8】




### 不成熟的优化




<blockquote>“在 97% 的时间里，我们应该忘记微不足道的效率：过早的优化是万恶之源。然而在关键的 3% 我们不应该错过优化的机会。” ------Donald Knuth

“不假思索就动手还不如不做。” ------Tim Peters，《The Zen of Python》【注5】</blockquote>




#### 意思


对于在哪里优化、如何去优化，在你有足够信息做出有意义的结论之前，就开展的优化。


#### 糟糕的原因


难以确切地知道实践中的瓶颈。企图在得到实验数据之前优化，伴随着微不足道的改进，有可能增加代码复杂度和 bug 产生的空间。


#### 如何避免


把编写整洁、可读性强的、能运行的代码摆在首位，使用已知的和测试过的算法和工具。当需要找到瓶颈和优化优先级时，再使用分析工具。依靠策略而非臆测和推断。


#### 例子和信号


在企图找到瓶颈之前做缓存。使用复杂的、未经通过的“启发式”，而不是知名的、数学上正确的算法。选择一种新的、未经测试的实验性框架，在理论上可以减少高负载下的请求延迟，当你处于早期阶段时，你的服务器大部分时间处于空转状态。


#### 棘手的地方


棘手的地方在于知道什么时候是不成熟的优化。提前规划对于增长是重要的。选择易于优化和成长的设计和平台是关键。把“不成熟的优化”做为评判编写糟糕代码的借口也是有可能的。例如：当更简单的、数学上正确的 O(n) 算法存在时，编写一个 O(n2) 算法来解决问题，仅仅因为越简单的算法，越难以理解。


#### 总结


在优化之前做分析。在效率被需要、被观察到的证据支持之前，避免为了效率而牺牲简洁。


### 单车车库




<blockquote>“我们总是在讨论封面的排版和颜色时出现中断。每次讨论之后，我们被要求投票。我想，对于我们之前在会上决定的相同颜色进行投票，是最有效率的，但结果显示，我总是处于少数派！我们最终选择了红色。（结果是蓝色。）” ------Richard Feynman，《你在乎其他人的想法吗？》</blockquote>




#### 意思


把过多时间花在琐碎而且经常是主观问题的辩论和决定上的趋势。


#### 糟糕的原因


这是浪费时间。Poul-Henning Kamp [在这封邮件里](http://phk.freebsd.dk/sagas/bikeshed.html)进行了深入讨论。


#### 如何避免


当你注意到这一点时，鼓励团队成员注意到这种趋势，把达成一个决定做为高优先级（投票、抛硬币等，如果你不得不这样做的话）。当这个决定有意义（例如，在两种不同的 UI 设计之间决定）、而不是进一步的内部讨论时，考虑稍后的 A/B 测试以重新审视这个决定。

[caption id="attachment_2061" align="alignnone" width="291"][![feynman](http://www.labazhou.net/wp-content/uploads/2015/05/feynman.jpg)](http://www.labazhou.net/wp-content/uploads/2015/05/feynman.jpg) Richard Feynman不是单车车库的粉丝[/caption]


#### 例子和信号


花费数小时或数天讨论你的 app 应该使用什么背景色，或者把一个按钮放在 UI 的左侧还是右侧，或者在你的代码库里的缩进使用制表符而非空格。


#### 棘手的地方


在我看来，单车车库相较于不成熟的的优化，是更容易发现和防止的。只需要注意到花在做决定和合约上的时间，问题有多么琐碎，如有必要就加以干预。


#### 总结


不要把过多时间花在琐碎的事情上。


### 分析瘫痪




<blockquote>“想要预见性，不愿意行动，而行动是简单有效的，缺乏清晰的思考，建议混乱……这些构成了历史上无休止重复的特点。” ------Winston Churchill，国会辩论

“做也许好过不做。” ------Tim Peters，《The Zen of Python》</blockquote>




#### 意思


对问题的过度分析阻碍了行动和进展。


#### 糟糕的原因


过度分析能够完全延缓或阻止进展。在极端情况下，分析的结果到了实施的时候，会变得毫无用处；或者更糟糕的是，项目或许从来走不出分析阶段。当决定难以做出时，更容易臆测出，更多的资讯将有助于做决定 ------参看 [资讯偏误](http://en.wikipedia.org/wiki/Information_bias_(psychology)) 和 [效度偏误](http://en.wikipedia.org/wiki/Illusion_of_validity)。


#### 如何避免


重申，意识是有帮助的。强调迭代和改善。根据可用于进一步有意义分析的更多的数据点，每次迭代提供更多的反馈。没有新的数据点，更多的分析将变得越来越让人猜疑。


#### 例子和信号


花费数月、甚至数年来决定一个项目的需求、新 UI、或数据库设计。


#### 棘手的地方


棘手的地方在于知道什么时候该从计划、需求收集和设计阶段转移到实施和测试阶段。


#### 总结


宁愿迭代，也不要过度分析和猜测。


### 上帝类




<blockquote>“简洁胜过复杂。” ------Tim Peters，《The Zen of Python》</blockquote>




#### 意思


上帝类是控制很多其它类，以及有很多依赖和负责过多的类。


#### 糟糕的原因


上帝类倾向于增长到变成维护噩梦的地步------因为他们违反了单一责任原则，它们难以单元测试、调试和记录文档。


#### 如何避免


避免把类变成上帝类，可以通过把责任分解为有着单一化的、清晰定义的、经过单元测试和文档责任的更小的类。


#### 例子和信号


寻找类名包含了“manager”、“controller”、“driver”、“system”、或“engine”的类。当心 import 或依赖很多其它类、控制太多其它类、或有很多处理不相关任务的方法的类。

[caption id="attachment_2064" align="alignnone" width="406"][![上地类知道很多类和/或很多控制。](http://www.labazhou.net/wp-content/uploads/2015/05/god-class1.png)](http://www.labazhou.net/wp-content/uploads/2015/05/god-class1.png) 上地类知道很多类和/或很多控制。[/caption]


#### 棘手的地方


随着项目年限、需求和工程师人数的增长，小型的且有着良好意图的类慢慢地变成了上帝类。重构这些类就变成了浩大的任务。


#### 总结


避免有着太多责任和依赖的庞大的类。


### 害怕新增类




<blockquote>“间隔胜于紧凑。” ------Tim Peters，《The Zen of Python》</blockquote>




#### 意思


坚信更多的类必然使得设计更加复杂，从而对新增类或把大类分解为一些小类感到恐惧。


#### 糟糕的原因


新增类可以显著帮助降低复杂度。贴一副大的杂乱的毛线团。当解开时，你将得到一些分隔开的毛线团。类似地，一些简单的、易于维护、易于记录文档的类，要远远好过于有着太多责任的、单一庞大的、复杂类。（参看上面的上帝类的反设计模式）

[caption id="attachment_2057" align="alignnone" width="612"][![Photo by absolut_feli on Flickr](http://www.labazhou.net/wp-content/uploads/2015/05/yarn.jpg)](http://www.labazhou.net/wp-content/uploads/2015/05/yarn.jpg) [Photo by absolut_feli on Flickr](https://www.flickr.com/photos/absolut_feli/7162673224)[/caption]


#### 如何避免


要注意新增类在什么时候可以简化设计以及解耦你的代码中不必要的耦合部分。


#### 例子和信号


考虑下面一个简单的例子：



    
    class Shape:
        def __init__(self, shape_type, *args):
            self.shape_type = shape_type
            self.args = args
    
        def draw(self):
            if self.shape_type == "circle":
                center = self.args[0]
                radius = self.args[1]
                # Draw a circle...
            elif self.shape_type == "rectangle":
                pos = self.args[0]
                width = self.args[1]
                height = self.args[2]
                # Draw rectangle...


现在对比下面的代码：



    
    class Shape:
        def draw(self):
            raise NotImplemented("Subclasses of Shape should implement method 'draw'.")
    
    class Circle(Shape):
        def __init__(self, center, radius):
            self.center = center
            self.radius = radius
    
        def draw(self):
            # Draw a circle...
    
    class Rectangle(Shape):
        def __init__(self, pos, width, height):
            self.pos = pos
            self.width = width
            self.height = height
    
        def draw(self):
            # Draw a rectangle...


当然，这是一个明显的例子，但是它揭示了一点：内部有着依赖性的或复杂逻辑的大型类，可以、也经常应该被分解为更小的类。最后的代码将有更多的类，但是更加小型。


#### 棘手的地方


新增类不是一颗神奇的子弹。通过分解大型类来简化设计，需要对责任和需求进行深入分析。


#### 总结


类的数量多，不一定是糟糕设计的信号。


### 内部平台效应




<blockquote>“那些不理解 Unix 的人因对其不良改造而受到谴责。” ------Henry Spencer

“任何 C 或 Fortran 程序复杂到一定程度之后，都会包含一个临时开发的、只有一半功能的、不完全符合规格的、到处都是 bug 的、运行速度很慢的 Common Lisp 实现。” ------格林斯潘第十法则</blockquote>




#### 意思


复杂软件系统倾向于它们所运行平台、或它们所使用编程语言的、功能的重新实现，通常是不良实现。


#### 糟糕的原因


像计划任务或磁盘缓冲区之类的平台级别的任务不是容易搞定的。糟糕的设计方案易于带来瓶颈和 bug，尤其系统规模变大后。重新发明可替代的语言结构来达到语言已有可能的东东，会导致难以阅读的代码，对于刚接手代码库的人而言，有着更加陡峭的学习曲线。它还限制了重构和代码分析工具的效用。


#### 如何避免


学习使用你的操作系统或平台所提供的平台和功能。避免创建与已有结构（尤其是因为你不熟悉新语言而找不到你的旧语言的功能）竞争的语言结构的诱惑。


#### 例子和信号


使用你的 MySQL 数据库做为工作队列。重新实现你自己的磁盘缓冲区、而不是依赖你的操作系统。用 PHP 为你的 web 服务器编写计划任务。用 C 定义Python 之类的语言结构的宏。


#### 棘手的地方


在极少情况下，重新实现平台（JVM、Firefox、Chrome 等）的某些部分可能是有必要的。


#### 总结


避免重新发明你的操作系统或开发平台已经做得很多的功能。


### 魔术数字和字符串




<blockquote>“明了胜于晦涩。” ------Tim Peters，《The Zen of Python》</blockquote>




#### 意思


直接使用数字或字符串字面量，而不是在代码里命名的常量。


#### 糟糕的原因


主要问题在于，数字或字符串字面量的语义由于没有一个解释型的名字或另一种形式的注解，而被部分或完全地隐藏了。这增加了理解代码的难度，如果必须要修改常量，那么搜索和替换、或其它重构工具会引入微妙的 bug。考虑下面的代码片段：

    
    def create_main_window():
        window = Window(600, 600)
        # etc...


这两个数字是什么？假定一个数字是窗户的宽度，第二个是高度。如果需要修改宽度为 800，那么搜索和替换将是危险的，因为在这个例子中，它也将修改高度的值，或许还有代码库里其它出现数字 600 的地方。

字符串字面量的这些问题貌似不多，但是代码里有未命名的字符串字面量，将使得国际化更加困难，对于有着相同字面量却有着不同语义的情况，就带来了类似的问题。比如，英语中的同义词在搜索和替换时，能够产生类似问题；假设“point”出现了两次，一个是指名词（比如“she has a point”），另一个是动词（比如“point out the differences……”）。如果一种字符串检索机制可以明确地指示语义，那么用这种机制替换这样的字符串字面量，将帮助你区分这两种情况，当你把这些字符串送去翻译时，也就方便多了。


#### 如何避免


使用命名的常量、资源检索方法、或注释。


#### 例子和信号


简单的例子如上所示。这种特定的反面模式非常容易检测到（期待下面提到的一些棘手的情况）。


#### 棘手的地方


有一个狭窄的灰色地带，难以区分特定的数字是不是魔术数字。例如，索引从 0 开始的语言中的数字 0。其它例子，用 100 来计算百分比，用 2 做奇偶校验等。


#### 总结


避免代码中出现未注解、未命名的数字和字符串字面量。


### 目标管理




<blockquote>“用代码行来衡量开发进度，无异于用重量来衡量制造飞机的进度。” ------比尔·盖茨</blockquote>




#### 意思


严格地依靠数字来做决定。


#### 糟糕的原因


数字是伟大的。避免本文提及的前两个反面模式（不成熟的优化和单车车库）的主要策略是分析或 A/B 测试，帮助你根据数字而非臆测来优化或决策。然而，盲目地依赖数字是危险的。比如，数字倾向于比它们有意义的模型要长久，或者模型过期了、不再精确地代表现实。这会导致错误的决策，尤其当它们完全自动化时------参考[自动化偏误](http://en.wikipedia.org/wiki/Automation_bias)。

[caption id="attachment_2058" align="alignnone" width="300"][![Do you find yourself commiserating with Pryzbylewski from the HBO show The Wire, Season 4?](http://www.labazhou.net/wp-content/uploads/2015/05/pryzbylewski.jpg)](http://www.labazhou.net/wp-content/uploads/2015/05/pryzbylewski.jpg) Do you find yourself commiserating with Pryzbylewski from the HBO show The Wire, Season 4?[/caption]

依赖数字做决定（不仅仅是告知）的另一个问题是，策略过程可以随着时间来操作，以达成期望的数字。参看[观察者期望效应](http://en.wikipedia.org/wiki/Observer-expectancy_effect)【注7】。分数膨胀就是这种情况的一个例子。HBO 显示了 The Wire（顺便说一句，如果你还没有看过，你一定要看！）出色地描述了依赖数字的问题，展现了警察部门和后来的教育系统用数字游戏取代了有意义的目标。如果你喜欢图表，下面的图表展示了 30% 通过率的一场考试的分数分布，极好地说明了这个观点。

[caption id="attachment_2059" align="alignnone" width="604"][![波兰高中毕业考试中通过率30%的分数分布](http://www.labazhou.net/wp-content/uploads/2015/05/poland-matura-1024x661.png)](http://www.labazhou.net/wp-content/uploads/2015/05/poland-matura.png) 波兰高中毕业考试中通过率30%的分数分布[/caption]


#### 如何避免


要理智地使用测量和数字，而非盲目。


#### 例子和信号


使用代码行数、提交次数等来评判程序员的效率。通过员工呆在公司的小时数来测量他们的贡献。


#### 棘手的地方


运营规模越大，需要做出决策的数字就越高，这意味着自动化和盲目依赖数字做决策开始蔓延到过程里了。


#### 总结


让数字告知你的决策，而不是决定它们。


### 无用的（幽灵）类




<blockquote>“达到完美，貌似不是在没有什么更多的要添加的时候，而是在没有什么更多的要去掉的时候。” ------Antoine de Saint Exupéry</blockquote>




#### 意思


无用类本身没有真正的责任，经常用来指示调用另一个类的方法或增加一层不必要的抽象层。


#### 糟糕的原因


幽灵类增加了复杂度、要维护和测试的额外代码，降低了代码可读性------读者首先需要意识到幽灵类做了什么，它们经常几乎没有用处，然后培养自己在精神上用实际处理该责任的类取代幽灵类的使用。


#### 如何避免


不要写无用类，或者通过重构来消除它们。Jack Diederich 的题为“[Stop Writing Classes](https://www.youtube.com/watch?v=o9pEzgHorH0)”就是和这种反面模式相关的。


#### 例子和信号


多年前，我正忙于我的硕士学位，当时是大一 Java 编程课的助教。在其中一个实验课上，我收到了实验材料，是关于使用链表来实现栈的主题。我还被提供了“答案”的参考。下面是给我的答案，一个 Java 文件，几乎没做改动（限于篇幅我删除了注释）：

    
    import java.util.EmptyStackException;
    import java.util.LinkedList;
    
    public class LabStack<T> {
        private LinkedList<T> list;
    
        public LabStack() {
            list = new LinkedList<T>();
        }
    
        public boolean empty() {
            return list.isEmpty();
        }
    
        public T peek() throws EmptyStackException {
            if (list.isEmpty()) {
                throw new EmptyStackException();
            }
            return list.peek();
        }
    
        public T pop() throws EmptyStackException {
            if (list.isEmpty()) {
                throw new EmptyStackException();
            }
            return list.pop();
        }
    
        public void push(T element) {
            list.push(element);
        }
    
        public int size() {
            return list.size();
        }
    
        public void makeEmpty() {
            list.clear();
        }
    
        public String toString() {
            return list.toString();
        }
    }


你能想象出我看到这个参考答案的困惑，试图搞清楚 `LabStack` 类是做什么的，以及学生应该从这个毫无意义的练习中学到什么。在本例中，这个类的错误不是太明显，它绝对没有意义！它只是通过实例化的 `LinkedList` 对象传递调用。这个类修改了很多方法的名字（比如把通用的 `clear` 换成 `makeEmpty`），这只会让用户困惑。错误检查逻辑完全不必要，因为 `LinkedList` 里的方法已经做了同样工作（但是抛出了一个不同的异常，`NoSuchElementException`，这是又一个可能困惑的地方）。直到今天，我还是无法想象当学生拿到这份实验材料时，作者会作何感想。当你看到和上例相似的类时，重新考虑一下，它们是否真的需要。


#### 棘手的地方


这里的建议初看起来和“害怕新增类”的建议相矛盾。重要的是要明白，类在什么时候发挥着有价值的角色和简化设计，而不是无谓地增加复杂度却没有得到益处。


#### 总结


避免没有真正责任的类。



* * *






	
  * 注1：在软件工程中，一个反面模式（anti-pattern或antipattern）指的是在实践中明显出现但又低效或是有待优化的设计模式，是用来解决问题的带有共同性的不良方法。它们已经经过研究并分类，以防止日后重蹈覆辙，并能在研发尚未投产的系统时辨认出来。[http://zh.wikipedia.org/wiki/%E5%8F%8D%E9%9D%A2%E6%A8%A1%E5%BC%8F](http://zh.wikipedia.org/wiki/%E5%8F%8D%E9%9D%A2%E6%A8%A1%E5%BC%8F)

	
  * 注2：西里尔·诺斯古德·帕金森以人们对于单车车库（bike shed）与核子反应堆的意见作为例子来说明，对于价格不高、无特别影响力的脚踏车车库，因为人人都认为自己了解，所以会花费很多时间在讨论要为脚踏车车库漆上什么颜色；但对于造价高昂、影响力大的核子反应堆，因为与日常生活距离太远，技术上又困难，人们反而不会提出什么意见，就轻易让它通过。因此这个定理又称车库颜色效应（ "color of the bike shed" effect）。[http://zh.wikipedia.org/wiki/%E5%B8%95%E9%87%91%E6%A3%AE%E7%91%A3%E7%A2%8E%E5%AE%9A%E7%90%86](http://zh.wikipedia.org/wiki/%E5%B8%95%E9%87%91%E6%A3%AE%E7%91%A3%E7%A2%8E%E5%AE%9A%E7%90%86)

	
  * 注3：在面向对象编程领域, 一个上帝对象是一个了解过多或者负责过多的对象。 上帝对象是反面模式的一个例子。
结构化编程背后的基本概念是一个大型的问题应该被分解成为多个较小的问题中（分而治的策略）并且针对每个较小的问题提出解决方案。当每个小问题都得到解决后，大问题本体就得到了解决。[http://zh.wikipedia.org/wiki/%E4%B8%8A%E5%B8%9D%E5%AF%B9%E8%B1%A1](http://zh.wikipedia.org/wiki/%E4%B8%8A%E5%B8%9D%E5%AF%B9%E8%B1%A1)

	
  * 注4：程式设计中所谓的魔术数字（magic number）是指直接写在程式码里的具体数值（如“10”“123”等以数字直接写出的值）。虽然程式作者写的时候自己能了解数值的意义，但对其他程式员而言，甚至制作者本人经过一段时间后，会难以了解这个数值的用途，只能苦笑讽刺“这个数值的意义虽然不懂，不过至少程式能够执行，真是个魔术般的数字”而得名。[http://zh.wikipedia.org/wiki/%E9%AD%94%E8%A1%93%E6%95%B8%E5%AD%97](http://zh.wikipedia.org/wiki/%E9%AD%94%E8%A1%93%E6%95%B8%E5%AD%97)。 关于魔幻字符串（Magic strings），尚无词条，只有一句解释“直接在代码里使用常量字符串，例如用来比较，或是作为事件代码”。考虑到原文将数字和字符串放在了一起，就翻译为“魔术数字和字符串”

	
  * 注5：文中引用的关于Tim Peters的《Python之禅》的句子，引用了赖勇浩的翻译。请参考 [http://www.douban.com/group/topic/3740034/](http://www.douban.com/group/topic/3740034/)

	
  * 注6：在维基“反面模式”词条中，有如下引用：目标管理（Management by objectives）：通过数字管理，过于关注非本质而或不易取得的数字指标。而目标管理的词条地址为：[http://zh.wikipedia.org/wiki/%E7%9B%AE%E6%A8%99%E7%AE%A1%E7%90%86](http://zh.wikipedia.org/wiki/%E7%9B%AE%E6%A8%99%E7%AE%A1%E7%90%86)。目标管理（英语：Management by objectives，简称MBO）是1960年代末期之后迅速发展的企业管理理论之一，首先提出者为彼得·杜拉克。

	
  * 注7：观察者期望效应是认知偏见的一种。在科学实验中，由于观察者预期某些测试结果，于是无意识地以某种形式操纵了实验步骤，或错误解释实验结果以达至他们希望得到的结论。观察者期望效应能严重歪曲实验结果，因此需利用双盲方式进行实验来消除这效应。[http://zh.wikipedia.org/wiki/%E8%A7%80%E5%AF%9F%E8%80%85%E6%9C%9F%E6%9C%9B%E6%95%88%E6%87%89](http://zh.wikipedia.org/wiki/%E8%A7%80%E5%AF%9F%E8%80%85%E6%9C%9F%E6%9C%9B%E6%95%88%E6%87%89)

	
  * 注8：在程式设计中，幽灵（poltergeist）是指一些生命期很短，没有内部状态的物件，这些物件是只用来进行初始化或调用其他生命期较长物件的方法。幽灵是一种反面模式。原始定义是由 Michael Akroyd 于1996年在Object World West Conference中提出。[http://zh.wikipedia.org/wiki/%E5%B9%BD%E7%81%B5_(%E5%8F%8D%E9%9D%A2%E6%A8%A1%E5%BC%8F)](http://zh.wikipedia.org/wiki/%E5%B9%BD%E7%81%B5_(%E5%8F%8D%E9%9D%A2%E6%A8%A1%E5%BC%8F))

	
  * 注9：认知偏误是在某些特定情况下的特定的思考、行为倾向，会导致理性或判断产生系统性偏误，这些现象广泛受到心理学与行为经济学研究。[http://zh.wikipedia.org/wiki/%E8%AA%8D%E7%9F%A5%E5%81%8F%E8%AA%A4%E5%88%97%E8%A1%A8](http://zh.wikipedia.org/wiki/%E8%AA%8D%E7%9F%A5%E5%81%8F%E8%AA%A4%E5%88%97%E8%A1%A8)


