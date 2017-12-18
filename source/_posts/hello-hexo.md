---
title: Hello Hexo
tags: hexo
categories: 前端
date: 2017-11-21
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
```yml
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
```html
// 引入 Hexo/source/yang/css 下的文件
<link rel="stylesheet" href="./css/index.css">
```
若想引入source内的静态文件
```
//这个路径引入的是 Hexo/themes/yourthemes/source/css 下的文件
<link rel="stylesheet" href="../css/style.css">
```

### 完成，执行 hexo g  访问看一下，这样你就可以在hexo内添加自定义页面了，比如可以自定义关于我们等静态页面了

# 代码块高亮

说说我自定义代码块高亮遇到的坑，本想着用hexo自带的 highlight 配置来着，但是当把 _config.yml 文件里的 highlight 配置打开，代码块始终没有颜色，可能是我不会用吧，就想着自己搞一下用 highlight.js实现代码块高亮；

很简单：在页面引入

```javascript
<%- js('//cdn.bootcss.com/highlight.js/9.12.0/highlight.min.js?rev=@@hash') %>
//我这里用的是vs主题，你可以自己找喜欢的主题
<%- css(['//cdn.bootcss.com/highlight.js/9.12.0/styles/vs.min.css']) %>
<script>
hljs.initHighlightingOnLoad(); //初始化代码高亮 
</script>
```
**注意：** 如果自己外部引入 highlight.js 来制作代码高亮的，必须关闭 hexo 自带的 highlight 的配置，_config.yml highlight.enable 改为 fasle 不然可能会造成代码块渲染错误

# 主题更换
本博客采用的是 [hexo-theme-snippet](https://github.com/shenliyang/hexo-theme-snippet "主题") 喜欢的可以去看一下，作者中国人，说明写的很详细，特别是里面说了一下 Travis CI 持续集成的相关配置；本博客就是使用Travis CI持续集成构建的



