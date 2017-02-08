---
author: viviworld
comments: true
date: 2015-04-20 00:46:03+00:00
excerpt: 但是，当我开始应用代码大全里学到的东西，开始编写经常比我之前写的注释还要整洁的代码时，我意识到，我给那些接手我代码的人所帮的忙，要比单纯地写注释更有益处。我正在让我的代码更加整洁。
layout: post
link: http://www.labazhou.net/2015/04/why-comments-are-stupid-a-real-example/
slug: why-comments-are-stupid-a-real-example
title: 一个实例：为什么注释是愚蠢的
wordpress_id: 1884
categories:
- 编程
tags:
- .net
- 代码
- 代码大全
- 注释
- 重构
---


	
  * 原文地址（original source）：[http://simpleprogrammer.com/2015/04/13/why-comments-are-stupid-a-real-example/](http://simpleprogrammer.com/2015/04/13/why-comments-are-stupid-a-real-example/)

	
  * 作者（author）：[https://twitter.com/jsonmez](https://twitter.com/jsonmez)





* * *



当我写[一篇文章](http://simpleprogrammer.com/2015/03/16/11-rules-all-programmers-should-live-by/)、或制作一个 [YouTube 视频](https://www.youtube.com/watch?v=ErW6fEvulAc)，提及大部分情况下注释不是必需的以及实际上弊大于利时，没有什么比这更能激起宗教式讨论了。

在我读《[代码大全](http://www.amazon.com/gp/product/0735619670/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0735619670&linkCode=as2&tag=makithecompsi-20&linkId=XRVP7LFMXGGPFZPK)》第二版时，我首先转到这个讨论的侧面。

在那本书，Steve McConnell 相当详实整洁地给我阐明我在代码放入如此多注释的原因：



	
  * 我的命名没有采用让解释型注释成为不必要的方式。

	
  * 我的方法和函数过于庞大，而需要额外的解释。


我写代码的方式发生了巨大的变化。

我相信我过去做得还不错，通过写注释解释我的代码、让下一个开发人员更容易地理解它们，使我成为一名本分的程序员。

但是，当我开始应用[代码大全](http://www.amazon.com/gp/product/0735619670/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0735619670&linkCode=as2&tag=makithecompsi-20&linkId=XRVP7LFMXGGPFZPK)里学到的东西，开始编写经常比我之前写的注释还要整洁的代码时，我意识到，[我给那些接手我代码的人所帮的忙](http://www.labazhou.net/2013/12/say-welcome-to-someone-who-repalces-you/)，要比单纯地写注释更有益处。我正在让我的代码更加整洁。

当我读 Uncle Bob 【注1】的《[代码整洁之道](http://www.amazon.com/gp/product/0132350882/ref=as_li_tl?ie=UTF8&camp=1789&creative=390957&creativeASIN=0132350882&linkCode=as2&tag=makithecompsi-20&linkId=OE6W2DLW3J5Z2TNZ)》一书时，我的观点进一步加强了。

Uncle Bob 不仅仅说我们应该避免注释，还说了------并且演示了------注释多半是怎样在表达代码意图上失败的。

Bob 让我意识到我仍然在深入学习注释，我需要进一步提高我的命名，努力让我的代码无需外在帮助就能交流意图。


### 演示真实的移除注释的例子


这是我自己的个人发展------我不期望每个人都和我有同样的经历，或看到同样的方式------但是，我觉得当我提起更多的会沟通的代码（communicative code）、注释通常应该避免时，还会有大量的无知要吐出来。

过了一会儿，我觉得有必要支撑一下我要说的东东。

对我而言，赞美整洁、会沟通代码的价值是一回事，而像 Uncle Bob 所定义的“整洁”，相较于过度注释的、同等“优秀”的代码，清晰的代码是多么地更容易被人理解和维护。

起初我打算编造一些代码例子向你演示这种情况。

我打算写一些代码，有着不好的命名、充满了注释，然后向你演示我是怎样重构代码以除掉这些注释并真正增加清晰程度。

但是，据我经验看，这是一个陷阱。

很多人将吐槽、指责我设立了一个“稻草人”，它无法代表真实世界的代码。

幸运的是，我意识到一个绝佳机会正向我走来。


### 重构来自 .NET 框架的真实代码


自从微软决定开源整个 .NET 代码库后，我决定不去挑选一段不太糟糕的真实代码示例，而要挑选可以被重构以消除代码、且仍然让代码清晰的例子------据我看，要更清晰。

我决定“挑选”的这段代码[位于这里](https://github.com/dotnet/corefx/blob/master/src/System.IO.FileSystem/src/System/IO/PathHelpers.cs)。

我仅仅摘出这段代码里的一个方法，`SplitDirectoryFile`，来阐明我的观点。

我不知道这段代码的作者，甚至不认为这段代码是糟糕的。我只是用它作为示例，请记住这一点。

我挑选一个相当小的方法，这样容易被理解，并适合本文，但是我的总体方法可以应用到更大型的代码样本里。

在我重构之前，让我们先看看这段代码：

    
    internal static void SplitDirectoryFile(string path, out string directory, out string file)
    {
        directory = null;
        file = null;
     
        // assumes a validated full path
        if (path != null)
        {
            int length = path.Length;
            int rootLength = GetRootLength(path);
     
            // ignore a trailing slash
            if (length > rootLength && EndsInDirectorySeparator(path))
                length--;
     
            // find the pivot index between end of string and root
            for (int pivot = length - 1; pivot >= rootLength; pivot--)
            {
                if (IsDirectorySeparator(path[pivot]))
                {
                    directory = path.Substring(0, pivot);
                    file = path.Substring(pivot + 1, length - pivot - 1);
                    return;
                }
            }
     
            // no pivot, return just the trimmed directory
            directory = path.Substring(0, length);
        }
        return;
    }


正如我上面说的，这段代码还不错。

它相当清晰地表达了要实现的功能。

注释甚至更加明确。

但是，我们能够消除所有注释并真正让代码更加易懂吗？

咱们从第一行注释开始。它貌似非常无辜。

    
    // assumes a validated full path


在这段代码里，存在我们可以讨论的方式吗？


### 用更好的参数名取代注释


如果我们把变量名从 path 改成 validatedFullPath，会怎样呢？

    
    internal static void SplitDirectoryFile(string validatedFullPath, out string directory, out string file)
    {
        directory = null;
        file = null;
     
        if (validatedFullPath != null)
        {
            int length = validatedFullPath.Length;
            int rootLength = GetRootLength(validatedFullPath);
     
            // ignore a trailing slash
            if (length > rootLength && EndsInDirectorySeparator(validatedFullPath))
                length--;
     
            // find the pivot index between end of string and root
            for (int pivot = length - 1; pivot >= rootLength; pivot--)
            {
                if (IsDirectorySeparator(validatedFullPath[pivot]))
                {
                    directory = validatedFullPath.Substring(0, pivot);
                    file = validatedFullPath.Substring(pivot + 1, length - pivot - 1);
                    return;
                }
            }
     
            // no pivot, return just the trimmed directory
            directory = validatedFullPath.Substring(0, length);
        }
     
        return;
    }


没有太大差异------太琐碎------但是，我们不但消除了一行注释，我们也让调用这个方法的人能够根据变量名辨认出，它们不只是传递过来的 path，而是验证过的 full path。

重申，这貌似是个相当小的修改，但是，我相信它让代码更清晰了。


### 稍微大点儿的改动……


继续，我们可以看到下面的注释：

    
    // ignore a trailing slash


现在，我们有了处理这种情况的一些方法。

我们可以用一种方法简单地取代注释，因此有了：

    
    if (ShouldIgnoreTrailingSlash(length, rootLength, validatedFullPath)
    
        length–;


我们还可以创建简单的布尔变量来取代注释：

    
    bool ShouldIgnoreTrailingSlash = length > rootLength && EndsInDirectorySeparator(validatedFullPath);
    
    if(ShouldIgnoreTrailingSlash)
    
        length–;


另外，或许更好的可能性就是下面的方法：

    
    length = LengthWithoutTrailingSlash(length, rootLength, validatedFullPath);


不过，我看到了一个机会，那就是改善整体阅读性和代码结构，并去掉注释。

这次该怎样重构呢？

    
    public class DirectoryFileSplitter
    {
        private readonly string validatedFullPath;
        private int length;
        private int rootLength;
     
        public DirectoryFileSplitter(string validatedFullPath)
        {
            this.validatedFullPath = validatedFullPath;
        }
     
        public void Split(out string directory, out string file)
        {
            directory = null;
            file = null;
     
            if (validatedFullPath != null)
            {
                length = validatedFullPath.Length;
                rootLength = GetRootLength(validatedFullPath);
     
                IgnoreTrailingSlash();
     
                // find the pivot index between end of string and root
                for (int pivot = length - 1; pivot >= rootLength; pivot--)
                {
                    if (IsDirectorySeparator(validatedFullPath[pivot]))
                    {
                        directory = validatedFullPath.Substring(0, pivot);
                        file = validatedFullPath.Substring(pivot + 1, length - pivot - 1);
                        return;
                    }
                }
     
                // no pivot, return just the trimmed directory
                directory = validatedFullPath.Substring(0, length);
            }
     
            return;
        }
     
        private void IgnoreTrailingSlash()
        {
            if (length > rootLength && EndsInDirectorySeparator(validatedFullPath))
                length--;
        }
    }


或许做得过度了，但是我认为把原来的静态方法放到一个实际的类里，要清晰很多。

然后我们可以非常清晰地说明该类应该做什么，并利用类的状态来简化代码。

尽量整洁地移除代码，导致我重构了这个方法本身，因为我发现，表达这个意图的最清晰方式就是将其封装。

现在，你或许认同了这种特定的重构------还不错------但是我确信，你仍然想看到我们是怎样通过更清晰地表达代码意图来轻松地去除注释的。


### 现在容易了


去除剩下的注释就有些琐碎了：

    
    // find the pivot index between end of string and root


我们所有不得不要做的修改就是将其改成刚才提到的方法。

    
    public class DirectoryFileSplitter
    {
        private readonly string validatedFullPath;
        private int length;
        private int rootLength;
        private bool pivotFound;
        public string Directory { get; set; }
        public string File { get; set; }
     
        public DirectoryFileSplitter(string validatedFullPath)
        {
            this.validatedFullPath = validatedFullPath;
            length = validatedFullPath.Length;
            rootLength = GetRootLength(validatedFullPath);
        }
     
        public void Split()
        {
            if (validatedFullPath != null)
            {
                IgnoreTrailingSlash();
     
                FindPivotIndexBetweenEndOfStringAndRoot();
     
                // no pivot, return just the trimmed directory
                if(!pivotFound)
                    Directory = validatedFullPath.Substring(0, length);
            }
     
            return;
        }
     
        private void FindPivotIndexBetweenEndOfStringAndRoot()
        {
            for (int pivot = length - 1; pivot >= rootLength; pivot--)
            {
                if (IsDirectorySeparator(validatedFullPath[pivot]))
                {
                    Directory = validatedFullPath.Substring(0, pivot);
                    File = validatedFullPath.Substring(pivot + 1, length - pivot - 1);
                    pivotFound = true;
                }
            }
        }
     
        private void IgnoreTrailingSlash()
        {
            if (length > rootLength && EndsInDirectorySeparator(validatedFullPath))
                length--;
        }
    }


我仍然忍不住继续修改这个结构。

我把 `Directory` 和 `File` 移到了类的属性，而不是方法的参数。

但是，这没有移除注释和用方法取代它重要，然而在逻辑之上提供了一种抽象。

我还把找到 `pivot` 的方式挪到了变量里，因此我们可以显式地使用其状态，而不是依靠之前的 `return`。（甚至都不用一行注释来解释）

现在意图更加清晰了。如果我们找不到 pivot，就只返回 `trim` 过的目录。


### 最终重构


我们来到了最终的重构：

    
    public class DirectoryFileSplitter
    {
        private readonly string validatedFullPath;
        private int length;
        private int rootLength;
        private bool pivotFound;
        public string Directory { get; set; }
        public string File { get; set; }
     
        public DirectoryFileSplitter(string validatedFullPath)
        {
            this.validatedFullPath = validatedFullPath;
            length = validatedFullPath.Length;
            rootLength = GetRootLength(validatedFullPath);
        }
     
        public void Split()
        {
            if (validatedFullPath != null)
            {
                IgnoreTrailingSlash();
     
                FindPivotIndexBetweenEndOfStringAndRoot();
     
                if(!pivotFound)
                    TrimDirectory();
            }
        }
     
        private void TrimDirectory()
        {
            Directory = validatedFullPath.Substring(0, length);
        }
     
        private void FindPivotIndexBetweenEndOfStringAndRoot()
        {
            for (int pivot = length - 1; pivot >= rootLength; pivot--)
            {
                if (IsDirectorySeparator(validatedFullPath[pivot]))
                {
                    Directory = validatedFullPath.Substring(0, pivot);
                    File = validatedFullPath.Substring(pivot + 1, length - pivot - 1);
                    pivotFound = true;
                }
            }
        }
     
        private void IgnoreTrailingSlash()
        {
            if (length > rootLength && EndsInDirectorySeparator(validatedFullPath))
                length--;
        }
    }


我们简单地抽出了 trim 过的目录，放到一个可以确切表明意义的方法里。

现在，据我看，这段代码已经非常清晰了，并且零注释。

我快速地浏览这段代码，就理解了它的功能。

这种结构和变量、方法的命名，比原来代码里的注释所要表达的意义，更加精确和清晰。


### 比较和对比


看下原来的代码和这份重构的代码，你认为哪一个版本更易于理解和维护。

尤其要比较实现每种功能的主要方法：

    
    internal static void SplitDirectoryFile(string path, out string directory, out string file)
    {
        directory = null;
        file = null;
     
        // assumes a validated full path
        if (path != null)
        {
            int length = path.Length;
            int rootLength = GetRootLength(path);
     
            // ignore a trailing slash
            if (length > rootLength && EndsInDirectorySeparator(path))
                length--;
     
            // find the pivot index between end of string and root
            for (int pivot = length - 1; pivot >= rootLength; pivot--)
            {
                if (IsDirectorySeparator(path[pivot]))
                {
                    directory = path.Substring(0, pivot);
                    file = path.Substring(pivot + 1, length - pivot - 1);
                    return;
                }
            }
     
            // no pivot, return just the trimmed directory
            directory = path.Substring(0, length);
        }
     
        return;
    }



    
    public void Split()
    {
        if (validatedFullPath != null)
        {
            IgnoreTrailingSlash();
     
            FindPivotIndexBetweenEndOfStringAndRoot();
     
            if(!pivotFound)
                TrimDirectory();
        }
    }


是的，我修改了代码结构，让其变成了类，我用属性取代了输出参数，但是我达到了类似的结果，消除注释、用更有表现力的代码和变量命名取代了注释。（尽管如此，在特定情况下，我将承认输出参数会增加代码难度。）


### 没有注释的代码更容易维护


然而，我要说的是，尽量用代码表达的方式编写代码而非依靠注释，使你以更好的方式构造代码，这会因此产生更加内敛的类和更好的总体结构。

不管你是否认为我这样做得更好，你或许同意的一个地方就是，我肯定没有使其变得更糟。

如果你把有注释的代码重构为没有注释的代码、且没有损失清晰度，在我看来就是最大的胜利，因为代码被更新了，注释却没有。（至少它们经常没有）

记住，这是一些已经得体的代码示例，这里的注释不是非常不相关的。

我见过的大部分注释的代码看起来根本不是这样。

代码中的变量已经有着非常好的命名，注释描述了逻辑要做的事情，而不是它是怎样做到的。

我见过的大部分带注释的代码，使用注释做为代码的支撑，一点都不清晰。

因此，在某种意义上说，我挑了一个糟糕的例子。

我没有挑选带有糟糕注释的丑陋代码，并通过移除它们让代码更好------这应该也不难。

不管怎么说，我静候着愤怒评论家们的猛烈攻击（没有别的意思）。

你是怎么看的？

我已经完全说服你了吗？

你至少看到了编写没有注释的代码不是懒惰、而是真正有益处的------或者至少是一种偏好？



* * *






	
  * 注1：Robert Cecil Martin (colloquially known as Uncle Bob) is an American software engineer and author. [http://en.wikipedia.org/wiki/Robert_Cecil_Martin](http://en.wikipedia.org/wiki/Robert_Cecil_Martin)


