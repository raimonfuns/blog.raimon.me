---
title: 【全栈日记】2016/12/08
categories: Ruby on Rails全栈训练营
---

## Objective

下班之后，花一个半小时，做第三遍rails 101，完成1-5节。

## Relective

做第三次遍，感觉越来越熟练了，敲代码的速度也更快了，很有成就感。

## Interpretive

### git 存档

平时做项目时，经常会改很多很多东西，然后要提交git时才发现，怎么修改了这么多！！！经常搞不清楚到底哪个步骤修改了哪些文件，最终往往会写一句可能以后自己都看不懂的提交信息，草草了事。在练习rails101时，因为rails101的教程对项目进行了分解，每一个步骤对应一次commit，目标明确，循序渐进，写完一节就提交一节，所以我才发现，原来每次只做一件小事情，做好了就马上提交，一点都不会乱，这点我是学到了，很棒。

### 漏写了无数次的 “end”

犯错误最多的就是忘了写end，所以我决定每次写if或者循环等语法时，先把end写了再说，养成一个好习惯。

### 慢慢地能默写了

已经做了两遍rails，在做第三遍时，已经比较熟练了，比较意外的是，竟然可以在看了教程的一句引导词之后，可以不看后面的步骤，自己把下一步给写出来了，比如说CRUD，这非常有成就感，真是熟能生巧呀。

### 情不自禁地和nodejs做比较

平时学后端用nodejs，所以不自觉地会比较ruby on rails(RoR)和nodejs，最让我刚到惊讶的是，rails帮开发者做了很多很多事情，就拿路由来说，rails只需要在routes.rb写一句

```rub
resources :groups
```

它就能帮你生成7个Action

```ruby
              groups GET    /groups(.:format)              groups#index
                     POST   /groups(.:format)              groups#create
           new_group GET    /groups/new(.:format)          groups#new
          edit_group GET    /groups/:id/edit(.:format)     groups#edit
               group GET    /groups/:id(.:format)          groups#show
                     PATCH  /groups/:id(.:format)          groups#update
                     PUT    /groups/:id(.:format)          groups#update
                     DELETE /groups/:id(.:format)          groups#destroy
                root GET    /                              groups#index
```

如果用nodejs的框架koa来写的话，是需要一个一个手动定义的

```javascript
router.get('/', controller.getUser)
router.post('/', controller.addUser)
router.put('/', controller.updateUser)
router.delete('/:id', controller.destroy)
...
```

因为rails帮开发者做很多事情，所以开发者的开发效率会更高。

另外，发现了一个node和RoR一个很相似的地方，那就是rails的`gemfile`和node的`package.json`，都是用来安装一些模块的，RoR的安装命令是`bundle install `，而node是`npm install`。

### ApplicationRecord 和 ActiveRecord

用rails创建model时，默认是长这个样子的

```ruby
class Group < ApplicationRecord
end

```

教程要求把`ApplicationRecord`改成`ActiveRecord::Base`，但是因为教程没有明说，所以我经常忘记。现在我还弄不清楚为什么要改成`ActiveRecord::Base`，所以先背起来再说。

### 良好的编程规范

rails提供的一些功能是有助于帮助程序员养成良好的习惯的，比如说

- html模板代码重复太多，冗余了把？用partial。
- 很多请求都要先经过登录认证吧？用before_action。
- 很多html模板都需要用到工具函数吧？用Helper。
- 很多action里面都用到同一个函数吗？把它封装成函数，写在private里面。

### 做得越多，想写的东西就越多。

一开始做的时候，感觉没有可以写，于是就偷懒没写学习日记，随着练习次数的增加，学到的东西越来越多，慢慢地就开始有很多东西可以写了，继续保持。

### 加入一个登录系统也太轻松了吧？

前阵子有nodejs开发一套登录系统，费力很大的劲，还算是比较复杂的，开发起来有点麻烦，而RoR可以直接使用devise模块，直接搞定登录系统，哇塞，太轻松了吧。

### <% %> 和 <%= %>

这两者经常搞混，虽然现在也没有彻底弄清楚，不过还是发现一些规律的，很多情况下，都用到`<%= %>`，比如说

```ruby
<h2><%= @group.title %></h2>

<%= link_to("Edit", edit_group_path(@group), class: "btn btn-primary pull-right") %>

<%= f.input :title, input_html: { class: "form-control"} %>

<%= render "common/navbar" %>
```

而`<% %>`是用在一些判断或者遍历的关键词上面的，比如说

```ruby
<% if current_user && current_user == @group.user %>

<% end %>
```

```ruby
<% @groups.each do |group| %>

<% end %>
```

## Decisional

放下之前无效的学习方式，摒弃傲慢的态度，一心一意按照教程的指示做，养成好的学习习惯，相信一定会有惊喜的。
