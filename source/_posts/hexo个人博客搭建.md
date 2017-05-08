---
title: hexo个人博客搭建
date: 2017-03-12 08:15:23
tags: ['hexo']
categories: hexo博客搭建
---
### 叨的叨叨以叨叨，那是什么叨
该说啥呢。。。博客不是第一次写，但在自己搭建的博客上写文章的确是第一次。十分兴奋。看着自己辛苦搭建出来的博客，一点一点达到自己心目中的样子，这种感觉只有做过的人才可以体会到。如果你还在犹豫，那就别墨迹了。废话不多说。
搭建自己的博客，当时我查的时候好多人推荐用Wordpress，既然这么多人推荐，那我就不用，怎么滴。好吧被看穿了，其实是我太穷了，没钱租服务器。虽然好像也可以免费做出来，这个不太清楚，因为没太了解。就在我茶不思饭不想的时候，我发现了Hexo，这个真是太符合我了。利用github来部署静态博客，谁叫咱们就是干前端的呢。啥也不说了，立马开干。 
### 适合人群
哈哈你来看这篇文章说明你就适合
使用windows的你们（其他系统差不多）
### 安装必要程序
#### 安装GIT
到[ msysgit](https://git-for-windows.github.io/)下载好后， 下一步下一步执行安装即可。
什么，下载太慢了，我含泪告诉你人这一生不翻几次墙是干不了大事的。
#### 安装Node.js
到[Node.js](https://nodejs.org/en/)下载，左边稳定版，右边最新版，根据需要下载。推荐稳定版。安装的话，下一步还得下一步 非常简单。
#### 安装Hexo（我才是主人翁）
终于到我隆重出场了，鼠标右键任意位置，选择Git bash Here，输入npm 命令即可安装。
``` bash
$ npm install hexo -g
```
好吧，我叫特简单。文件一般会安装到C:\Users\Administrator\AppData\Roaming\npm\node_modules下可通过下边npm命令具体查看：
``` bash
$ npm root -g
```
安装好了就可以随便找个你喜欢的位置建个名叫hexo的文件夹，在这个文件夹里右键选择Git bash Here，分别输入hexo init和npm install（初始化文件和安装依赖包）：
``` bash
$ hexo init
```
``` bash
$ npm install
```
好了你应该已经看见效果了。接下来我们就要在网页中查看了，本地预览。分别输入g和s（生成静态网页和本地预览）：
``` bash
$ hexo g
```
``` bash
$ hexo s
```
上面的g和s其实generate和server的缩写，但是写缩写就够了，效果一样。如果出现
``` bash
$ hexo s
INFO  Start processing
INFO  Hexo is running at http://localhost:4000/. Press Ctrl+C to stop.
```
哈哈你成功了，下一步在网页中打开localhost:4000就可以看到网页了，兴奋兴奋呀。现在本地已经OK了。下来我们要把它发布到网上让世界人民来观摩。
### 注册github来部署博客
#### 注册[github](https://github.com/)
github应该很多人已经注册或正在注册的路上。我就不多说啥了。
#### 创建页面仓库
![Alt text](http://ooa3lxrpg.bkt.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20170417212627.png)
选择New repository
![Alt text](http://ooa3lxrpg.bkt.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20170417212833.png)
Repositoryname输入：你的账号名字.github.io，如（cspp01.github.io）。Description输入描述，最下面的选框Initialize this repository with a README可选可不选，建议选上。点击Create。好了，你在网上存放博客的地方也见好了。
#### SSH密钥
##### 生成SSH密钥
还是右键点击Git base Here输入
``` bash
ssh-keygen -t rsa -C "你的邮箱地址"
```
按回车，按回车，按回车，你得按3边，成功，到C:\Users\Administrator\.ssh下，可以看到两个文件，id_rsa是密钥 ，id_rsa.pub是公钥。
##### 建立连接
回到github选择setting->SSH and GPG keys->右上角New SSH key
![Alt text](http://ooa3lxrpg.bkt.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20170417214638.png)
![Alt text](http://ooa3lxrpg.bkt.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20170417214722.jpg)
![Alt text](http://ooa3lxrpg.bkt.clouddn.com/%E5%BE%AE%E4%BF%A1%E6%88%AA%E5%9B%BE_20170417215217.png)
title随便了，最好有意义点。打开刚才的id_rsa.pub，Ctrl+a->Ctrl+c，粘贴到key，Add SSH key，OK。
### hexo
#### _config.yml配置文件
这个文件在hexo根目录下，打开_config.yml配置文件，找到下面（在最下面）修改为：
``` bash
deploy:
  type: git
  repo: 仓库地址
  branch: master
```
注意repo是你刚才新建的仓库的地址,复制粘贴上去就好OK了。还有注意冒号后面的空格必须。
#### hexo部署
``` bash
$ hexo g
```
``` bash
$ hexo d
```
最后出现
``` bash
INFO  Deploy done: git
```
说明成功
如果在执行 hexo d 后,出现的错误
``` bash
error deployer not found:git
```
请再次输入
``` bash
npm install hexo-deployer-git --save 
```
然后再次执行
``` bash
$ hexo g
$ hexo d
```
应该就可以了，如果还失败。请重新安装hexo重新部署。我第一次就是不管怎么样操作都部署失败，后来重新安装了一下就好了。就是这么神奇。
最后在浏览器输入你刚才新建仓库的名字：你的用户名.github.io（如cspp01.github.io）就可以访问了。
是不是很酷。
### 写博客
你的博客文章都放在 source \ _posts 下，你如果要写新博客文章的话，可以手动在这个文件夹下创建.md文件。也可以通过命令创建：
``` bash
$ hexo new "你的文章名字"
```
然后再在你建好的.md文件里编辑文章。文章运用的是Markdowm（Markdown 是一种用来写作的轻量级「标记语言」）,还是很简单很好用的，其实你仿照hello world的那篇文章来写就可以。
#### 文章中加图片
加图片可以先把图片上传到云端，推荐[七牛](href="https://www.qiniu.com/")，然后在文章中加入了。
建好，编辑完，先在本地调试预览，在通过命令上传：
``` bash
$ hexo clean
$ hexo g
$ hexo s --debug
$ hexo d
```
好了，现在你新写的文章也上传上去了。上传上去立马刷新可能还不会作用到是因为会有一丝丝延迟，再刷新下就会好了。本地调试好后要上传记得每次都（每次上传最好先claer）：
``` bash
$ hexo clean
$ hexo g
$ hexo d
```
### hexo常用命令
``` bash
hexo 安装
$ hexo install hexo -g(安装hexo)
$ hexo init(初始化)
$ npm install(安装依赖包)

服务器
$ hexo s(开启本地服务，本地预览)
$ hexo s --debug(以调试模式启动，对文件的更改无需停止网站只需刷新即可看到效果)
$ hexo s -p 5000(更改端口)

$ hexo clean(清除缓存)
$ hexo d(上传部署)

本地文件
$ hexo g(重新生成本地文件)

编辑文章
$ hexo new "page" (新建文章)
```
这篇就到这里，下篇我们介绍怎么设置主题，和一些样式的修改自定义。