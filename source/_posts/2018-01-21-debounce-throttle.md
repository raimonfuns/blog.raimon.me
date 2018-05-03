---
title: Debounce 和 Throttle 的区别
categories: Javascript
---

这两个函数的目的都是让我们能够根据时间控制一个函数的执行次数。

debounce能让一堆突然间爆发的事件合并成一个事件。最形象的例子是电梯。当你在1楼，然后你摁了10楼，在电梯准备关门的时候，电梯外突然有人摁了电梯按钮，电梯重新打开门，开始等待，然后在电梯准备关门的时候，又有一个人摁了电梯按钮，电梯又打开门，开始等待，直到在电梯关门的这段时间内，没有人再摁按钮了，电梯才关门，然后开始动起来。在这个例子中，一堆事件指的是「摁按钮」这个动作，而一个事件指的是电梯关上门，开始动起来的这个事件。

和debounce不同的是，throttle是保证每隔固定的一段时间，执行一次函数。最形象的例子是支持无限滚动的页面。每隔一段时间，要检查当前滚动的位置距离底部还有多远，一旦到达某一个临界值，就拉新的数据。

参考链接：[https://css-tricks.com/debouncing-throttling-explained-examples/](https://css-tricks.com/debouncing-throttling-explained-examples/)