---
title: 布局解决方案之「多列布局」
categories: CSS
---

常见的页面布局有：两列布局，多列布局，等分布局，等高布局，然后再加上一些自适应布局。

## 定宽 + 自适应

![](http://oggx6lf7f.bkt.clouddn.com/bpt48.png)

### float + margin

<p data-height="265" data-theme-id="0" data-slug-hash="LxexrB" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="两列布局:float + margin" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/LxexrB/">两列布局:float + margin</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：简单，很容易理解
- 缺点：IE6有一些bug

### float + margin + (fix)

<p data-height="265" data-theme-id="0" data-slug-hash="MJrJLo" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="两列布局:float + margin + (fix)" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/MJrJLo/">两列布局:float + margin + (fix)</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：简单，很容易理解，不存在兼容性问题
- 缺点：1. 你试着选中left的文案就会发现，left的文案无法被选中，因为left被right遮住，解决方法是用`position: relative`提高left的层级。

### float + overflow

<p data-height="265" data-theme-id="0" data-slug-hash="jyYyoy" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="两列布局:float + overflow" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/jyYyoy/">两列布局:float + overflow</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：写法简单

### table

<p data-height="265" data-theme-id="0" data-slug-hash="vgpgqw" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="两列布局:table" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/vgpgqw/">两列布局:table</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 缺点：不能设置margin，只能设置padding，代码比较多。

### flex

<p data-height="265" data-theme-id="0" data-slug-hash="LxeWPM" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="两列布局:flex" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/LxeWPM/">两列布局:flex</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：功能强大！代码少
- 缺点：内部标签太多的话会有性能问题，所以只能用来做小范围的布局。



## 定宽 + 定宽 + 自适应

![](http://oggx6lf7f.bkt.clouddn.com/ywv4h.png)

<p data-height="265" data-theme-id="0" data-slug-hash="ggompp" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="多列布局" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/ggompp/">多列布局</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

## 不定宽 + 自适应

![](http://oggx6lf7f.bkt.clouddn.com/9k6nz.png)

### float + overflow

<p data-height="265" data-theme-id="0" data-slug-hash="WRdprR" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="【不定宽 + 自适应】float + overflow" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/WRdprR/">【不定宽 + 自适应】float + overflow</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

### table

<p data-height="265" data-theme-id="0" data-slug-hash="WRdpGp" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="【不定宽 + 自适应】table" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/WRdpGp/">【不定宽 + 自适应】table</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

### flex

<p data-height="265" data-theme-id="0" data-slug-hash="apEJBQ" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="【不定宽 + 自适应】flex" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/apEJBQ/">【不定宽 + 自适应】flex</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

## 不定宽 + 不定宽 + 自适应

![](http://oggx6lf7f.bkt.clouddn.com/1cii7.png)

<p data-height="265" data-theme-id="0" data-slug-hash="rjpyyr" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="【多列布局 + 自适应】" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/rjpyyr/">【多列布局 + 自适应】</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

## 等分布局

![](http://oggx6lf7f.bkt.clouddn.com/4qwxe.png)

![](http://oggx6lf7f.bkt.clouddn.com/pf76c.png)

### float

<p data-height="265" data-theme-id="0" data-slug-hash="ygpMbv" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="等分布局: float" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/ygpMbv/">等分布局: float</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：高级浏览器全兼容
- 缺点：列数和百分比高度百分比耦合性太高，也就是说一旦列数改变，宽度百分比就得有相应的改变。

#### table

<p data-height="265" data-theme-id="0" data-slug-hash="qRpmbO" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="等分布局: table" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/qRpmbO/">等分布局: table</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：结构和样式彻底解耦，因为table加了`table-layout: fixed`会自动平分所有单元格
- 缺点：加了一层标签

### flex

<p data-height="265" data-theme-id="0" data-slug-hash="PWEmWE" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="等分布局: flex" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/PWEmWE/">等分布局: flex</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：代码简洁。结构和样式彻底解耦，因为table加了`table-layout: fixed`会自动平分所有单元格。
- 缺点：兼容性问题

## 等高布局

![](http://oggx6lf7f.bkt.clouddn.com/rbeh5.png)

### table

<p data-height="265" data-theme-id="0" data-slug-hash="YNYVVV" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="等高布局:table" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/YNYVVV/">等高布局:table</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

### flex

<p data-height="265" data-theme-id="0" data-slug-hash="MJrmvd" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="等高布局:flex" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/MJrmvd/">等高布局:flex</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>



## 总结

以上是网站最常用，最高频的布局方式，把这些学会，并且记住，多练习，以后再遇到类似的布局时，就能信手拈来，快速地把页面写出来！
