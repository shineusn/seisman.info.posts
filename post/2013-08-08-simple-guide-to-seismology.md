---
title: 地震学入门简易指南
date: 2013-08-08
lastmod: 2014-07-07
author: SeisMan
categories:
  - 胡言乱语
tags:
  - 笔记
slug: simple-guide-to-seismology
---

写下标题《地震学入门指南》之后，觉得这个标题写得太大，我有些 hold 不住，所以加上了 “简易” 二字。
这里所说的地震学，专指天然地震学（勘探地震学不在讨论之列）。进入地震学，需要掌握地震学相关的基础知识、
了解地震学的前沿进展，同时需要掌握一些数据处理、分析相关的工具。这里只谈一谈天然地震学需要掌握的一些
工具与计算机技能。

<!--more-->

## 写在前面

### 受众

这篇博文的主要受众是还没开始正式接触科研或刚刚接触科研的人，即大三大四的本科生以及研一新生，希望能够
在方向上给予指引；已经入门的人，或许可以看看有没有提到一些你还不知道的工具；地震学的牛人们，如果有
其他的想法和建议，也欢迎不断完善。

### 为什么要学习工具？

有些人认为，做科研最重要的是 idea，工具什么的都不重要。我个人是很反对这样一个观点的。idea 本身是
很重要的，但是如何将 idea 快速、准确地转换成科研成果，则需要自己有足够的知识积累以及足够的工具支持。

同样要完成一件事情，没有工具的人可能需要做一天的重复劳动，有工具的人则可能借助于工具几分钟解决问题，
这就是效率上的差异，很多时候科研成果也是要拼速度的，不是吗？

因为**工具可以提高我们的效率**，所以值得学习。

### 要学习哪些工具？

各类工具那么多，究竟要学习哪些？要学习多少工具？

这其实是个很难回答的问题。过分地关注于工具的学习，会导致科研的时间被压缩；而不去认真学习这些工具，
科研的效率又无法提升上去。这是一个矛盾，需要自己去权衡。

我个人的态度是，首先掌握最基础的工具，在此基础上，多接触其它工具、软件和代码，不求每个工具都搞明白，
至少花一点点时间看看 README，了解**其可以做什么**。在需要的时候第一时间判断哪个工具可以满足当前的需求。

## Linux 基础

选择 Linux 还是 Windows？这个话题曾经在网上吵得很热，也许现在还有人在争论。就地震学而言，使用 Linux 的
优势要远远高于使用 Windows，原因简单列举如下：

-   大多数地震学专用的软件都是在 Linux 下开发的，然后再移植到 Windows 下，因而这类软件在 Windows 下
    相对来说有更多的 Bug；
-   很多开源的代码是在 Linux 下写的，然后用 `gcc` 或 `gfotran`
    编译的。理论上，只要程序写的时候考虑的可移植性，在 Windows 下编译是没有问题的，但实际上大多
    数代码都需要经过一番修改；
-   Windows 自带了批处理工具（Batch）以及 Shell（PowerShell），可以用于完成数据的批处理；
    但前者功能太单一，后者用的人又很少，所以两者都不是合适的选择；
-   Linux 下自带了多种 Shell（Bash、csh、zsh），以及多个适合数据处理的工具，非常适合用于科研。

要学习 Linux，首先要选择合适的发行版：Ubuntu、Debian 和 Fedora 应该算是比较适合新手的发行版。刚
接触 Linux 的新手可以考虑在虚拟机中安装不同的发行版，每个都尝试一下，找到最适合自己的就好。选择好发
行版之后，还要对发行版的版本代号有一些了解。以 Ubuntu 为例，对于 12.04 和 14.04 是长期支持版，支持周期
为 5 年，而其他版本的支持周期只有一年多。我遇到不少目前还在用 Ubuntu 13.10 的人，（13.10 在 2014 年 7 月
便不再被支持）。这就是在给自己挖坑，系统用的时间越长，重装的代价就越高，想要重装的欲望就越低，重装时
数据丢失的风险也越大。

接下来要选择合适的入门书籍：国内推荐的比较多的是《鸟哥的 Linux 私房菜 -- 基础学习篇》，个人觉得其语言
过于啰嗦，知识点对于新手来说稍显繁杂；另一本推荐的比较多的是开源的《The Linux Command Line》，
该书有 [中文译本](http://billie66.github.io/TLCL/)。注意，要读的是介绍 Linux 的书，而不是
任何介绍 Linux 发行版的书。

对于 Linux 入门需要了解的知识点包括：

-   了解 Linux 的历史，以及 Linux 与各个发行版之间的联系；
-   熟悉 Linux 的目录树，习惯使用命令行，掌握基本命令 `cd` 、 `pwd` 、`mkdir` 、 `rmdir`、 `ls` 、 `cp` 、 `rm` 、 `mv` 的基本用法；
-   理解绝对路径和相对路径；
-   理解环境变量 `PATH` 的作用；
-   理解 Linux 文件权限 `rwx` ，掌握 `chmod` 命令；
-   其他几个有用的命令： `cat` 、 `touch` 、 `head` 、 `tail` 、 `which` 、 `locate`
-   符号链接 `ln` 与挂载 `mount` ；
-   了解最基本的 vi 编辑器的使用，因为很多时候 vi 是服务器上唯一能使用的编辑器；
-   掌握至少一种高级编辑器的使用，如 vim、emacs、sublime text、atom。怎样才叫掌握？这个问题
    没有标准答案，选择其中一个一直用下去，遇到需要重复劳动或者不顺心的地方就去找各种插件配置一下。
    像 gedit 这种编辑器不用也罢，用它来写程序效率太低；
-   理解 `~/.bashrc` 文件的作用；
-   理解并学会使用数据流重定向；
-   理解管道的作用及其用途；
-   Linux 通配符；
-   掌握压缩相关命令 `tar` 、 `gzip` 、 `bzip2` ，其实最主要的是 `tar` 命令的两种常用方式： `-zxvf` 和 `-jxvf` ；
-   与数据处理相关的命令： `awk` 、 `cut` 、 `grep` 、 `wc` 、 `sort` 、`uniq` ；

PS：严格地说， `awk` 已经不单单是一个命令，更像是一种微型语言了。

## 高级编程语言

C 应该是目前地震学界目前最常用的编程语言，一些老的代码可能用 Fortran 比较多，现在也有一些人使用 Java。

使用哪种高级编程语言并不重要。高级编程语言至少需要熟练使用一种，同时最好能够了解一些其它语言的语法，
这样可以更轻松的阅读别人的代码。

大学阶段应该都学过谭浩强写的 C 语言，这本书过分强调了一些不重要的东西，有些错误和误导之处，因而找
一本权威的 C 语言书籍重新复习、巩固和整理编程知识是很重要的。

在掌握了语言的基本语法的同时，还要确定自己的编程风格、注释风格以及代码管理方式，同时需要了解一些编译相关的知识：

-   最基本的编译器选项，比如 `-c` 、 `-o` 、 `-g` 、 `-I` 、 `-L` 、
    `-l` ；
-   编译、链接及运行的基础知识，理解头文件、库文件在编译、链接和执行过程中的作用。这部分很重要，
    因为平常编译源码过程中出现最多的错误除了语法问题就是编译链接问题；
-   makefile：实现编译的自动化，比较流行的入门手册是《[跟我一起学 Makefile](/how-to-write-makefile/)》，
    基本上前 8 章的内容就已经足够了；

当然，也有些组只用 Matlab 就可以完成绝大部分任务，这个得看组内的传统。

## 脚本语言

### Bash 及其相关

Bash 其实本身只是一个空壳，具有最基本的条件判断和循环功能。除此之外，日常需要的数据处理、字符串处理，
都需要借助于 Linux 下的其他命令，比如 `cat` 、 `awk` 、 `grep` 、 `cut` 、 `paste` 等等。
因而除了 bash 脚本自身的功能以外，还需要了解的工具包括:

-   `awk` ：文本处理工具；
-   `sed` ：流编辑器
-   `printf` ：格式打印；
-   `grep` ：正则表达式匹配；
-   正则表达式；

在科研过程中不推荐使用 Bash 脚本，因为 Bash Shell 与 awk 等命令本质上是独立的个体，二者在设计上有很多
不一致的地方，且 awk 等命令在设计的时候明显有向 Shell 妥协的意味。总之，Bash 脚本中坑比较多，仅仅适合
用几行就可以搞定的情况。

### Perl 或 / 和 Python

Perl 和 Python 是另外两种常见的脚本语言。在学会了 Bash 脚本以及相关的各种工具之后为什么还要学习新的
脚本语言呢？因为 Bash 虽然作为 Linux 下最底层最常用的脚本语言，但是其功能过于依赖于外部工具，且难以
实现更加复杂的功能。Perl 和 Python 可以完全自给自足，其内部完全实现了 awk、grep 等工具的功能，
且速度很快，更重要的是 Perl 和 Python 具有模块功能，可以从网上下载各种别人已经写好的模块来实现几乎
所有自己想要的功能。因而 Perl/Python 实际上比 Bash 功能更强大，学起来也并不难。如果有心学习
Perl/Python 的话，可以简单了解 bash 相关知识，然后直接进入更高级的脚本语言。

就目前的情况来看，Perl 适合日常的简单的数据处理，而 Python 适合完成各种复杂的工作同时也适合进行
科学计算。对于新手，更推荐学习 Python。当然最好 Perl 也懂一些，技多不压身嘛。

## SAC

SAC 是地震学的最常用的数据处理软件。关于 SAC，可以参考本博客的《SAC 参考手册》。

SAC 基础：

-   阅读 SAC 文件格式，理解 SAC 文件的二进制存储，理解 SAC 头段变量的含义；
-   SAC 常用基本命令；

SAC 进阶：

-   SAC 变量；
-   SAC 内置函数；
-   SAC 宏以及脚本调用；
-   调用 SAC 提供的库读写 SAC 文件；
-   利用 Prof. Lupei Zhu 的 `sacio.c` 读写 SAC 文件；
-   学习并掌握 saclst 的用法；

## GMT

GMT 是地震学领域最常用的绘图软件。GMT 很重要，但是又没那么重要。其重要之处在于数据处理的最终结果要
通过图像的形式表现出来，而 GMT 在某些时候是最佳的工具，其不重要之处在于入门前期基本不太需要绘图。

GMT 基础：

GMT 入门的最好方法大概就是阅读《GMT Technical Reference and Cookbook》了；

-   掌握最常用的 GMT 选项；
-   将所有的投影方式看一遍，对每种投影方式的结果有些印象即可；
-   简单浏览所有命令，大概知道每个命令的功能；
-   浏览 GMT 提供的 30 个例子，对每个例子有印象，必要的时候再翻看，同时巩固 bash 脚本的知识；

GMT 进阶：

-   熟悉 GMT 的常用命令及其每个选项；
-   熟悉 GMT 的全部命令；
-   查看相关代码，理解一下内部机制

## 其他计算机技能

### Git

对于经常写代码的人来说，在修改代码之前都会把原始代码备份一下，以防止一时糊涂把好代码给改坏了。备
份的次数多了，自己也就乱了。所以经常写代码的人，需要学会版本控制。

Git 是目前最流行的版本控制软件。学会使用 Git 之后，就可以随心所欲的修改代码而不必担心把代码改坏了。

Git 学起来很简单，几乎几分钟就可以学会使用基本功能，当然高级些的功能还是需要看看教程的。

-   [Git 简易指南](http://www.bootcss.com/p/git-guide/)
-   [廖雪峰的 Git 教程](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000)
-   [Pro Git 中文版](http://git-scm.com/book/zh)

## 其他相关

-   pssac：利用 GMT 的绘图库绘制 SAC 文件的命令；
-   TauP：计算到时等等信息的工具；
-   仪器响应：理解仪器响应是正确数据处理的基础；