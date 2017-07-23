
---
title: 【ORID总结】1/18
categories: 全栈营
---

## Objective
**完成了哪些事情?**
- 商店网站拆解任务
- 商店网站前期准备（bootstrap、用户系统、simple\_form\_）

## Reflective
**高峰是什么?**
整理了目前所学rails知识，当需要某个知识点时，能够快速地进行全局搜索，效率大大提高了，感觉很爽。

## Interpretive
**git技巧：做坏了怎么办?**

今天补了一下YY老师的《rails db migration》讲解视频，学到了很有用一招。如果当目前分支的代码做烂了，改怎么办呢？

`git checkout -b xxx_test`
`git add .`
`git commit -m "changes I don't want"`
`git chechout -b xxx`

之前竟然一直不会找个招数，所以在敲代码的时候特别害怕犯错，现在会了之后，就可以大胆地试错了。

另外，对于代码，可以用git恢复，但对于数据库的恢复，git是无能为力的，所以要借助`rails db:rollback`或者`rails g migration xxx`来修复数据。

—

**schema.rb是用来干嘛的？**

在讲解视频中，YY老师不说有`schema.rb`，我还真没注意到它。原来它的作用是给开发者看的，能让开发者清楚地查看当前数据库中所有的字段，包括它们的类型等等之类的信息。

但是，如果修改`schema.rb`是没有任何作用的，因为它只是用来看的，不能用来操作数据库。

## Decisional
明天练习商店网站的part1、part2、part3部分。