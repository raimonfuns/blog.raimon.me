---
title: 【ORID总结】1/7
categories: 全栈营
---

## Objective

- 《招聘网站》第五部分，对照着解答优化自己的代码

## Reflective

- 发现的bug，脑中的想法是：“又能学到一点原先不知道的知识，挺好”。
- 遇到不懂的东西，在论坛上面找到了答案，很开心。
- 当发现自己的代码，对比别人的代码，从中学习，也挺开心。

今天的低点：花比较少的时间在学习上，浪了一天。

## Interpretive

### 不能执行正确的create和update（多级路由）

文章：http://raimonfuns-blog.logdown.com/posts/1285306

### bootstrap中的row布局

文章：http://raimonfuns-blog.logdown.com/posts/1285436

### ! 和 ?

我发现一个规律，当写在model里面的方法

- 如果是要进行某个操作，则用`!`表示肯定的语气，比如说：`join!`,`quit!`, `publish!`,`hide!`；
- 如果是用来判断状态，则用`？`表示疑问的语气，比如说：`is_member_of?`,`admin?`

### 没有提供入口并不代表访问不到

在《招聘网站》中，如果在后台把文章的状态设置为`false`，那么文章就不会再首页上显示，但用户还是可以从地址栏上面直接输入job地址，进而访问job页面，所以呢，要在job#show里面加一个条件判断

![][image-1]

之所以要总结一下这个知识点，不是因为它很难，而是因为它`太容易被忘记了`，因为一般情况下都会想当然的认为，文章隐藏了就是隐藏了，所以就会认为别人无法访问到了，但其实不是，这是个很容易犯的错误，切记切记。

### self 

今天看到了这个代码：

`contoller`

![][image-2]

`model`

![][image-3]

原来[self指的就是到物件本身][1]（@job），又学到了一招！

### redirect\_to :back

![][image-4]

`redirect_to :back`的作用是重定向到本页面，也就是相当于刷新页面，这样一来就不用写当前页面的路由，简洁易懂。

## Decisional

对照着《招聘网站》的解答版，优化自己写的代码，多做总结。

[1]:	https://rocodev.gitbooks.io/rails-102/content/chapter3-ruby/self.html

[image-1]:	http://oggx6lf7f.bkt.clouddn.com/qbdpb.png
[image-2]:	http://oggx6lf7f.bkt.clouddn.com/fn8pn.png
[image-3]:	http://oggx6lf7f.bkt.clouddn.com/ejfqd.png
[image-4]:	http://oggx6lf7f.bkt.clouddn.com/3lici.png
