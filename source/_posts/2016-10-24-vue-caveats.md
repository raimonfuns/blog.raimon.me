---
title: 使用vue容易犯的错误
categories: Javascript


---

- [在data里面声明的属性才是reactive][1]。在声明vue实例之后，如果要添加reactive的变量，可以通过[set方法][2]。
- 在vue实例的属性或者回调函数中，[使用箭头函数][3]，因为使用箭头函数，this就不是指向vue实例，而是指向父级作用域。
- `vm.items[indexOfItem] = newValue`更新数据，但不会更新视图，应该使用[set方法][4]。
- `vm.items.length = newLength`更新数据，但不会更新视图，应该使用[splice方法][5]
- [component的data必须是一个函数][6]，而且必须返回一个干净的对象（fresh data object），如果不是一个干净的对象，那么所有的组件都会引用同一个对象，这不是我们想要的结果。
- [camelCase vs kebab-case][7]。组件的props在js里面是camelCase写法，而在HTML里面是kebab-case写法。同理，[组件的命名][8]也是如此。
- [Literal vs Dynamic][9]。如果想要给子组件传递一个数字而不是字符串，那就要使用v-bind。
- [One Way Data Flow][10]。父组件可以修改props，但子组件不允许修改props，也就说数据的单向的，只允许 `父 -> 子`，不允许 `子 -> 父`。子组件要改变父组件的数据只能通过events up。父子组件的通信方式可以总结为：[props down, events up][11]。
- [Compilation-Scope][12]。父组件的模板只能使用父组件作用域里面的变量，子组件的模板只能使用子组件作用域里面的变量。
- [Child Component Refs][13]。子组件的$refs不是reactive的，所以不要用在template或者computed

[1]:	http://vuejs.org/guide/instance.html#Properties-and-Methods
[2]:	http://vuejs.org/guide/reactivity.html#Change-Detection-Caveats
[3]:	http://vuejs.org/guide/instance.html#Properties-and-Methods
[4]:	http://vuejs.org/guide/list.html#Caveats
[5]:	http://vuejs.org/guide/list.html#Caveats
[6]:	http://vuejs.org/guide/components.html#data-Must-Be-a-Function
[7]:	http://vuejs.org/guide/components.html#camelCase-vs-kebab-case
[8]:	http://vuejs.org/guide/components.html#Component-Naming-Conventions
[9]:	http://vuejs.org/guide/components.html#Literal-vs-Dynamic
[10]:	http://vuejs.org/guide/components.html#One-Way-Data-Flow
[11]:	http://vuejs.org/guide/components.html#Composing-Components
[12]:	http://vuejs.org/guide/components.html#Compilation-Scope
[13]:	http://vuejs.org/guide/components.html#Child-Component-Refs