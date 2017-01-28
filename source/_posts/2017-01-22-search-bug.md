
---
title: 【错误】搜索空内容会报错
categories: Ruby on Rails全栈训练营
---

## 报错信息

## ![][image-1]

## 分析

结果显示@jobs为空，所以报错。查看了一下controller

![][image-2]

也就是，只在有传参数的情况下才会设置@jobs的值，否则就是空，所以导致报错。



## 解决办法

![][image-3]

如果没有传参数，那就设置@jobs的值为正常的按时间排序的结果。


[image-1]:	http://oggx6lf7f.bkt.clouddn.com/rn2n2.png
[image-2]:	http://oggx6lf7f.bkt.clouddn.com/0mag2.png
[image-3]:	http://oggx6lf7f.bkt.clouddn.com/mjhc9.png