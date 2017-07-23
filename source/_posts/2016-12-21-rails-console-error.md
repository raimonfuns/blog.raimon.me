---
title: 【错误】在rails console中操作数据库报错
categories: 全栈营

---

## 动作

《rails初级练习》3-8节，进入rails console，运行`Topic.count`。

## 结果

![2016-11-26 13-25-19](http://oggx6lf7f.bkt.clouddn.com/69foq.jpg)

## 解决方法
运行 `bundle update`，如果问题没有解决，执行`spring stop`应该就ok。

## 参考链接
[Segmentation fault with Rails after upgrading to OS Sierra, possibly related to sqlite3 gem](http://stackoverflow.com/questions/39812707/segmentation-fault-with-rails-after-upgrading-to-os-sierra-possibly-related-to)
