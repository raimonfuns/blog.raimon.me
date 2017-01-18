---
title: 《React Native开源项目 — Snowflake》学习总结
categories: Javascript
tags: [React]
---

snowflake是一个非常好的[react naitve开源项目][1]，功能其实并不复杂，但是讲解却非常详细，它的功能主要是实现手机app的登录、注册、修改密码以及获取和修改用户信息等功能，是个很常见的业务场景。

通过它可以了解一个完整的React Native项目是长什么样子的，有哪些常用的模块，以及代码是怎么规划的，组件和组件之间是如何通过redux来进行通信交流的。

## 新发现的几个模块

开发React Native有一些几乎是必备的模块，比如`react-redux`，`redux-thunk`，在看这个项目的过程中，发现了几个之前不知道的模块。

### react-native-i18n

[https://github.com/AlexanderZaytsev/react-native-i18n][2]

一开始不明白`i18n`是什么意思，后来google之后才知道，原来是internationalization，国际化的意思，nternationalization去掉头尾的i和n刚好还剩下18个字符。这个模块可以让app自动地切换成当前移动设备使用的语言。

比如在一份json文件中定义不同的语言：

```javascript
{
  "zh": {
    "App": {
      "version": "版本"
    },
    "Header": {
      "current_state": "当前状态",
      "see_console": "查看控制台",
      "update_state": "更新状态"
    }
  },
  "en": {
    "App": {
      "version": "Version"
    },
    "Header": {
      "current_state": "Current State",
      "see_console": "see console",
      "update_state": "Update State"
    }
  },
  "fr": {
    "App": {
      "version": "Version"
    },
    "Header": {
      "current_state": "état actuel",
      "see_console": "voir console",
      "update_state": "état de mise à jour"      
    }    
  },
  "es": {
    "App": {
      "version": "Versión"
    },
    "Header": {
      "current_state": "Estado actual",
      "see_console": "ver la consola",
      "update_state": "Estado de actualización"      
    }  
  }
}
```

引用这份json文件：

```javascript
var I18n = require('react-native-i18n')
import Translations from '../lib/Translations'
I18n.translations = Translations

let version = I18n.t('App.version')
```

变量version的值在中文的手机会显示：“版本”，在英文的手机会显示：“Version”。

### tcomb-form-native

[https://github.com/gcanti/tcomb-form-native][3]

一个非常好用的表单库，根据配置可以快速生成表单，使用的方法如下

```javascript
const t = require('tcomb-form-native')
let Form = t.form.Form

loginForm = t.struct({
  username: t.String,
  email: t.String,
  password: t.String,
  passwordAgain: t.String
})
options.fields['username'] = username
options.fields['username'].placeholder = I18n.t('LoginForm.username')
options.fields['username'].autoCapitalize = 'none'
options.fields['email'] = email
options.fields['email'].placeholder = I18n.t('LoginForm.email')
options.fields['email'].autoCapitalize = 'none'
options.fields['password'] = password
options.fields['password'].placeholder = I18n.t('LoginForm.password')
options.fields['passwordAgain'] = passwordAgain
options.fields['passwordAgain'].placeholder = I18n.t('LoginForm.password_again')
```

最终可以生成相应的表单

![][image-1]

### react-native-router-flux

[https://github.com/aksonov/react-native-router-flux][4]

React Native路由模块，轻松实现不同组件的切换。使用方法：

```javascript
// 引入模块
import {
    Router,
    Scene} from 'react-native-router-flux'

// 配置组件
<Router sceneStyle={{ backgroundColor: 'white' }}>
  <Scene key='root' hideNavBar>
    <Scene key='App'
      component={App}
      type='replace'
      initial />

    <Scene key='InitialLoginForm'
      component={Register}
      type='replace' />

    <Scene key='Login'
      component={Login}
      type='replace' />

    <Scene key='Register'
      component={Register}
      type='replace' />

    <Scene key='ForgotPassword'
      component={ForgotPassword}
      type='replace' />

    <Scene key='Subview'
      component={Subview} />
  </Scene>
</Router>
         
```

key就是组件的标志，比如说，如果要跳转到`Register`组件，可以这么做：

```javascript
import { Actions } from 'react-native-router-flux'
Actions.Register()
```

### react-native-simple-store

[https://github.com/jasonmerino/react-native-simple-store][5]

React Native本地的异步储存，使用方法如下：

```javascript
import store from 'react-native-simple-store';

store
  .save('coffee', {
    isAwesome: true
  })
  .then(() => store.get('coffee'))
  .then(coffee => {
    console.assert(coffee.isAwesome === true);
  })
  .then(() => store.update('coffee', {
    isNotEssential: false
  }))
  .then(() => store.get('coffee'))
  .then(coffee => {
    console.assert(coffee.isNotEssential === false);
    console.assert(coffee.isAwesome === true);
    return store.delete('coffee');
  })
  .then(() => store.get('coffee'))
  .then(coffee => {
    console.assert(coffee === null);
  })
  .catch(error => {
    console.error(error.message);
  });
```

## 代码规划

- 入口文件，index.ios.js和index.android.js
- 所有业务代码放在src目录中
- reducers单独一个文件夹，里面分成4个模块，分别是auth、device、global和profile，每个模块里面有3份文件，分别是installState.js（初始化数据）、actions.js（dispatch行为）和reducer.js（接受diapatch，更改数据），每个模块里面还有一个tests文件夹，用来存放actions和reducer的测试用例。
- containers存放所有路由组件，也就是所有的页面
- lib存放config、数据请求以及工具类文件
- images存放图片
- componengs存放通用的小组件

项目虽然不是很复杂，但是代码的规划非常合理，也有完整的单元测试，确实学到了很多东西。

[1]:	https://github.com/bartonhammond/snowflake
[2]:	https://github.com/AlexanderZaytsev/react-native-i18n
[3]:	https://github.com/gcanti/tcomb-form-native
[4]:	https://github.com/aksonov/react-native-router-flux
[5]:	https://github.com/jasonmerino/react-native-simple-store

[image-1]:	http://oggx6lf7f.bkt.clouddn.com/v2jdt.png