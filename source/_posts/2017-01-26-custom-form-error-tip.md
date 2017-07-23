---
title: 【教程】自定义表单报错信息 + 限制薪水下限不能低于薪水上限
categories: 全栈营
---

## 如何自定义表单报错信息

在教材的job-listing中，很多输入框的报错信息都是默认的`can't be blank`，如下图

![][image-1]

我们可以修改一下，增加自定义的报错信息，如下图

![][image-2]

方法：

打开`models/job.rb`，原先可能是长这个样子的：

```
validates :title, presence: true
validates :wage_lower_bound, presence: true
validates :wage_upper_bound, presence: true
validates :wage_lower_bound, numericality: { greater_than: 0 }
```

把它改成这样：

```
validates :title, presence: { message: "请填写标题" }
validates :wage_upper_bound, presence: { message: "请填写最低薪水" }
validates :wage_lower_bound, presence: { message: "请填写最高薪水" }
validates :wage_lower_bound, numericality: { greater_than: 0, message: "最小薪水必须大于零" }
```

done!

## 如何限制薪水下限不能低于薪水上限

方法：

打开`models/job.rb`，加上一句：

```
validates :wage_lower_bound, numericality: { less_than: :wage_upper_bound, message: "薪水下限不能低于薪水上限" }
```

![][image-3]

done!



参考链接：http://guides.rubyonrails.org/active\_record\_validations.html#numericality

---

ps：我正在持续更新我的魔改作品：[NewJob][1]，喜欢的话，多多支持。

[1]:	https://fullstack.xinshengdaxue.com/works/21

[image-1]:	http://oggx6lf7f.bkt.clouddn.com/lppii.png
[image-2]:	http://oggx6lf7f.bkt.clouddn.com/nxkml.png
[image-3]:	http://oggx6lf7f.bkt.clouddn.com/wr46i.png