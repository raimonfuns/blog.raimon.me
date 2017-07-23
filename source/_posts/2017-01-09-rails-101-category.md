---
title: rails101 动作分解
categories: 全栈营
---

### bootstrap配置

- [帮 Rails 专案穿上衣服“Bootstrap”](https://fullstack.xinshengdaxue.com/posts/55)
  - add bootstrap to project
- [套用 Bootstrap 的 html 样式](https://fullstack.xinshengdaxue.com/posts/56)
  - add bootstrap html
- [制作漂亮的“提示讯息”](https://fullstack.xinshengdaxue.com/posts/57)
  - add bootstrap flash function

### 建立一个讨论组

- [建立讨论群的架构](https://fullstack.xinshengdaxue.com/posts/59)
  - create groups index
- [将首页换成讨论群一览表](https://fullstack.xinshengdaxue.com/posts/60)
  - replace root with groups#index

### 手动实做讨论组的“新增”“修改”“删除”功能

- [实作讨论群“新增”功能](https://fullstack.xinshengdaxue.com/posts/62)
  - implement groups#new
- [实作讨论群“浏览”功能](https://fullstack.xinshengdaxue.com/posts/63)
  - implement groups#create
- [实作讨论群“修改”功能](https://fullstack.xinshengdaxue.com/posts/64)
  - implement groups#edit
  - implement groups#update
- [实作讨论群“删除”功能](https://fullstack.xinshengdaxue.com/posts/65)
  - implement groups#destroy
- [限制“标题为空”的文章，不能被送出](https://fullstack.xinshengdaxue.com/posts/66)
  - add validation to title
  - add validation to title apply to edit/update
- [共用“表单”](https://fullstack.xinshengdaxue.com/posts/67)
  - move form to partial
- [将表单换为 Bootstrap 提供的版型](https://fullstack.xinshengdaxue.com/posts/68)
  - style form with bootstrap
  - replace form with simple_form bootstrap template

### 加入使用者功能

- [安装 devise gem](https://fullstack.xinshengdaxue.com/posts/71)
  - install devise
- [这个网站有实际“登入”、“登出”的功能](https://fullstack.xinshengdaxue.com/posts/72)
  - user can login/logout/signup
- [让“群组”与“使用者”产生关联](https://fullstack.xinshengdaxue.com/posts/73)
  - add user_id to group
  - show group's creator info
- [只有群组的“创始者”可以“修改”“删除”群组资讯](https://fullstack.xinshengdaxue.com/posts/74)
  - people can't see edit button unless he is group owner
  - check owner permission when access edit/update/destroy
  - use before_action to find_group_and_check_permission
  - add permission check on show page

### 在讨论组里面“发表文章”

- [建立文章的架构](https://fullstack.xinshengdaxue.com/posts/76)
  - add post and hook group/user relation
  - add posts nested route
  - add post button
- [实际发表文章](https://fullstack.xinshengdaxue.com/posts/77)
  - implement post create function
- [文章应该按照发表时间倒序排列](https://fullstack.xinshengdaxue.com/posts/78)
  - add order by created_at to group's post
  - using scope to write order by created_at to group's post
- [加入文章分页功能](https://fullstack.xinshengdaxue.com/posts/79)
  - implement posts pagination with will_paginate

### 使用者应该要“加入社团”才能发表文章

- [建立“群成员”资料表](https://fullstack.xinshengdaxue.com/posts/81)
  - implement group relation
- [在群组里面判断“是否群组成员”实作](https://fullstack.xinshengdaxue.com/posts/82)
  - implement is_member_of?(group)
- [“加入群组”或“退出群组”](https://fullstack.xinshengdaxue.com/posts/83)
  - join or quit group
- [实际操作“加入群组”或“退出群组”](https://fullstack.xinshengdaxue.com/posts/84)
  - join & quit group action
- [User 在建立 group 后自动成为 group 的一员](https://fullstack.xinshengdaxue.com/posts/85)
  - when created a group, join it automatically

### 使用者可以在“自己的后台”看过曾经发表的文章、以及创立的社团

- [可以看到自己参与的所有群组](https://fullstack.xinshengdaxue.com/posts/87)
  - implement my groups
- [可以看到自己发表的所有文章](https://fullstack.xinshengdaxue.com/posts/88)
  - implement my posts

### 修饰细节，使用 Helper 与 Partial

- [系统内建 Helper “simple_format”的使用](https://fullstack.xinshengdaxue.com/posts/90)
  - use simple_format helper to decorate
- [使用自定义 Helper](https://fullstack.xinshengdaxue.com/posts/91)
  - use self delimit helper
- [partial 还可以这样用](https://fullstack.xinshengdaxue.com/posts/92)
  - render partial with collection
