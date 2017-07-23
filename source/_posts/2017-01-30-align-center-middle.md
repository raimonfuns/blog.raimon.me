---
title: 布局解决方案之「居中布局」
categories: CSS
---

居中布局在网页中很常见，出现频率极高 ，所以有必要总结一下所有居中布局的方法。主要分为3种情况：

- 水平居中
- 垂直居中
- 水平居中 + 垂直居中

下面的方法同样适用于**父子元素的高度、宽度都不确定**的情况。

## 水平居中

### inline-block

<p data-height="265" data-theme-id="0" data-slug-hash="ygpVKd" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="【水平居中】display:inline-block" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/ygpVKd/">【水平居中】display:inline-block</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：兼容性好
- 缺点：child的文本也会居中

### table

<p data-height="265" data-theme-id="0" data-slug-hash="VPymxz" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="【水平居中】display:table" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/VPymxz/">【水平居中】display:table</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：只设置child，不关心parent

### absolute+transform

<p data-height="265" data-theme-id="0" data-slug-hash="VPymBz" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="【水平居中】absolute+transform" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/VPymBz/">【水平居中】absolute+transform</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：不会对其他子元素产生影响
- 缺点：低版本浏览器不支持，高版本浏览器要加前缀

### flex + justify-content

<p data-height="265" data-theme-id="0" data-slug-hash="jyYVeo" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="【水平居中】flex + justify-content" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/jyYVeo/">【水平居中】flex + justify-content</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：只需设置parent
- 缺点：低版本浏览器不支持

## 垂直居中

### table-cell + vertical-align

<p data-height="365" data-theme-id="0" data-slug-hash="apEBMB" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="垂直居中: table-cell + vertical-align" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/apEBMB/">垂直居中: table-cell + vertical-align</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：兼容性好

### absolute + transform

<p data-height="365" data-theme-id="0" data-slug-hash="xgpReq" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="垂直居中: absolute + transform" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/xgpReq/">垂直居中: absolute + transform</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：不会对其他子元素产生影响
- 缺点：低版本浏览器不支持，高版本浏览器要加前缀

###  flex + align-items

<p data-height="365" data-theme-id="0" data-slug-hash="egyBaJ" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="垂直居中: flex + align-items" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/egyBaJ/">垂直居中: flex + align-items</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

- 优点：只需设置parent
- 缺点：低版本浏览器不支持

## 水平居中 + 垂直居中

### inline-block + text-align + table-cell + vertical-align

<p data-height="365" data-theme-id="0" data-slug-hash="GryNbB" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="水平垂直居中: inline-block + text-align + table-cell + vertical-align" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/GryNbB/">水平垂直居中: inline-block + text-align + table-cell + vertical-align</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>

### absolute + transform

<p data-height="365" data-theme-id="0" data-slug-hash="xgpgKd" data-default-tab="css,result" data-user="raimonfuns" data-embed-version="2" data-pen-title="水平垂直居中: absolute + transform" class="codepen">See the Pen <a href="http://codepen.io/raimonfuns/pen/xgpgKd/">水平垂直居中: absolute + transform</a> by raimonfuns (<a href="http://codepen.io/raimonfuns">@raimonfuns</a>) on <a href="http://codepen.io">CodePen</a>.</p>
<script async src="https://production-assets.codepen.io/assets/embed/ei.js"></script>

### 补充：inline-block和table兼容Ie6、7的方法

- display:inline-block -> display:inline; zoom: 1
- display:table -> 把结构换成table
