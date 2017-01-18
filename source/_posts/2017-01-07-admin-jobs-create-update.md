---
title: 【错误】不能执行正确的create和update（多级路由）
categories: rails全栈
---

### 位置

《招聘网站》admin的CURD

### 动作

在`views/admin/jobs/new.index.html`和`views/admin/jobs/update.index.html`中触发new和update

### 预期结果

分别执行`admin/jobs#new`和`admin/jobs#update`

### 实际结果

分别执行的是`jobs#new`和`jobs#update`

### 分析

在jobs和admin/jobs的模板是一样的，这样导致admin/jobs最终触发的都是jobs的controller里面的方法，所以要修改admin/jobs中的模板，加以区分。

### 解决方法

![][image-1]
![][image-2]

[image-1]:	http://oggx6lf7f.bkt.clouddn.com/8v9cd.png
[image-2]:	http://oggx6lf7f.bkt.clouddn.com/l3bl7.png
