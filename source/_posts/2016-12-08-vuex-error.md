
---
title: vuex报错：vuex requires a Promise polyfill in this browser
categories: Javascript
tags: vue
---

使用vue2.0脚手架生成的项目，并且继承vuex和vue-router，在谷歌浏览器是正常的，但是在微信和uc浏览器就会出现这个错误。

后来知道了原来需要加一个补丁，因为有些浏览器并不支持promise。

解决方法：

step1：安装babel-polyfill。

    npm i babel-polyfill -S

step2：将babel-polyfill添加到webpack的entry

    entry: {
      app: ['babel-polyfill', './src/main.js']
    }


