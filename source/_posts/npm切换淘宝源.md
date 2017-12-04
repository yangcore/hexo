---
title: npm切换淘宝源
tags: npm
categories: 工具
date: 2017-12-04
---

# npm切换淘宝源
众所周知国内访问npm十分不稳定，所以才会有镜像源的存在了，在中国大家经常使用的就是阿里的npm淘宝源；这里就说一下如何切换；

## 第一种方法就是直接安装淘宝定制的cnpm命令行工具替代npm

打开 [cnpm官网](https://npm.taobao.org/)可以看一下使用说明

直接安装
``` js
npm install -g cnpm --registry=https://registry.npm.taobao.org
```
这种方式安装cnpm后就可以使用cnpm命令来代替npm命令执行相关操作了
## 直接使用npm切换镜像源
npm 内置配置是可以切换镜像源的

1.临时使用
```
npm --registry https://registry.npm.taobao.org install express
```
```
2.持久使用
npm config set registry https://registry.npm.taobao.org
// 配置后可通过下面方式来验证是否成功

npm config get registry
// 或npm info express
```
这样还是熟悉的npm命令，但是获取包的时候就是从淘宝的镜像获取的，所以速度要快很多。
