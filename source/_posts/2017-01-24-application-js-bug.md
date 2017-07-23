
---
title: 【错误】切换页面，jquery的绑定事件会失效
categories: 全栈营
---

## 动作

![][image-1]

在application.js，用jquery的ready绑定方法，第一次打开首页是正常的，如果跳到其他的页面，然后回到首页就会失效。

![][image-2]

## 分析

结果调试发现，在页面跳转时，application.js是不会再次执行，除非刷新页面，所以相当于事件没有绑上去。

## 解决方法

改成监听事件的模式，监听document上面的事件，done

![][image-3]

[image-1]:	http://oggx6lf7f.bkt.clouddn.com/557od.gif
[image-2]:	http://oggx6lf7f.bkt.clouddn.com/51dq2.png
[image-3]:	http://oggx6lf7f.bkt.clouddn.com/90kjt.png