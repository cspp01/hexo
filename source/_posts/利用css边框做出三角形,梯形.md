---
title: 利用css边框做出三角形,梯形
date: 2017-04-5 08:15:23
tags: ['css','css3']
categories: css
---
在网页中常能看到三角形，可是我们都知道网页中只有矩形边框，那这些三角形是怎么做出来的呢。其实做出这些三角形是利用了边框。如果了解边宽的话应该都知道边框的结构是下面这样的。
![enter image description here](http://ooa3lxrpg.bkt.clouddn.com/border.jpg?imageView2/0/q/75|watermark/2/text/d3d3LmNjYmxvZy53aW4=/font/6buR5L2T/fontsize/600/fill/I0Y2RjZGNg==/dissolve/85/gravity/SouthEast/dx/10/dy/10)
如果我将width,height以及padding都设为0,也就是上图区域1为none,那么渐变为下图这样。
![enter image description here](http://ooa3lxrpg.bkt.clouddn.com/border1.jpg?imageView2/0/q/75|watermark/2/text/d3d3LmNjYmxvZy53aW4=/font/6buR5L2T/fontsize/600/fill/I0Y2RjZGNg==/dissolve/85/gravity/SouthEast/dx/10/dy/10)
是不是已经看到4个三角形了，对的，这就是我们需要的，接着就看你需要哪个方向的三角形，然后设置对边为none,侧边两边为透明就可以了，如下图：
![enter image description here](http://ooa3lxrpg.bkt.clouddn.com/border2.jpg?imageView2/0/q/75|watermark/2/text/d3d3LmNjYmxvZy53aW4=/font/6buR5L2T/fontsize/600/fill/I0Y2RjZGNg==/dissolve/85/gravity/SouthEast/dx/10/dy/10)
代码如下：
``` bash
width:0;
height:0;
border-top:40px solid yellow;
border-left:40px solid transparent;/*transparent和rgba(0,0,0,0)一样*/
border-right:40px solid transparent;
或者
width:0;
height:0;
border-width:40px 40px 0 40px;
border-color:yellow transparent;
border-style:solid;
```
当然如果给它一个width,就可以出现梯形了。

知识点虽小，但却很实用，如果再结合伪元素::before,::after，简直太好用了。
继续upupup
