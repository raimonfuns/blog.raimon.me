---
title: 【全栈日记】2016/12/10
categories: rails全栈
---

## Objective

重新做一遍基础练习，并完成加分题。

（倒叙题尝试了很多种方法，最后还是没有做出来 XD）

## Relective

### 高峰是什么？

虽然今天练了一天车，很累，但还是坚持完成了昨天定下的计划。

## Interpretive

### 新建'about'页面

一开始路由是怎么写的

![](http://oggx6lf7f.bkt.clouddn.com/mwdwh.jpg)

但却得到这种结果

![](http://oggx6lf7f.bkt.clouddn.com/f5evc.jpg)

后来看到文档里面原来是怎么写的

![](http://oggx6lf7f.bkt.clouddn.com/sqxax.jpg)

于是就改一下写法

![](http://oggx6lf7f.bkt.clouddn.com/idf0m.jpg)

ok

![](http://oggx6lf7f.bkt.clouddn.com/bpry1.jpg)

### 加一个'扣分'按钮

```ruby
def downvote
  @topic = Topic.find(params[:id])
  @topic.votes.first.destroy
  redirect_to(topics_path)
end
```

## Decisional

明天完成基础练习的加分题，然后再练习一遍rails 101