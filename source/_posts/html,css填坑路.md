---
title: css,html填坑路
date: 2017-05-05 08:15:23
tags: ['html','css3','css']
categories: htmlcss
---

### 前端填坑路
#### 1.外边距合并
例子：
1.子元素设置margin-top;父元素不设置margin-top;,但父元素会出现上边距，子元素相对父元素却不会出现。
 2.同级元素上面那个设置margin-bottom：下面那个设置margin-top:可是中间的间距却不是两个边距的和。
原因：
这个是css默认行为，因为元素没有找到另一个那个元素的边界，只在垂直方向的外边距合并，合并为边距中最大的那个，水平方向的不会，目的只是为了文档美观性（如：在文段落中间如果不合并就会出现两倍的边距，看起来不美观。），而且只发生在文档流中的块级元素，如果是行内块，浮动，和定位则不会合并。
解决：
1.1父元素设置
``` bash
overflow:hidden/auto;
```
1.2父元素设置
``` bash
border:1px solid #;
```
1.3用padding代替
``` bash
padding:
```
1.2兄弟间形成BFC
#### 2.img间隙
例子：
一个div中包含img图像时，图像最下面和div边框会有一些间隙。
原因：
由于html，css都是外国人发明的，所以默认字体是英文，而英文最好的展现方式是vertical-align:baseline;而img是行内块元素，所以默认垂直对齐方式也为vertical-align:baseline;，所以会出现间隙；
解决：
``` bash
vertical-align:middle/bottom;
```
#### 3.行内块水平方向之间的间隔
列子：
``` bash
<div style="display:inline-block">1</div>
<div style="display:inline-block">2</div>
<div style="display:inline-block">3</div>
```
原因：
行内块也有行内元素的特性，所以浏览器把换行解析为一个空格。
解决：
1.不换行
``` bash
<div style="display:inline-block">1</div><div style="display:inline-block">2</div><div style="display:inline-block">3</div>
```
2.margin设负值，负回去
3.把父元素的font-size:设为0;
``` bash
<div style="font-size:0;">
	<div style="display:inline-block">1</div>
	<div style="display:inline-block">2</div>
	<div style="display:inline-block">3</div>
</div>
```
#### 4.p标签不能放块级元素
列子：
记得刚开始敲代码时就把div放进p标签里去了，后来在css中通过p标签找div却找不到，f12后才发现div自动被解析到p外面去了。才知道了p不能放块级元素。
解决：
不呢个解决，反正就不能放。
####  5.行内元素设置margin-top;margin-bottom;无效
就是无效，记住就行。
#### 6.塌陷
列子：
下边列子ul没高度，这就是塌陷了。
``` bash
<ul>
	<li style="float:left;width:200px,height:200px"></li>
	<li style="float:left;width:200px,height:200px"></li>
</ul>
```
原因：
li设为浮动后，脱离文档流，所以这时候ul找不见它的子元素li了，所以没高度了。
解决：这个问题太常见了，但ul没设置背景或边框也很容易被忽略。解决方法比较多，下面只列了最常使用的方法，其他方法可查看我另一篇介绍关于塌陷的博文。
``` bash
<style>
ul:after{
	content:'';
	display:table;
	clear:both;
}
ul{
	zoom:1/*为了兼容低版本ie*/
}
</style>
<ul>
	<li style="float:left;width:200px,height:200px"></li>
	<li style="float:left;width:200px,height:200px"></li>
</ul>
```
#### 7.opacity:0;背景内容都会透明
列子：
最常见的就是弹出框，如果父元素背景设置opacity:0;它的所有子元素也会透明。
原因：
opacity:属性使然。
解决：
1.背景和子元素分离.
2.背景透明使用rgba();
#### 8.父元素设置display:none;，子元素设置position:fixed;也看不到。
毕竟就算脱离文档，也不会脱离父元素。还是受父元素影响
#### 9.label for=""放a标签里或外面，for指向单选或多选框，点label却点不到。
背景：
可能有人会说你为什么会这么做，感觉没必要。
其实我当时是想试着用a标签指向不同的id,看可不可以做个选项卡，没想到点不同的a标签确实可以在设置了overflow:hidden;的div框里显示不同的选项，视觉上很像选项卡。最后就剩点不同的a标签，给a标签加个选中状态了，当时想的是用input的伪类:checked来做，于是就出现了上面的坑。
原因：
不管怎样，点的都是a标签。
解决：
没办法，最后只能不用a标签指向id来做，都使用了::checked来做。
#### 10.子元素中有设置了position:absolute;的，其他子元素没法到设置了position:absolute;的上面
本身absolute就会提高层级，而z-index又是针对定位元素的，所以只能把其他元素设为相对定位，然后使用z-index来提高层级。
#### 11.加css3过渡效果，如果是width或height，过渡到的状态不能设为auto
列子：
``` bash
div{
	width:100px;
	height:100px;
	transition-property:height;
	transition-duration:2s;
}
div:hover{
	height:auto;
}
```
解决：
设固定数值的宽高。
#### 12.给a标签加js点击事件，点击无效果（好坑，因为这蓝飞了半个来小时。）
原因：
a标签href为空,为空会重新刷新页面，使得点击无效果。
解决：
href="javascript:void(0);"或href="#";
#### 持续总结更新中。。。。。。

以上都是本人在实际操作中遇到的坑，这些坑对于有些人可能不是坑。但对于我来说是，毕竟每个人遇到的坑相对的都不一样。希望这些坑的解决方式方法对你有所帮助。
