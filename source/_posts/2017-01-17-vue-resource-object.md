---
title: 【错误】vue-resource发送参数格式错误
categories: Javascript
---

## 动作
用`vue-resource`发送post请求，参数是一个多维对象

## 预期结果
![][image-1]

## 结果
最深层的对象的属性`prop`会被转化成`[prop]`

![][image-2]

## 解决方法
在发送数据之前，把对象转化成字符串

![][image-3]



[image-1]:	http://oggx6lf7f.bkt.clouddn.com/s6vfn.png
[image-2]:	http://oggx6lf7f.bkt.clouddn.com/t5t5w.png
[image-3]:	http://oggx6lf7f.bkt.clouddn.com/ljfqr.png