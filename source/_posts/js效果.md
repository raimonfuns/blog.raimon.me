这篇文章的目录：

- 前言
- 轮播图
- 回到顶部
- 图片切换
- 菜单栏的切换

## 前言

这是我做「小小食杂铺」时，用jquery实现的效果，希望对大家有帮助。

## 轮播图

html:

```html
<div id="myCarousel" class="carousel slide">
  <ol class="carousel-indicators">
    <li data-target="#myCarousel" data-slide-to="0" class="active"></li>
    <li data-target="#myCarousel" data-slide-to="1"></li>
    <li data-target="#myCarousel" data-slide-to="2"></li>
 </ol>
 <div class="carousel-inner">
    <div class="item active">
     <a href="javacript:;">
      <img src="https://ww2.sinaimg.cn/large/006tNc79ly1fcrl5afeqhj30xc0afgpx.jpg">
      <div class="carousel-caption"></div>
     </a>
    </div>
    <div class="item">
     <a href="javacript:;">
      <img src="https://vipweb.bs2cdn.yy.com/vipinter_de4f123bb220482e93649571a1491572.jpg">
      <div class="carousel-caption"></div>
     </a>
    </div>
    <div class="item">
     <a href="javacript:;">
      <img src="https://ww2.sinaimg.cn/large/006tNc79ly1fcrlcb0knhj30xc0afwib.jpg">
      <div class="carousel-caption"></div>
     </a>
    </div>
  </div>
</div>
```

在application.scss加上

```css
.carousel {
  width: 1200px;
  margin: 0 auto;
}
.carousel .item {
  height: 375px;
}
```

在application.js顶部加入

```js
//= require bootstrap
```

然后在底部加上

```js
$('.carousel').carousel({
  interval: 2000 //目前是2秒播放一张，可以根据需要调整这个值
})
```

done!

效果：

![](https://ww1.sinaimg.cn/large/006tKfTcly1fczb89s9wbg30z50acqv5.gif)

实例代码：[轮播图](http://codepen.io/raimonfuns/pen/GWKoOM)

## 回到顶部

在_footer.html.erb加入

```html
<div id="gotop"></div>
```

在application.scss加入

```css
#gotop {
  width: 50px;
  height: 50px;
  position: fixed;
  right: 20px;
  bottom: 20px;
  background: #F25F5C;
  cursor: pointer;
}
```

在application.js加入

```javascript
$(document).ready(function() {
  $('#gotop').click(function () {
    $('body').animate({'scrollTop': 0}, 500)
  })
})
```

![](https://ww1.sinaimg.cn/large/006tKfTcgy1fczj8tczoug30z50f3h09.gif)

实例代码：[回到顶部](http://codepen.io/raimonfuns/pen/NpKpqX)

但其实，当页面在顶部时，是不需要显示「gotop按钮」的，所以，我们可以优化一下，当页面滚动下来之后，才显示「gotop按钮」。

修改application.scss

```css
#gotop {
  width: 50px;
  height: 50px;
  position: fixed;
  right: 20px;
  bottom: 20px;
  background: #F25F5C;
  cursor: pointer;
  display: none; /*默认先隐藏掉*/
}
```

修改application.js

```javascript
$(document).ready(function() {
  $('#gotop').click(function () {
    $('body').animate({'scrollTop': 0}, 500)
  })

  $(window).scroll(function () {
    if ($(this).scrollTop() > 500) { 
      $('#gotop').fadeIn() // 当页面向下滚动的距离大于500px时，慢慢地显示「回到顶部按钮」
    } else {
      $('#gotop').fadeOut() // 否则慢慢地隐藏「回到顶部按钮」
    }
  })
})
```

![](https://ww3.sinaimg.cn/large/006tKfTcgy1fczjdhsx6eg30z50f31ky.gif)

实例代码：[回到顶部优化版](http://codepen.io/raimonfuns/pen/wJwedG)

## 图片切换

html

```html
<div class="productDetail">
  <div class="productDetail-left">
    <div class="productDetail-left-bigImage">
      <img src="https://newsmallshop.s3.amazonaws.com/uploads/photo/avatar/892/medium_TB1V46qOFXXXXanXpXXXXXXXXXX___0-item_pic.jpg_430x430q90.jpg" />
    </div>
    <div class="productDetail-left-imageList">
      <div class="productDetail-left-imageList-item">
        <img src="https://newsmallshop.s3.amazonaws.com/uploads/photo/avatar/892/medium_TB1V46qOFXXXXanXpXXXXXXXXXX___0-item_pic.jpg_430x430q90.jpg" />
      </div>
      <div class="productDetail-left-imageList-item">
        <img src="https://newsmallshop.s3.amazonaws.com/uploads/photo/avatar/893/medium_TB21el5X9GI.eBjSspcXXcVjFXa___725677994.jpg_430x430q90.jpg" />
      </div>
      <div class="productDetail-left-imageList-item">
        <img src="https://newsmallshop.s3.amazonaws.com/uploads/photo/avatar/894/medium_TB2IATBX71M.eBjSZFOXXc0rFXa___725677994.jpg_430x430q90.jpg" />
      </div>
      <div class="productDetail-left-imageList-item">
        <img src="https://newsmallshop.s3.amazonaws.com/uploads/photo/avatar/895/medium_TB2DjSOdNBmpuFjSZFDXXXD8pXa___725677994.jpg_430x430q90.jpg" />
      </div>
      <div class="productDetail-left-imageList-item productDetail-left-imageList-lastItem">
        <img src="https://newsmallshop.s3.amazonaws.com/uploads/photo/avatar/891/medium_TB1V46qOFXXXXanXpXXXXXXXXXX___0-item_pic.jpg_430x430q90__1_.jpg" />
      </div>
    </div>
  </div>
</div>
```

在application.scss加上

```css
/*商品信息*/
.productDetail {
	width: 1200px;
	margin: 20px auto;
	height: 518px;
}

.productDetail img {
  width: 100%;
  height: 100%;
}

.productDetail-left {
	float: left; /*你去左边*/
	width: 420px;
	height: 518px;
}

.productDetail-right {
	float: right; /*你去右边*/
	width: 744px;
	height: 518px;
}

.productDetail-left-bigImage {
	width: 420px;
	height: 420px;
}

.productDetail-left-imageList {
	margin-top: 15px;
}

.productDetail-left-imageList-item {
	float: left; /*虽然我们是block元素，但是我们还是想在同一行呀，那就用float吧*/
	width: 72px;
	height: 72px;
	margin-right: 15px;
}

.productDetail-left-imageList-lastItem {
	margin-right: 0;
}
```

在application.js加上

```javascript
$(document).ready(function() {
	// 图片切换
	$('.productDetail-left-imageList-item').mouseover(function () {
	  var src = $(this).find('img').attr('src') //从被鼠标选中的图片的src里面拿到图片链接
	  $('.productDetail-left-bigImage').find('img').attr('src', src) //把图片链接设置到大图的src里面
	})
})
```

效果：

![](https://ww4.sinaimg.cn/large/006tKfTcgy1fczk14hbi7g30ev0ahapr.gif)

实例代码：[切换图片](http://codepen.io/raimonfuns/pen/aJoJgZ)

## 菜单栏的切换

html

```html
<div class="productDecription">
  <div class="productDecription-menuList bg-color1">
    <div class="productDecription-menuList-item bg-color2">选项卡1</div>
    <div class="productDecription-menuList-item bg-color3">选项卡2</div>
  </div>
  <div class="productDecription-content">
    <div class="productDecription-content-item bg-color4" style="display: block;">内容1</div>
    <div class="productDecription-content-item bg-color5">内容2</div>
  </div>
</div>
```

在application.scss加上

```css
/*5种背景颜色*/
.bg-color1 {
  background: #50514F; 
}

.bg-color2 {
  background: #F25F5C; 
}

.bg-color3 {
  background: #FFE066; 
}

.bg-color4 {
  background: #247BA0; 
}

.bg-color5 {
  background: #70C1B3; 
}

/*商品详情*/
.productDecription {
	width: 1200px;
  text-align: center;
	margin: 20px auto;
	border: 1px solid #50514F;
  line-height: 30px;
}

.productDecription-menuList {
	height: 35px;
}

.productDecription-menuList-item {
	float: left;
	width: 175px;
	height: 35px;
}

.productDecription-content {
	width: 750px;
  height: 500px;
	margin: 50px auto;
}

.productDecription-content-item {
  display: none;
  width: 750px;
  height: 500px;
}
```

在application.js加上

```javascript
$(document).ready(function() {
  $('.productDecription-menuList-item').click(function () {
    var index = $(this).index() //拿到这个「选项卡」的index，第一个是0，第二个是1，以此类推
    $('.productDecription-content-item').hide() //所有的内容都隐藏
    $('.productDecription-content-item').eq(index).show() //只显示对于index的内容
  })
})
```

效果：

![](https://ww3.sinaimg.cn/large/006tKfTcgy1fczktvvtdxg30z408dt92.gif)

实例代码：[选项卡切换](http://codepen.io/raimonfuns/pen/XMrRXd)

## 系列文章：

- [【一步一步做出小小食杂铺】前端分享系列1 — navbar导航栏](http://forum.qzy.camp/t/1-navbar/690)
- [「一步一步做出小小食杂铺」前端分享系列2 — logo + search + 购物车](http://forum.qzy.camp/t/2-logo-search/696)
- [【一步一步做出小小食杂铺】前端分享系列3 — 页面布局的高频小套路](http://forum.qzy.camp/t/topic/733)

未完待续，敬请期待。如果你有什么建议，欢迎留言！

------

ps：如果教程对大家有帮助的话，希望能为「[小小食杂铺](https://fullstack.xinshengdaxue.com/works/201)」投上一票哈。