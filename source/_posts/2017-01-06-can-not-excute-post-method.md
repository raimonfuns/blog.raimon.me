---
title: 【错误】无法执行post方法
categories: 全栈营
---

### 动作

html代码

![][image-1]

点击`hide`按钮

![][image-2]

### 结果

![][image-3]

### 分析

从图中可以看出页面发出的是`get`请求

而我定义的方法是post

![][image-4]

### 解决方法

把方法定义为`post`

![][image-5]

done！

[image-1]:	http://oggx6lf7f.bkt.clouddn.com/lxhv1.png
[image-2]:	http://oggx6lf7f.bkt.clouddn.com/czrzb.png
[image-3]:	http://oggx6lf7f.bkt.clouddn.com/d5jjq.png
[image-4]:	http://oggx6lf7f.bkt.clouddn.com/3cav2.png
[image-5]:	http://oggx6lf7f.bkt.clouddn.com/n73pl.png
