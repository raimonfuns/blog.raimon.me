# collection 和 member 的区别

我们先定义一下`member`和`collection`：

- `member`：请求一个特定的资源，是单数，路径后面不带`s`
- `collection`：获取一个集合，或者说列表，是复数，路径后面带`s`

拿这段路由配置为例：

```ruby
resources :groups do
  member do
    post :join
    post :quit
  end

  collection do
    post :hot
  end
end
```

我们运行`rails routes`看一下

![](https://ww3.sinaimg.cn/large/006tKfTcly1fckce3231jj31560asjuf.jpg)

从图中可以看出来，`hot_groups`和`group_posts`是`collection`类型，而其他的是`member`类型。