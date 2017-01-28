---
title: 【教程】如何清空heroku上面的数据
categories: Ruby on Rails全栈训练营
---

当第一次把job-listing提交到heroku之后，运行`heroku run rake db:seed`，产生了10个publish工作和10个hidden工作。

为了让网站的内容显得更加真实，今天把在`seed.rb`里面，把所有职位的描述都改成真实的招聘要求，然后重新提交到heroku上面，运行`heroku run rake db:seed`，结果发现之前的20个工作还在，反而多了20个工作，总共40个！

这是因为在`seed.rb`里面，只执行增加，而没有执行删除。于是，我就打算把数据清空，先在本地执行`rake db:reset`，结果和我预期的一样，只剩下新的20个工作。接着我在heroku上面运行`rake db:reset`，结果报错了

![][image-1]

貌似清空数据库这个操作比较危险，用这种方式不能正常地执行。

后来，想到[rails101教材，5-4 让“群组”与“使用者”产生关联][1]这一节，里面有个步骤：`删除所有“无主”的群组`，用的命令是`Group.delete_all`，所以，我打算在heroku上面尝试一下这种方法。

![][image-2]

发现这个方法真的行得通，可以看到数据已经删除了。于是我在运行`heroku run rake db:seed`，done！

![][image-3]

注意：现在是学习阶段，可以不断地尝试，试错。但是以后在正式环境中，清空数据库是一个非常危险的操作，所以，要谨慎操作。

---

ps：我正在持续更新我的魔改作品：[NewJob][2]，喜欢的话，多多支持。

[1]:	https://fullstack.xinshengdaxue.com/posts/73
[2]:	https://fullstack.xinshengdaxue.com/works/21

[image-1]:	http://oggx6lf7f.bkt.clouddn.com/v3grj.png
[image-2]:	http://oggx6lf7f.bkt.clouddn.com/u5rv0.png
[image-3]:	https://vipweb.bs2cdn.yy.com/vipinter_eb9b195a72e64a5cacdf437f32464c09.png