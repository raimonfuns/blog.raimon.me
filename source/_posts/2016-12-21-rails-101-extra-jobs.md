---
title: rails 101 额外作业
categories: rails
---

![](http://oggx6lf7f.bkt.clouddn.com/3xg77.jpg)



一开始认为，既然是删除我的文章，那肯定是写在`account/posts`里面咯，于是就写了`account/posts#edit`这个action。然后打开刷新页面，却出现这个结果

![](http://oggx6lf7f.bkt.clouddn.com/iofxy.png)

百思不得其解...

后来，发现点击编辑文章是，跳转的路径是`edit_group_post_path(post.group, post)`，焕然大悟

![](http://oggx6lf7f.bkt.clouddn.com/m35el.jpg)

于是就把`edit`这个action从`controllers/account/posts.controller.rb`搬到`controllers/posts.controller.rb`，再把`edit.html.erb`从`views/account/posts`搬到`views/posts`，然后刷新页面，done！

同样的，接着写`posts#destroy`，可以删除文章了，done！

另外一点，我发现教程上的路径函数中传入了当前文章对应的group

![](http://oggx6lf7f.bkt.clouddn.com/bscpf.jpg)

一开始真不知道是要用来干嘛的，所以在写controller时，一直想着怎么用这个group，想不明白，后来才想到，原来是用跳转页面时要用到的。

![](http://oggx6lf7f.bkt.clouddn.com/qn5r7.jpg)


