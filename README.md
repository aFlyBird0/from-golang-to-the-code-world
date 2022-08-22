# From Golang to the Code World

## 我是谁

如题，这是一个为编程零基础同学准备的从 Go 语言入门编程的小册子。

## 我从哪来

Bird 参与了社团（杭电助手）的学习平台（主要面向新大一）的建设，在建设初期需要准备 Go 语言的基础入门教程。

我们本觉得现在的教程已经够丰富了，可以直接丢给新人看。也能省去我们自己「宝贵」的时间。

但现在的教程大多又臭又长，以及绝大多数 Go 语言的教程都假设读者已经学会了其他语言，即已经有了基本的编程思想。

于是我们决定到处找合适的教程，做一个缝合者，删减与增补多个教程，做成我们自己的教程。

但今晚，也就是2022年08月22日的凌晨，Bird 在和一位叫 ZZM（from SRT社团） 的奇人聊了一会后，被他的格局所感动。

**既然别人的教程都对新人不友好，为什么不自己动手搞一个心目中的完美的Go入门教程？**

**这不正是自己所热爱的吗？**

## 我长什么样

（即，看完这个小册子，你能获得什么）

* 首先，**看完这个教程，并不能让你学会 Go 语言**，你甚至可能写不出一行代码

我认为，比学语言本身更重要的，是如何去 **「理解编程是什么」，去学「怎么学编程」**。

所以，我会像 Go 语言本身的小而美那样，

* 介绍 Go 语言或者说一门编程语言最核心的东西
* **并传授给你能看得下去其他教程的能力**

「From Go」由我来做，「to the Code World」就交给你了。

## 特此正名

Go 语言的正式、官方、真正的名字就是「Go语言」。Golang 只是一个小名，据说为了搜索引擎能更精确地搜到。

我给这个小册子起名用「Golang」原因类似，不然名字就会变成：「from go to the code world」，go-to。

## 为什么？

因为热爱、因为梦想，因为开源是程序员的浪漫。欢迎贡献（PR、Issue等）。

## 关于目录

本目录主要基于 [Go 语言官方教程](https://tour.go-zh.org/)，有一定修改。所以建议读者看到第一章后，边看这个小册子边对着教程相应的章节去学习正经的代码语法和敲代码。

但是官方的 Go 语言教程有点简单，推荐同时学习[菜鸟教程](https://www.runoob.com/go/go-tutorial.html)的对应章节，这是一个神奇的几乎拥有所有语言和工具的零基础教程的网站。不评价它的质量如何，但它能恰到好处地讲解每门编程语言所需要知道的核心概念，非常适合新手入门。

菜鸟教程里有部分章节比较「迂腐」，比如安装 Go 语言环境，或者说有些东西太细了没必要现在学。如果冲突和我说的比较大的，建议暂时以我的为准，主要是我会选取尽可能简单的路线来带着入门。也可以通过各种方式联系 Bird （例如邮件、QQ群，不要直接打电话哪怕你真的是个猛人能搞到我电话）以确认，我们共同完善。

## 目录

* 章节〇
  * [引子](./引子.md)
  * [编译器与代码](./编译器与代码.md)
  * [何为代码](./何为代码.md)
  * [编程的尿性](./编程的尿性.md)
* 章节一
  * [数据类型与变量](./数据类型与变量.md)
  * [输入输出](./输入输出.md)
  * [函数](./函数.md)
  * [包与可见性](./包与可见性.md)
  * [流程控制-判断](./流程控制-判断.md)
  * 流程控制-循环
* 章节二
  * struct 类型
  * slice 类型
  * Map 类型
* 章节三
  * 方法和类
  * 接口
* 章节四
  * 并发

## 再唠两句

这里写一些杂七杂八的说明。

### 没讲到的内容

局部变量与全局变量及变量作用域、错误处理、指针。