---
title: 【ORID总结】1/10
categories: 全栈营
---

## Objective
完成招聘网站的观看系统和应征系统
## Reflective
今天精神特别集中，一口气把功能都做完了，情绪不错。

## Interpretive
### case和when
今天学到一个新的语法，case和when，是用来控制流程的，类似于js中的switch。
### 文件上传
本来一开始打算根据提示，自己独立完成，但是到了上传pdf这个步骤就懵了，因为之前没做过，当我准备建立resume的model时，最让我感到困惑的一点是pdf这个属性的类型是什么？想不明白，后面就直接看答案，哦，原来这个数据类型的string。于是就跟着解答版，把后面的功能都实现了，学到了一个叫做carrierwave上传的gem，挺好用的。
### 《招聘网站》与《rails 101》
xdite老师昨天晚上说可以对比《招聘网站》与《rails 101》有哪些是相同的，有哪些不同。相同点有很多，比如
- groups 对应 jobs
- posts 对应 resumes

最大的不同是《招聘网站》多了一个角色：admin，而admin#jobs的controller是这样建的：

`rails g controller admin::jobs`

admin#resumes的controller是这样建的：

`rails g controller admin::resumes`

总的来说，和《rails 101》相比，多了一个角色，复杂度就高了一些。
## Decisional
- 整理每个功能，做一份cheatsheet，方便将来快速查询。
- 功能都完了，开始给《招聘网站》上漆。
