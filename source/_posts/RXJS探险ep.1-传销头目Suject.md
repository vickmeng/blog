---
title: '[RXJS探险ep.1]传销头目Suject'
photos:
  - ./img/cx.png
date: 2018-12-12 15:26:51
excerpt: 老孟的理解有问题~~
---
老孟对Subject的理解有误，而且这个错误是共性的，此篇记录探险过程。
## 开局一张图
![](/img/subject.png)

[上图原文](https://github.com/RxJS-CN/rxjs-articles-translation/blob/master/articles/Subjects-For-Human-Beings.md)如此描述Subject：

> Subject is both an Observable and Observer 

***(值得注意，在大多数关于观察者模式的资料里，Subject代表产生事件的主体。Rx的Subject不太一样。)***

依老孟看Subject跟搞传销的差不多：**既接收上游发的货（数据），又把货发给下游。**

那我为什么还要辛苦new Observable对象？全用Subject不就成了？值得调查~~

## 开搞

  ......

  ......

好吧...老孟决定直接[大哥一下](https://www.zhihu.com/people/sangka/posts)。
![](/img/wx.png)

Z搜永远能把你的问题变成更多问题:

1. 为啥少用Subject？
2. asObservable是个啥？

## 问题一
开篇的文章结尾处对Suject的使用场景有明确的介绍：
>## When to use Subject
>You need to share the same observable execution.
>When you need to decide what to do when an observer arrives late, do we use ReplaySubject, BehaviorSubject?
>You need full control over the next(), error() and complete() methods.

Subject是仅为多播而存在的，我的用法属实不对，但这并没有解决我的问题，我在[RxJS 中文社区](https://github.com/RxJS-CN),找到了另一篇文章:[[译]关于 RxJS 中的 Subject](https://github.com/RxJS-CN/rxjs-articles-translation/blob/master/articles/On-The-Subject-Of-Subjects.md)。

文章开头就提到了我的问题，感谢译者......哦，还是大哥.....


