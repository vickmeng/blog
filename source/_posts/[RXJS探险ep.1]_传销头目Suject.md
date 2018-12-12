---
title: '[RXJS探险ep.1]_传销头目Suject'
photos:
  - ./img/cx.png
date: 2018-12-12 15:26:51
tag: 凭什么不让用？
---
老孟对Subject的理解有误，而且这个错误是共性的，此篇记录探险过程。
## 开局一张图
![](/img/subject.png)

[上图出处中](https://github.com/RxJS-CN/rxjs-articles-translation/blob/master/articles/Subjects-For-Human-Beings.md)如此描述Subject：

> Subject is both an Observable and Observer 

依老孟看Subject跟搞传销的差不多：***既接收上游发的货（数据），又把货发给一众下游。***

那我为什么还要辛苦new Observable对象？全用Subject不就成了？就像下面这样多舒服：


```javascript
const subject = new Subject();
button.addEventListener('click', () => subject.next('click'));
subject.subscribe(x => console.log(x));
```
## 开搞

  ......

  ......

好吧...老孟选择直接 “大哥一下” ，联系到了[Rxjs中文社区的发起者](https://www.zhihu.com/people/sangka/posts)：
![](/img/wx.png)

大哥永远会把你的问题变成更多问题:

1. 为啥少用Subject？
2. asObservable是个啥？

## 问题一
开篇文章结尾处对Suject的使用场景有明确的介绍：
>## When to use Subject
>You need to share the same observable execution.
>When you need to decide what to do when an observer arrives late, do we use ReplaySubject, BehaviorSubject?
>You need full control over the next(), error() and complete() methods.

Subject是为多播而存在的，我的用法的确不对，但这并没有解决我的问题，在[中文社区](https://github.com/RxJS-CN),找到了另一篇文章:[[译]关于 RxJS 中的 Subject](https://github.com/RxJS-CN/rxjs-articles-translation/blob/master/articles/On-The-Subject-Of-Subjects.md)。

文章开头就提到了我的问题，感谢译者......哦，还是大哥.....
>.......很有帮助，但这不是以 “Rx 的方式”在处理问题。理想的是在 Observable 中包装事件注册，既可以监听事件，又可以取消事件监听。看起来像这样:

```javascript
  const clicks = new Observable(observer => {
    const handler = (e) => observer.next(e);
    button.addEventListener('click', handler);
    return () => button.removeEventListener('click', handler);
  });
```
风格原因？这不足以让老孟抛弃Subject,主要所有逻辑是全挤在new Observable的参数里太难写了。我需要更充分的理由~~

[大哥一下：](https://www.zhihu.com/people/sangka/posts)
![](/img/wx2.png)

直觉告诉老孟，Subject带来的麻烦可能和***不可重用***这个特征有关系，unsubscribe之类的balabalabala......老孟现在不想深究，以后有机会再研究。

so that，我们的第一个问题变成了***如何用O代替S***（ps： 虽然egghead搞圣诞节打折，但年费也要十张毛爷爷，md这年头没钱想搬砖都搬不起）




