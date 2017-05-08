---
title: css水平垂直居中
date: 2017-04-03 08:15:23
tags: ['css','css3']
categories: css
---
要让下图中绿色框水平垂直居中，你是怎么实现的，可能每个人都有自己习惯的使用方法。下面是我总结的几种方法废话不多说，直接上菜。
![enter image description here](http://ooa3lxrpg.bkt.clouddn.com/005K8nLYzy77M9vyXFM4a&690.png)
### 1.利用绝对定位

方法：把top和 left 偏移 50%，在用margin 偏移回去。
适合：已经固定大小的元素。做响应的话可能根据实际需要还需要js的操作。
``` bash
div1{
    background:gold;
    width:500px;
    height:500px;
    position:relative;
}
div2{
    width:400px;
    height:400px;
    background:greenyellow;
    position:absolute;
    top:50%;
    left:50%;
    margin-top:-200px;
    margin-left:-200px;
}
<div id="div1">
    <div id="div2">
    </div>
</div>
```
### 2..利用绝对定位

方法：把偏移都设为0，在用margin 自动属性居中。
适合：:已经固定大小的元素，不设置宽高，它会撑满整个父元素。
``` bash
   #div1{
        background:gold;
        width:500px;
        height:500px;
        position:relative;
    }
    #div2{
        position:absolute;
        top:0;
        bottom:0;
        left:0;
        right:0;
        width:400px;
        height:400px;
        margin:auto;
        background:greenyellow;
    }
<div id="div1">
    <div id="div2">
    </div>
</div>
```
### 3.利用伪元素
方法：div2和::after都转为inline-block，在父元素中设文本居中来达到元素水平居中，把伪元素宽度设为100%，然后div2和::after都垂直垂直对齐方式为middle。
适合：宽高不定的元素，元素会随内容改变大小，但不管怎么改变，就是可以始终维持垂直和水平置中。
``` bash
#div1{
            background:gold;
            width:500px;
            height:500px;
            text-align:center;
        }
        #div2{
            background:greenyellow;
            height:400px;
            width:400px;
            display:inline-block;
            vertical-align:middle;
        }
        #div1::after{
            content:'';
            height:100%;
            display:inline-block;
            background:green;
            vertical-align:middle;
       }
<div id="div1">
    <div id="div2">
    </div>
</div>
```
### 4.利用伪元素

这个方法和方法3差不多，只是元素属性不太一样。
``` bash
#div1{
            background:gold;
            width:500px;
            height:500px;
            text-align:center;
        }
        #div2{
            background:greenyellow;
            height:400px;
            width:400px;
            display:inline-block;
            vertical-align:middle;
        }
        #div1::after{
            content:'';
            height:50%;
            display:inline-block;
            background:green;
        }
<div id="div1">
    <div id="div2">
    </div>
</div>
```
### 5.把元素设为inline-block

方法：在父元素中设置line-height和center然后设置垂直对齐方式为居中就可以
适合：父元素高固定的，毕竟要设置行高。
``` bash
#div1{
        background:gold;
        width:500px;
        height:500px;
        line-height:500px;
        text-align:center;
    }
    #div2{
        width:400px;
        height:400px;
        vertical-align:middle;
        display:inline-block;
        background:greenyellow;
    }
<div id="div1">
    <div id="div2">
    </div>
</div>
```
你可以根据实际情况使用不同方法。