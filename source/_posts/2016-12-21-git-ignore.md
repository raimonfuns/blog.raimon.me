---
title: 【用法】为什么在.gitignore设置忽略文件夹无效？
categories: 工具
tags: [Git]
---

当我不想把某个文件夹提交到git时，可以在`.gitignore`文件中写入要忽略的文件夹。当时我的操作是这样子的，先把所有的文件夹都提交上去，然后才意识到有一个文件夹不应该提交，所以我就在`.gitignore`中写（我要忽略的文件夹是buildfiles）

```
buildfiles/
```

![](http://oggx6lf7f.bkt.clouddn.com/n2v9e.jpg)

然后当我修改buildfiles里面的文件夹时，用`git status`查看git状态，发现里面竟然还有buildfiles的内容！！！我不是忽略它了吗，怎么还有？

![](http://oggx6lf7f.bkt.clouddn.com/820n4.jpg)

后来才知道，**已经提交到git的文件，就会一直存在着，无法没忽略，除非你把它从git上面删除**。于是，我把本地`buildfiles`里面所有的文件都删除，重新提交一遍，之后在添加文件就会自动被git忽略掉了，done！
