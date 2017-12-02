---
title: chrome的跨域配置
tags: chrome
categories: 工具
date: 2017-12-02
---
# chrome的跨域配置,前端调试利器

由于浏览器安全性限制，Ajax是不能跨域访问的，而我们在日常开发工作中，经常会出现本地开发环境需要访问其他服务器上的API情况，尤其在用html5开发APP的过程中，前后台完全分离，使用Ajax进行数据交互。本文说明如何让Chrome浏览器支持开发时的Ajax跨域访问。

找到桌面chrome图标，点击右键属性

原属性里面的目标应该是
```
"C:\Program Files (x86)\Google\Chrome\Application\chrome.exe"
```

要想实现跨域请求就要在chrome启动时添加参数，所以修改成这样

```
"C:\Program Files (x86)\Google\Chrome\Application\chrome.exe" --enable-net-benchmarking --user-data-dir --test-type --disable-web-security

顺便推荐一下我使用的一个插件，就是当你在开发时快速切换host，切换开发环境的时候，可以点击一下，快速刷新浏览器的dns缓存，方便快速切换到当前环境；
插件地址 DNS Flusher :
https://chrome.google.com/webstore/detail/okehcbagcgnhifhcppklpmillcdnaclp

以上 --enable-net-benchmarking 参数 就是 DNS Flusher插件所需的参数

--user-data-dir 这个参数是说让chrome自定义用户数据地址，这里后面没有添加地址，所以用户数据还是源地址，若你想自定义chrome的用户数据地址 可以写成这样
--user-data-dir="C:\ChromeDebug" (这里自定义在C盘的ChromeDebug文件夹)

--disable-web-security 这个就是关键的参数，让浏览器禁用安全限制，这样就可以跨域请求了

--test-type 这个指测试模式，如果不加这一句也是可以的，我是加上了，因为不加这一句，chrome会有安全提示

```

好了，到这一步，你可以试一试跨域请求了；

这样，从快捷键启动Google Chrome即可启动指定参数，但是从外部程序(例如QQ、迅雷)打开Chrome时，Chrome是无法带参数启动的，(如果你自定义了用户数据地址，此时也无法调用指定的userdata插件、书签等)要使外部调用也能生效，还需要修改注册表。

1. 打开注册表，定位到以下项
```
          HKEY_CLASSES_ROOT\ChromeHTML\shell\open\command
          HKEY_CLASSES_ROOT\http\shell\open\command
          HKEY_CLASSES_ROOT\https\shell\open\command
          HKEY_CLASSES_ROOT\ftp\shell\open\command
```

2. 依次找到并修改以上4个位置，双击右侧窗口中的“(默认)”，随之弹出编辑字符串对话框，在“数值数据”框中将光标移到"Chrome路径"和-- "%1"之间，然后插入Chrome命令及参数
           --enable-net-benchmarking --user-data-dir --test-type --disable-web-security
    
3. 以上4个位置修改后关闭注册表编辑器，以后无论你如何启动Google Chrome，用户文件和临时文件都会到你所设置的目录加载插件和书签

快快试试吧！！！