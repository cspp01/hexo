---
title: 纯css点击效果
date: 2017-03-20 08:15:23
tags: ['css','css3']
categories: css
---
平时网页中如果需要出现点击效果的按钮或是菜单，你可能首先想到的是js的点击事件，实现这些利用js虽然也简单，但毕竟是脚本，运行起来，性能上还是会慢些，其实有些点击效果用css也可以实现，运行css那可就比js快多了，下面总结一些用纯css实现的点击效果。

### 1.利用单选框和复选框

#### 例如

#### 效果
![enter image description here](http://ooa3lxrpg.bkt.clouddn.com/1.gif)

html
``` bash
<input type="checkbox" id="p"><label for="p"></label>
```
css
``` bash
input[type='checkbox']{
			display:none;
		}
		label{
			display:inline-block;
			width:245px;
			height:81px;
			background:none;
			border:none;
			border-radius:40px;
			-moz-border-radius:40px;
			-webkit-border-radius:40px;
			-o-border-radius:40px;
			-ms-border-radius:40px;
			background:url('./images/button.jpg');
		}
		input:checked+label{
			background-position:245px top;
		}
```
不过由于利用了单选框和复选框的 :checked 来实现，所以需要支持css3的浏览器才可以。其实利用它最常用的就是改变单选复选框的样式，不过只要你想，它还可以实现很多效果，帮你减少使用js代码。就像下面这个例子。

#### 效果
![enter image description here](http://ooa3lxrpg.bkt.clouddn.com/pl.gif)
是不是很不错

###2.利用伪类:active

这应该是最容易想到，但也最容易忽略的。

效果
![enter image description here](http://ooa3lxrpg.bkt.clouddn.com/po.gif)

html
``` bash
<button class="button">click</button>
```
css
``` bash
.button {
    position: relative;
    background-color: #0d6ce2;
    border: none;
    font-size: 28px;
    color: #FFFFFF;
    padding: 20px;
    width: 200px;
    text-align: center;
	border-radius:20px;
	outline:none;
    -webkit-transition-duration: 0.4s; /* Safari */
    transition-duration: 0.4s;
    text-decoration: none;
    overflow: hidden;
    cursor: pointer;
}
.button:after {
    content: "";
    background: #fff;
    display: block;
    position: absolute;
	top:0;
	left:0;
    width:300px;
	height:300px;
    opacity: 0;
    transition: all 0.8s
}
.button:active:after {
    top:75px;
	right:200px;
    opacity: 1;
    transition: 0s
}
```
希望本篇博客对大家学习有所帮助。