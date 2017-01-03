---
title: supertest测试框架
categories: node
tags: [测试]
---

用来测试nodejs http服务的框架，断言的语法基于superagent框架（在客户端和nodejs都能使用的http请求框架，语法优雅）

## API

> ### .expect(status[, fn])
>
> Assert response status code.
>
> ### .expect(status, body[, fn])
>
> Assert response status code and body.
>
> ### .expect(body[, fn])
>
> Assert response body text with a string, regular expression, or parsed body object.
>
> ### .expect(field, value[, fn])
>
> Assert header field value with a string or regular expression.
>
> ### .expect(function(res) {})
>
> Pass a custom assertion function. It'll be given the response object to check. If the check fails, throw an error.
>
> ### .end(fn)
>
> Perform the request and invoke fn(err, res).

## 实例

```javascript
describe('GET', function(){
  it('should work', function(done){
    request
      .get('/')
	  .expect('Content-Type', /json/)
      .expect(200)
      .expect({ name: 'TJ' }, done);
  })
})
```

