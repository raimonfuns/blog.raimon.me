---
title: vue从1.0升级到2.0
categories: Javascript

---

原先有一个项目，想要使用[饿了么的UI库][1]来提高项目的简洁度以及可扩展性，也提高开发效率，所以决定将项目的基础库vuejs，从1.0升级为2.0。

vue2.0移除和替换了很多api，所以在升级的过程中，修改了无数个bug，最终费了很大的劲才升级成功，同时也集成了UI库，界面变简洁美观了，开发变得更加容易了，所以升级还是非常值得的。

在这个过程中，记录了很多的东西，在此总结一下。

## 检测需要升级的代码工具

[vue-migration-helper][2]能用来检测定位需要升级的代码，可以快速定位，批量修改代码，很实用。

## vuex的dispatch

1.0是通过actions的dispatch来派发mutation。

2.0改成用dispatch派发action，然后action通过commit派发mutation，然后对数据进行修改。

## router

1.0在组件中监听路由变化的写法

```javascript
new Vue({
  route ({to}) {
    //to是路由实例，可以拿到路由的各种信息，比如params，path等等
  }
})
```

2.0改成用watch监听

```javascript
new Vue({
  watch: {
    '$store' () {
      // ...
    }
  }
})
```

路由信息通过`this.$route`获取，路由实例是`this.$router`。

## filter

1.0的过滤器filter可以在指令中使用，比如说

```html
<div v-html="startTime | date"></div>
```

2.0将filter改成只能在取值的时候使用，而不能在指令中使用

```html
<div>{{startTime | date}}</div>
```

## 数据必须提前声明

1.0没有提前声明数据并不会有任何问题。

2.0如果提前声明数据就会有警告。

## for遍历中的$index

1.0的for遍历可以通过这种方式拿到$index

```html
<li v-for="item in items">
    {{$index}}
</li>
```

2.0这取消这种快捷写法，改成必须提前声明

```html
<li v-for="(item, index) in items">
    {{index}}
</li>
```

## 取消数组的$set和$remove方法

1.0可以这样子操作数组

```javascript
vm.list.$set(index, item)
vm.list.$remove(item)
```

2.0将$set改成全局的Vue.$set，$remove改用splice

```
Vue.set(list, index, item)
vm.list.splice(index, 1)
```

## 数据绑定的写法

1.0可以这样子绑定数据

```html
<div href="{{item.url}}"></div>
```

2.0不允许在内联属性中使用插值符号，所以要这么做

```html
<div :href="item.url"></div>
```

## vuex中getters和actions

1.0中getters和actions的写法

```javascript
new Vue({
  vuex: {
    actions: {
      getUserInfo
    },
    getters: {
      userId: ({ userInfo }) => userInfo.id,
    }
  }
})
```

2.0的写法是

```javascript
import { setTip } from '../../vuex/actions/doc_actions'
import { mapGetters } from 'vuex'

computed: {
  ...mapGetters({
    userId
  })
}
```

而action的调用方式为`this.$store.dispatch(action_name, payload)`

[1]:	http://element.eleme.io/#/zh-CN
[2]:	https://github.com/vuejs/vue-migration-helper