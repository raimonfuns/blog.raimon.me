---
title: 【错误】项目上传到heroku之后，访问报错
categories: rails
tags: 错误
---

## 动作

《rails 初级练习》3-14，上传项目到heroku，运行

```bash
$ heroku create
$ git push heroku master
$ heroku run rake db:migrate
```

然后访问[项目页面](https://protected-coast-71491.herokuapp.com/)

## 结果

![](http://oggx6lf7f.bkt.clouddn.com/f46bz.jpg)

原因：运行`git status`查看git工作区的状态，发现有文件没有提交

![](http://oggx6lf7f.bkt.clouddn.com/bjkoi.jpg)

## 解决方法

提交文件到heroku，done！

