---
title: Nginx学习笔记
categories: 工具
tags: Nginx
---

安装

```
brew install nginx
```

## 入门文档

[文档](http://nginx.org/en/docs/beginners_guide.html)

## Nginx是做什么的？基本流程是怎样的？

首先，有一个很重要的概念，就是**主从模式**，指的是由一个主进程（master）控制几个子进程（worker），用图片表示如下

主进程可以控制子程序的创建与退出（销毁），当一个主进程接收到一个url请求时，会读取nigix的配置（.conf结尾，比如niginx），然后会根据配置，会将url发放到对应的子进程，所以，主进程并不直接处理请求，只是起到一个控制的作用，最终还是子进程来处理，而nginx存在于主、子进程的中间，起到一个中间层的作用。

## 基本命令

### 启动

```
nginx
```

### 控制

```
nginx -s signal
```

signal可以是

- stop — 强制退出进程
- quit — 等进程处理完手上的事情之后退出
- reload — 重启
- reopen — 重新打开log日志文件

## 实例

### 启动nginx

安装好nginx之后，启动nginx，打开localhost:8080（默认），就可以看到nignx默认的欢迎界面，然后就可以打开nignx的配置文件

```
/usr/local/etc/nginx/nginx.conf
```

然后就可以修改配置，重启，看看效果，先配置一个最简单的

```
http {
  server {
	listen 8080;
    location / {
      root /Users/raimonfuns/www
    }
    location /images/ {
      root /Users/raimonfuns/www
    }
  }
}
```

当访问localhost:8080时，服务器返回/Users/raimonfuns/www/index.html

当访问localhost:8080/images/a.png时，服务器返回/Users/raimonfuns/www/images/a.png

nginx也经常用来做代理，也就是

> 根据不同的路由，访问不同的服务

```
http {
  server {
    listen 8080;
    location / {
      proxy_pass http://localhost:8080;
    }
    location /pages/ {
      root /users/raimonfuns/Public/www/;
    }
  }
}
```

当访问localhost:8080时，服务器返回http://localhost:8080/index.html（这就是代理）

当访问localhost:8080/images/a.png时，服务器返回/Users/raimonfuns/www/images/a.png（没有代理，访问原来的服务）

## 负载均衡

负载均衡通俗一点来讲就是平均工作量。就好比餐厅里面有很多厨师，当有一桌菜需要做时，服务员就会根据厨师们手上的事情来分配工作量，尽量平衡每个厨师的工作量，以免出现某个厨师累垮了，而另外一个厨师没事干。

当主进程接受到一个请求时，nginx会根据子进程的繁忙程度来指定由哪个进程处理这个请求，平衡每个进程的工作量，从而提高稳定性，这就是负载均衡。
