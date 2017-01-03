---
title: Node学习笔记：Global对象
categories: node
tags: [node]
---

## REPL环境

> 在Node.js中，为了使开发者方便测试JS代码，提供了一个叫做*REPL*（Read-Eval-Print-Loop）的可交互式运行环境。在该环境中，开发者可以输入任何JS代码，按下回车后，REPL环境中将显示表达式的运行结果。

## 全局对象与全局变量

### 全局对象

- Global：Node的全局对象，类似于浏览器的window。
- process：Node所处的当前进程。
- console：Node内置的console模块。

### 全局函数

- setTimeout
- clearTimeout
- setInterval
- clearInterval
- require：用于加载模块。
- Buffer：用于操作二进制数据。

### 全局变量

- __filename：当前运行的脚本文件名。
- __dirname：当前脚本所在的目录。

注意：这两个变量不能直接在REPL中访问，只能在js文件中访问。

### module.exports和exports

不同的模块之间怎么共享代码呢？使用Global？不可以，这样会污染全局变量，所以应该使用的是CommonJS规范的模块化功能。

模块通过module.exports对外提供代码，一般情况下module.exports和exports引用的是同一个对象，但不改变它们的引用时，不会有任何问题。当引用被改变了，CommonJS导出的永远是module.exports指向的对象。
