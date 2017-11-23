---
title: Hello Hexo
tags: hexo
categories: 前端
---
第一篇博客，就写写我在配置Hexo的时候遇到的问题吧
# 跳过Hexo的渲染，创建自定义网页
***
## 1.创建自定义页面
在Hexo/source目录下创建一个文件夹,about.html 部署完成后，访问http://yangcore.github.io/yang/about.html  即可看到效果，依此类推）。
## 2.跳过Hexo的渲染
如果你按照我上面的操作做了，你会发现，进入上面的链接不会报404或者找不到页面报错了，但是出来的页面并不是我们自己自定义的页面内容；
这个时候我们就要跳过Hexo的渲染，直出我们自己定义的页面。跳过Hexo渲染有两种方式：
### 1.直接在静态文件的头部添加跳过渲染指令
打开我们刚刚写的Hexo/source/yang/about.html文件，在文档最顶部添加如下代码

```javascript
---
layout: false
---
```
### 2.可在配置文件中添加要跳过的文件或文件夹
支持下面几种下发
```
skip_render: test.html //跳过指定文件

skip_render: test/* //正则跳过test下的文件

skip_render: test/** //跳过test下的所有文件，包括子文件夹

//跳过多个路径
skip_render:
 - test.html
 - test/*
```

以上两种方式引入静态资源的时候可在当前文件夹下创建静态文件，
直接相对路径引入，
```
// 引入 Hexo/source/yang/css 下的文件
<link rel="stylesheet" href="./css/index.css">
```
若想引入source内的静态文件
```
//这个路径引入的是 Hexo/themes/yourthemes/source/css 下的文件
<link rel="stylesheet" href="../css/style.css">
```

### 完成，执行 hexo g  访问看一下，这样你就可以在hexo内添加自定义页面了，比如可以自定义关于我们等静态页面了
    





