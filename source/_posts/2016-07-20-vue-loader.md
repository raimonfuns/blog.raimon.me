---
title: 使用vue-loader进行组件化开发
categories: Javascript
tags: [Vue, 组件化]
---

一般我们是按照文件类型来组织目录，也就是将html、css、js文件放在各自的文件夹中，然后根据路径在页面中引用对应的资源。这样做的弊端有

> 1. 多人协作，容易造成冲突
> 2. 不清楚哪里引用了这个文件，导致不敢随意移动和修改
> 3. 寻找对应资源繁琐，需要逐个打开目录

## 组件化开发是怎样的？
将html，css，js整合到一份文件里面，成为一个独立的组件。页面就相当于一个容器，装填许多的组件。组件化开发的基本理念是这样的（图引[张云龙][1]）

![components1][image-1]

一个项目的开发可以这样组织（图引[张云龙][2]）

![components2][image-2]

[vue-loader][3]就是来做这件事的，它是webpack的一个插件，可以实现组件化开发。我们只需要新建一个.vue文件，然后把html，css，js放到文件中，vue就会帮我们搞定一切。vue的组件文件的后缀名是.vue，它里面的写法是这样的：

![][image-3]

最后，我们的任务就是开发一个个组件，然后将之放到页面中，并解决组件之间的通信。

## vue-router
[vue-router][4]是vue官方做的路由插件，可以根据路由显示不同的组件，也就是可以用来做SPA（单页应用），它的写法是这样的

``` js
router.map({
  '/news/:page': {
    component: NewsView
  },
  '/user/:id': {
    component: UserView
  },
  '/item/:id': {
    component: ItemView
  }
})
```

然后在页面中添加入口

``` js
<router-view></router-view>
```

可以添加一些transition动画，做比较酷炫的切换。

``` js
<router-view
  transition
  transition-mode="out-in">
</router-view>
```

可以在route方法中取得路由的参数

``` js
route: {
  data ({ to }) {
    const page = to.params.page
  }
},
```

## 组件的规划
组件可以分为两层，分别是views和components。views组件用来做路由的入口，相当于一个页面，而components则是颗粒化比较小的组件，放在views组件里面。

## 组件之间的通信
当页面逻辑比较简单时，只需要使用Props属性进行传参即可。对于中型规模以上，数据逻辑比较复杂的应用，可以考虑引入[Vuex][5]集中管理状态。

## 例子
> 1. [vue-loader-example][6]
> 2. [vue-hackernews][7]
> 3. [vue-mobile][8]
> 4. [vue-zhihu-daily][9]


## 参考资料
> 1. [前端工程——基础篇][10]
> 2. [告别刀耕火种:浅谈VisMooc的前端工程化][11]

[1]:	https://www.zhihu.com/people/fouber
[2]:	https://www.zhihu.com/people/fouber
[3]:	https://github.com/vuejs/vue-loader
[4]:	http://router.vuejs.org/zh-cn/
[5]:	https://github.com/vuejs/vuex
[6]:	https://github.com/vuejs/vue-loader-example
[7]:	https://github.com/vuejs/vue-hackernews
[8]:	https://github.com/lihongxun945/vue-mobile
[9]:	https://github.com/hilongjw/vue-zhihu-daily
[10]:	https://github.com/fouber/blog/issues/10
[11]:	http://chenzhutian.org/blog/2016/%E6%B5%85%E8%B0%88VisMooc%E7%9A%84%E5%89%8D%E7%AB%AF%E5%B7%A5%E7%A8%8B%E5%8C%96/

[image-1]:	http://file.do.yy.com/group3/M04/CD/91/tz0MYFePEVCAErg8AADQj2Vx_yE826.png
[image-2]:	http://file.do.yy.com/group3/M04/CD/94/tz0GSFePEVCAQrBvAABOxVF9wgs511.png
[image-3]:	http://file.do.yy.com/group3/M04/CD/91/tz0MYFePEV2AeND1AAHbqgkHl5w930.png