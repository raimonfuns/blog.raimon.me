# 「一步一步做出小小食杂铺」前端分享系列2 — logo + search + 购物车

## 目标

![](https://ww2.sinaimg.cn/large/006tKfTcgy1fcvn1e419aj31kw04qgmm.jpg)

## 步骤

实现logo + search + 购物车

### step1：先贴html代码

```html
<div class="header">
  <div class="logo"><a href="/products">小小食杂铺</a></div>

  <div>
	  <div class="search">
		  <form action="/products/search" accept-charset="UTF-8" method="get">
		  	<input name="utf8" type="hidden" value="✓">
		    <input class="search-input" type="text" name="query_string" value="" placeholder="输入你要搜索的商品">
		    <button type="submit" class="search-button pa tc"><i class="fa fa-search"></i></button>
			</form>
		</div>
	</div>
	
	<div class="cart-wrap">
	  <div class="cart">
			<a href="/carts">
		     <i class="fa fa-shopping-cart cart-icon "></i>我的购物车(0) &gt;
			</a>
		</div>
	</div>
</div>
```

实例代码我已经帮你备好了，来这里：[http://codepen.io/raimonfuns/pen/xgoKqz](http://codepen.io/raimonfuns/pen/xgoKqz)

后面的步骤，大家可以在css区域跟着贴代码。

![](https://ww2.sinaimg.cn/large/006tKfTcly1fcuwiolppfj30hk09zglk.jpg)

## step2：写CSS代码

```
.header {
  width: 1200px; /*宽度1200px*/ 
  margin: 0 auto; /*水平居中*/
  margin-top: 30px; /*上边距*/
}
```

宽度1200px，水平居中

![](https://ww1.sinaimg.cn/large/006tNc79gy1fcvuqznib0j31kw06xab1.jpg)

先写logo的样式

```css
.logo {
  float: left; /*logo、seatch、cart这三个模块都是用div包起来的，是block元素，如果要处于同一行，那就要加float*/
  margin-right: 180px; /*加点右边距，和search*/
}

.logo a {
  font-size: 36px; /*设置字体36px*/
  color: #C81623; /*红色*/
  text-decoration: none; /*不要下划线*/
}
```

![](https://ww1.sinaimg.cn/large/006tNc79gy1fcvusoeexbj31kw05dwfj.jpg)

logo搞定了，接下来做搜索模块

```css
.search {
  float: left; /*logo、seatch、cart这三个模块都是用div包起来的，是block元素，如果要处于同一行，那就要加float*/
  width: 400px; 
  margin-left: 40px; /*右边距*/
  margin-top: 10px; /*上边距*/
  position: relative; /*相对定位*/
}

.search-input {
  width: 400px; 
  height: 36px; 
  line-height: 36px; /*设置行高，实现垂直居中，口诀「如果高度等于行高，那就实现了文本的垂直居中」*/
  color: #666; 
  padding: 4px 20px; /*调一下上下左右边距*/
  border-width: 2px; /*边框宽度为2px*/
  border-color: #D32048; /*设置边框颜色为红色*/
  border-style: solid; /*设置为实线*/
  font-size: 14px; /*字体14px*/
  font-family: "microsoft yahei"; /*设置成微软雅黑作品*/
  border-radius: 20px; /*圆角20px*/
}

.search-button {
  width: 54px; 
  height: 36px; 
  border: none; /*去掉button默认的border*/
  background: none; /*去掉button默认的背景颜色*/
  font-family: "Microsoft YaHei"; 
  font-size: 16px; 
  position: absolute; /*绝对定位*/
  cursor: pointer; /*鼠标一上去，显示手型*/
  top: 0; 
  right: 0; 
}

.search-button .fa-search {
  color: #d32048; /*搜索图标的颜色*/
}
```

![](https://ww4.sinaimg.cn/large/006tNc79gy1fcvutyh0rqj31kw05cmya.jpg)

搜索也可以了，最后写「我的购物车」代码

```css
.cart-wrap {
  float: left; /*logo、seatch、cart这三个模块都是用div包起来的，是block元素，如果要处于同一行，那就要加float*/
  margin-top: 10px; /*上边距*/
  margin-left: 238px; /*左边距*/
}

.cart {
  padding: 8px 20px; /*加内边距*/
  cursor: pointer; /*鼠标一上去，显示手型*/
  border: 1px solid #DFDFDF; /*1像素，实线，灰色*/
  background: #F5F5F5; /*灰色背景*/
  font-size: 12px; /*字体小一点好看*/
}

.fa-shopping-cart {
  color: #C81623; /*红色图标*/
  font-size: 16px; /*图标大一点好看*/
  margin-right: 10px; /*右边距*/
}

.cart a {
  color: #6D6D6D; /*灰色字体*/
  text-decoration: none; /*不要下划线*/
}

.cart a:hover {
  color: #C81623; /*鼠标一上去的时候，字体变成红色*/  
}
```

![](https://ww1.sinaimg.cn/large/006tNc79gy1fcvv03b4vdj31kw05igmp.jpg)

done!

最终代码示例：[http://codepen.io/raimonfuns/pen/rjENJb?editors=1100](http://codepen.io/raimonfuns/pen/rjENJb?editors=1100)。

## 总结一下

- 高度等于行高，就实现了垂直居中。
- float可以让block元素处于同一行。
- 绝对定位和相对定位比较难解释，大家可以写在笔记里面，然后再慢慢搞懂就可以了。



未完待续，敬请期待。如果你有什么建议，欢迎留言！

------

ps：如果教程对大家有帮助的话，希望能为「[小小食杂铺](https://fullstack.xinshengdaxue.com/works/201)」投上一票哈。