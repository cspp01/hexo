---
title: hsl颜色表示法
date: 2017-03-19 08:15:23
tags: ['css','颜色','hsl','css3']
categories: css3
---

css颜色表示法通常常用和最常见的三种
``` bash
background-color:red;
background-color:#ff0000;
background-color:rgb(255,0,0);
```
hsl颜色表示法，不知大家用没用过，反正我到我写这篇博客之前一直没用过。
``` bash
backgroud-color:hsl(0,100%,54%);
```
是不是感觉写法和rgb很像，rgb分别代表三原色，hsl分别代表色调(h)，饱和度(s)，亮度(l)，了解颜色或用过ps（ps的三通道）的应该很了解，这种标准是目前运用最广的颜色系统之一。
h：取值（0~360）0和360表示红色，120表绿色，240表示蓝色；
s：0%~100%；
l：0%~100%；
如果想给他加透明，写法和rgb一毛一样，
``` bash
backgroud-color:hsla(0,100%,54%,.5);
```
不过由于是css3属性，浏览器必须支持css3才可以。
