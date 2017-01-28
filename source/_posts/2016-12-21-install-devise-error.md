---
title: 【错误】安装devise出错
categories: Ruby on Rails全栈训练营

---

## 动作

《rails 101》5-2节，本来是要运行

```bash
rails g devise:install
```

但是手误，写成了

```bash
rails g divise:install
```

但没有发现，接着执行

```bash
rails g devise user
```

执行完之后，才发现`devise`敲成了`divise`，所以想着重新执行

```bash
rails g devise:install
```

## 结果

![](http://oggx6lf7f.bkt.clouddn.com/hc004.jpg)

## 解决方法

一开始就想着，既然安装不了devise了，那就卸载devise咯，于是就上网查了很多删除devise的资料，越找越复杂，心里就在想：“为什么一个简单的问题，搞得那么复杂呢？”，就在这时候，我想到的解决方法！

git是什么？时光机呀！如果你在某一个分支搞砸了，那就回到之前的分支，重新来过就行了。

于是，我先回到上一个分支

```bash
git checkout ch03
```

这时，服务已经能够正常运行了，时光机果然名不虚传，哈哈。

然后，我删除当前这个有着脏代码的分支

```bash
git branch -D ch04
```

最后，再次新建`ch04`分支，按照教程重新操作一遍，done！

这个经历这让我想起了一个比喻 ：

> 一道锁着的门，钥匙可能不在锁上面，而是在其他地方。

