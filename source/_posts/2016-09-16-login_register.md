---
title: post数据处理
categories: Node
---

## req.body

nodejs的req没有定义body，所以为undefined

## 表单提交post请求

两个重要的属性

> Content-Type: application/x-www-form-urlencoded
>
> Form Data: name=raimonfuns&password=1234 （这是stream）

## 接收数据流

- stream.on('data')
  - 将data添加到buffers
- stream.on('end')
  - buffer = Buffer.concat(buffers)
  - buffer.toString('utf8')

## querystring模块

```javascript
> qs.parse('name=raimonfuns&password=1234')
{ name: 'raimonfuns', password: '1234' }
```
