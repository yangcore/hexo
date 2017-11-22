---
title: Hello Hexo
tags: hexo
categories: 前端
---
第一篇博客，就写写我在配置Hexo的时候遇到的问题吧
# 跳过Hexo的渲染，直出静态页面，创建自定义网页
***
## 1.创建自定义页面
在Hexo/source目录下创建一个文件夹,并在此文件夹下创建一个新的html文件（文件夹名称任意，比如我创建的是yang这个文件夹，新建文件为index.html 部署完成后，访问http://yangcore.github.io/yang/index.html  即可看到效果，依此类推）。
## 2.跳过Hexo的渲染
如果你按照我上面的操作做了，你会发现，进入上面的链接不会报404或者找不到页面报错了，但是出来的页面并不是我们自己自定义的页面内容；
这个时候我们就要跳过Hexo的渲染，直出我们自己定义的页面。跳过Hexo渲染有两种方式：
### 1.直接在静态文件的头部添加跳过渲染指令
打开我们刚刚写的Hexo/source/yang/index.html文件，在文档最顶部添加如下代码

```javascript
---
layout:false
jj:false
---
```

```javascript
 var $body = document.body,
        $mnav = document.getElementById("mnav"), //获取导航三角图标
        $mainMenu = document.getElementById("main-menu"), //手机导航
        $process = document.getElementById('process'), //进度条
        $ajaxImgs = document.querySelectorAll('.img-ajax'), //图片懒加载
        $commentsCounter = document.getElementById('comments-count'),
        $gitcomment = document.getElementById("gitcomment"),
        $backToTop = document.getElementById("back-to-top"),
        timer = null;
```

| 链接 | 结果 | 原因 |
|:-----|:---:|----------:|
|文本内容| **`是`** |同协议同域名同端口|
|文本内容| **`是`** |同协议同域名同端口|
|文本内容| **`是`** |同协议同域名同端口|


    





