---
title: 函数式编程
categories: Javascript
---

## 什么是函数式编程？

首先说说什么是编程范式，它指的是计算机编程的基本风格或典范模式。打个比喻，如果说每个编程者都在创造一个虚拟世界，那么编程范式就是他们所采用的世界观和方法论。常见的编程范式有两种：面向过程编程（C）和面向对象编程（C++，JAVA）。

函数式编程是一种编程范性，它有如下特点：

- 函数是有确定性输出的（也就是维基百科上面所说的：避免使用程序状态以及易变对象）。
- 使用函数进行编程（恩，貌似是废话^_^）。
- 可以接受函数当作输入和输出（函数可以作为参数，也可以作为返回值）。
- 强调执行的结果而非执行的过程（比如这个函数 getUserInfo 就是针对结果的，我只关注这个函数需要什么参数，以及它会返回什么 ）。
- 倡导利用若干简单的执行单元让计算结果不断渐进，逐层推到复杂的运算，而不是设计一个复杂的执行过程。（循序渐进，不要一口气吃成一个大胖子）。

## 基本要求

- 函数是一等公民（函数可以作为参数，也可以作为返回值，也可以把函数赋给变量）。
- 函数没有副作用、不修改状态。
- 参数、对象不可变。
- 只用表达式，不用语句。
- 不鼓励使用this

## 种类

### 普通函数

```javascript
y = f(x)
```

![](http://ww1.sinaimg.cn/large/801b780ajw1f84lcsj027j20cl02bjrc.jpg)

将一个输入（x）隐射到一个输出（y）上。

### 隐射函数（map）

```javascript
y = map(f, x)
```

![](http://ww2.sinaimg.cn/large/801b780ajw1f84lffn529j20ch07n74t.jpg)

将一组输入映射到一组输出上。

如果用面向过程编程来写的话就要分别执行3次f函数：

```javascript
x1 = f(y1)
x2 = f(y2)
x3 = f(y3)
```

### 组合函数（compose）

```javascript
z = h(g(x))
```

设：z = f(x)，则

```javascript
f = compose(h, g)
```

h就好比是工厂里面的一条生产流水线，而g和h是流水线上的两道工序。

![](http://ww3.sinaimg.cn/large/801b780ajw1f84lo0y7q7j20ke028q30.jpg)

组合函数实例：

```javascript
function compose() {
  var fns = arguments
  return function (result) {
    for (var i = fns.length - 1; i >= 0; i--) {
      result = fns[i](result)
    }
    return result
  }
}

function a(x) {
  return x + 'a'
}

function b(x) {
  return x + 'b'
}

const add_ab = compose(b, a)
const str = add_ab('')
console.log(str) // 'ab'
```

### 隐射 + 组合

```javascript
z = map(compose(h, g), x)
```

![](http://ww4.sinaimg.cn/large/801b780ajw1f84lpe8qnrj20l70940tr.jpg)

### 柯里化（currify）

柯里化的函数：可以固定一部分参数的函数。

```javascript
z = h(c, y)
```

当c为定值时 z = f(y)

```javascript
h = currify(h) // 柯里话之后的函数h，接受一个固定参数c，并返回一个新的函数
f = h(c)
```

![](http://ww2.sinaimg.cn/large/801b780ajw1f84lrce3jtj20sh0bf0th.jpg)

currify函数实例：

```javascript
function curry(f) {
  return function (...a) {
    if (a.length < f.length) {
      return function (...b) {
        return f(...a, ...b)
      }
    } else {
      return f(...a)
    }
  }
}

const foo = curry(function (a, b, c, d) {
  return a*b + c*d
})

console.log(foo(1, 2, 3, 4)) // 14
const bar = foo(1, 2)
console.log(bar(3, 4)) // 14
```

### 隐射 + 组合 + 柯里化

```javascript
z = map(compose(furrify(h)(c), g), x)
```

![](http://ww3.sinaimg.cn/large/801b780ajw1f84m3nyl17j20l90cg3zt.jpg)

### filter

```javascript
z = map(compose(h(c), g), filter(x))
```

通过filter函数过滤掉特定的输入。

![](http://ww1.sinaimg.cn/large/801b780ajw1f84m6rchlqj20se0cigmx.jpg)

### 总结

```javascript
y = f(x)
```

f函数就是各种其他函数的组合和变形

![](http://ww1.sinaimg.cn/large/801b780ajw1f84m9zypkdj20la08q0tb.jpg)

## 高阶函数

接受一个或多个函数作为参数，返回一个新的函数。

## 什么是纯函数？

纯函数指的是确定输入能得到确定输出的函数，举个例子

```javascript
var minimum = 21

// 非纯函数，输出受到外部变量（minimum）的影响，同一个输入可能得到不同的输出
function checkAge(age) {
  return age >= minimum
}

minimum = 50

// 纯函数，确定输入得到确定输出
function checkAge(minimum, age) {
  return age >= minimum
}
```

纯函数有什么好处呢？

- 确定性/可缓存性
- 自文档化
- 可测试性
- 可序列化远程执行
- 无锁/并行

## 什么是副作用

副作用就是做了与处理输入输出之外的一些事情，常见的有以下场景：

- 更改文件系统
- 访问系统状态
- 往数据库插入记录
- 发送一个http请求
- 可变数据
- 打印/log
- 获取用户输入
- DOM查询

当然，上面这些操作是必不可少的，我们要做的就是将副作用的影响降到最低，或者是明确地在某一些地方使用这个操作。

PS：npm 有个库叫作[Immutable](https://github.com/facebook/immutable-js)，可以创建一个不可更改的数据，已减少副作用。

## 一个很重要原则

**尽可能**将纯函数（图中的f，g，也就是有确定性输入和输出的函数）集中在一起，不要和有副作用（不确定性）的函数混合在一起。

![](http://ww3.sinaimg.cn/large/801b780ajw1f84mdl00pfj20x208tt9y.jpg)

## 与面向过程式编程的比较

- for loop 对应 map，forEach。
- if else 对应 filter。
- 各种运算符，对应各种函数。
- 变量对应参数和返回值，理论上没有变量。