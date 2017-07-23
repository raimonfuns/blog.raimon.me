---
title: 【错误】new require构造函数
categories: Javascript
---

## 动作

```javascript
let player = new require('./player')() // player是一个构造函数
```

## 预期结果

`new`一个`Player`实例

## 实际结果

实例的`this`为`undefined`

## 分析

我尝试换了一种写法

```javascript
const Player = require('./player')
let player = new Player()
```

这种是可以的。

我认为是`new`和`require`不能连在一起用，于是尝试用`()`把`require`包起来

## 解决方法

```javascript
let player = new (require('./player'))()
```

It works!