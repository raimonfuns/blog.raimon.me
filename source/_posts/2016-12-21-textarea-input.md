---
title: 【错误】textarea为啥变成了input？
categories: 全栈营

---

## 位置

《rails 101》4-8节：将表单换为 Bootstrap 提供的版型。

## 动作

使用`simple_form`简化表单

## 预期结果

![](http://oggx6lf7f.bkt.clouddn.com/k2owp.jpg)

## 错误结果

![](http://oggx6lf7f.bkt.clouddn.com/ixyqh.jpg)

## 分析

首先，上`simple_form`[官网](https://github.com/plataformatec/simple_form)看看寻找解决方法，看到这样一句话：

![](http://oggx6lf7f.bkt.clouddn.com/d07z3.jpg)

也就是说，有可能是我创建model时，把description的类型设置成了`string`，而不是`text`。

于是，我看了一下db里面的文件，果然

![](http://oggx6lf7f.bkt.clouddn.com/4zlkt.jpg)

证据确凿，真的是类型搞错了。

## 解决方法

### step1

执行`rails g migration change_description_type_in_groups`创建migrate

### step2

在`db/migrate`目录中，打开刚才生成的文件，让它变成这样：

```ruby
class ChangeDescriptionTypeInGroup < ActiveRecord::Migration[5.0]
  def change
  	change_column :groups, :description, :text
  end
end
```

### step3

运行`rake db:migrate`，done！

## 参考链接

[http://stackoverflow.com/questions/5191405/change-a-column-type-from-date-to-datetime-during-ror-migration](http://stackoverflow.com/questions/5191405/change-a-column-type-from-date-to-datetime-during-ror-migration)