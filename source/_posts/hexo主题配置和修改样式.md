---
title: hexo的next主题配置和优化
date: 2017-03-14 08:15:23
tags: ['hexo','next','css']
categories: hexo博客搭建
---

## 继续叨叨叨
上一篇介绍了hexo的安装和部署（还没部署的小伙伴[点这里](http://www.ccblog.win/2017/04/11/hello-world))，这篇咱们接着上篇介绍怎么应用主题next和优化next。

## next主题
hexo的主题很多，但还是觉得next符合我的感觉，简洁大气，耐看。毕竟是博客，文章才是最主要的，花里胡哨的主题太宣兵夺主了。
### 下载应用next
hexo的主题都存放在themes文件夹下，在themes文件夹下右键Git bash Here，输入：
```bash
$ git clone https://github.com/iissnan/hexo-theme-next next
```
然后在_config.yml文件中找到theme字段改为next（hexo的所有主题应用都一样）。
然后输入：
``` bash
$ hexo clean
$ hexo s -debug
```
在本地预览调试看看是否应用成功。
### 选择自己喜欢的next外观
打开下载好的next文件夹下的_config.yml找到scheme字段，将你喜欢的外观前面的#删除。这样重新输入上面的命令，在本地预览查看。
### 设置语言
在next下的_config.yml中找到language字段，设置语言名字。在languages文件夹下的文件名就是所对应支持的语言：
| 名字| 对应语言|
| ------------- |:-------------:| 
| en      | 英语 |
| zh-Hans      | 简体中文      |
| zh-hk / zh-tw | 繁體中文      |
| ja      | 日本語|
| ko      | 韩语|
| ru| 俄语|
| fr-FR      | 法语      |
| pt | 葡萄牙语      |
| de     | 德语|
| id      | 印度尼西亚|
## 设置头像
在主题配置文件中找到avatar字段，写上你头像的http地址（云存储对应头像的地址）也可放在本地，不过推荐放云端存储。
### 添加标签页
在hext目录下右键git bash Here输入以下命令新建标签页，（注意：文章中没加入过标签的话页面为空）,标签页位于source文件夹下。
``` bash
$ hexo new page tags
```
在source \ _posts下的文章中在两个- - -之间添加
``` bash
type: "tags"
tags: ['hexo','next'](hexo和next就是标签，你可以写任何关于你文章名字的标签,加到后页面就可以打开看到标签了)
```
### 添加分类页面
和添加标签页一样
``` bash
$ hexo new page categories
```
在source \ _posts下的在文章中在两个- - -之间添加
``` bash
type: "categories"
categories: hexo博客
```
### 社交链接
在主题配置文件中找到social字段，输入对应的你的地址就ok了，不想显示的可以加#.
### 友情链接
在主题配置文件中找到links字段，输入一个（name: http地址）形式的地址就ok了。
``` bash
links:
  name: http地址
```
## 主题样式修改
我应用的外观是Pisces，我的方式简单粗暴，直接利用浏览器的开发者工具找到相应要修改的样式，然后直接在themes \ next \ source \ css \ _custom中的custom.styl文件中添加css来覆盖原有颜色样式，如果你懂css这些应该so easy。
``` bash
body { background:#2E0008;}//背景颜色
.site-meta{ background:#dd1031;}//左上角标题栏颜色
.site-title{ font-size:40px;}//左上角标题栏字体尺寸
.back-to-top{ background:#dd1031;opacity:1;}//右下角返回顶部样式
.content-wrap { background-image:url('http://ooa3lxrpg.bkt.clouddn.com/1232.png?imageView2/0/q/75');background-repeat:no-repeat;background-position:right top;}//右边区域背景
.site-author-image {//头像
border-radius: 50%;//头像变为圆形
-webkit-border-radius: 50%;
-o-border-radius: 50%;
-moz-border-radius: 50%;
border: 5px solid #dd1031;//头像边框尺寸 颜色
}
.
.
.
.
.
.
```
所以你可以修改你想修改的所有样式。今天基本就写到这里了，这几天突然发现自己的知识太少了，突然好想静下心来好好学习学习。希望我们大家都可以一直进步。
下一篇继续hexo的优化，给你的博客添加评论，搜索等。