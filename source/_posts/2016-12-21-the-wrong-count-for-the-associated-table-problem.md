---
title: 【错误】关联表的计数问题
categories: rails全栈

---

## 位置

《rails 初级练习》3-13 加分题 & 下一步

## 动作

当投票数为0时，让检票按钮失效，处于不能点击的状态

## 预期结果

![](http://oggx6lf7f.bkt.clouddn.com/0lj8k.jpg)

## 实际结果

![](http://oggx6lf7f.bkt.clouddn.com/xq6yg.jpg)

## 分析

我将`-1`按钮封装成helper，代码如下：

![](http://oggx6lf7f.bkt.clouddn.com/5s8kk.jpg)

当投票数为0时，让按钮变成disabled状态。但是结果却不是预期的那样子，说明这个的`topic.count`不是0，于是我就把它显示出来看一下究竟，在view写如下代码

```ruby
<td><%= topic.votes.count %> -- <%= topic.count %></td>
```

得到：

![](http://oggx6lf7f.bkt.clouddn.com/bo9j2.jpg)

哦！当点击`-1`时，原来`topic.votes.count`是会减少的，而topic.count没有减少，这样一来，错误可能出在`downvote`这个action中，果然

![](http://oggx6lf7f.bkt.clouddn.com/rdgvi.jpg)

原来是在执行`-1`时，没有更新count的值。

## 解决方法

![](http://oggx6lf7f.bkt.clouddn.com/4ybed.jpg)

而且，更为合理的是，在view中使用`topic.count`而不是`topic.votes.count`，虽然这两个的值是一样的，但因为在helper中使用到`topic.count`，所以在view中也使用它就能防止本次遇到的错误。view的代码如下

```ruby
<td><%= pluralize(topic.count, "voute") %></td>
```

## 参考链接

[RailsBridge：初探rails加分題](http://lesley.logdown.com/posts/736430-rails-beginners-the-practice-of-lu-series-railsbridge)