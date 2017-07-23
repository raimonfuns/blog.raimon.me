---
title: 【错误】for-in 和 for-of
categories: Javascript
---

## 动作

```javascript
let str = 'abcde'
for (let char in str) {
  console.log(char)
}
```

## 预期结果

a b c d e

## 实际结果

1 2 3 4 5

## 分析

用`for-of`试一下

```javascript
let str = 'abcde'
for (let char of str) {
  console.log(char) // a b c d e
}
```

这才是我想要的结果。

说明：`for-in`是遍历index，`for-of`是遍历value

## 解决方法

使用`for-of`