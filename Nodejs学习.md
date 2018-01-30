---
title: Nodejs学习
tags: Node,前端,服务端
grammar_cjkRuby: true
---
#### 初步认识Nodejs
1. Google V8引擎  
2. C++语言编写  
3. 本质是JavaScript运行环境
4. 没有浏览器各种安全级的限制
5. 提供了很多系统级别的API：文件读取、进程的管理、网络通信等。
#### 为什么学习Node？
1. 它很火   npm（Node Package Manager）、github上关于Node的项目众多
2. 它很强   服务端、硬件控制、各种其他框架
建议学习网站：
www.nodejs.org、www.npmjs.org、github.com、stackoverflow.com
#### 浏览器控制台和系统控制台中的运行环境的不同？
这两个环境运行一般的js代码是没有问题的，但是在全局变量上还是有区别的。Chrome控制台中有全局变量变量window、document，但是系统控制台没有。系统控制台有全局变量process，但是Chrom没有。
#### 模块与包管理工具 npm
#### npm是用来做什么的？
1. 用户从npm服务器下载别人编写的第三方包到本地使用
2. 用户从npm服务器下载并安装别人编写的命令行程序到本地使用
3. 用户将自己编写的包或命令行程序上传到npm服务器供别人使用
查看版本号（windows）  npm -v
旧版更新到新版的命令（windows）npm install npm -g
安装模块命令    npm install <Module Name>   例：npm install express
本地安装    npm install express
全局安装    npm install express -g  可以在命令中直接使用
查看所有全局安装的模块 npm list -g
查看某个模块的版本号    例:npm list grunt
卸载模块    npm uninstall express
可以到/node_modules/目录下查看包是否还存在 npm ls
更新模块    npm update  express
搜索模块    npm search express
创建模块，package.json文件必不可少  使用npm init可以生成  
在npm资源库中注册用户   npm adduser
发布模块    npm publish
查看所有命令    npm help
使用npm help <command>可查看某条命令的详细帮助 例：npm help install
#### 推荐使用淘宝镜像   cnpm
使用淘宝定制的cnpm --registry=https://registry.npm.taobao.org
#### 回调函数
1. Node.js异步编程的直接体现就是回调
2. 异步编程依托于回调来实现，但不能说使用了回调后程序就异步化了。
3. 提高Node.js的性能，可以处理大量的并发请求

### Node.js API-0.10.35
#### 1. URL相关的API
1. url.parse    url字符串解析成url对象
2. url.format   解析的url对象格式化成url字符串
3. url.resolve  获取一个基本的URL和一个href URL，并将它们作为一个浏览器的锚标记来解析
#### 2. QueryString相关的API
1. querystring.stringify 序列化一个对象成查询字符串
2. querystring.parse    反序列一查询字符串成一个对象
3. querystring.escape   转义
4. querystring.unescape 反转义
#### 3. 通过http协议请求资源的过程
1. Chrome搜索自身的DNS缓存(chrome://net-internals 查看chrome浏览器缓存)
2. 搜索操作系统自身的DNS缓存（浏览器没有找到缓存或缓存已经失效）
3. 读取本地的HOST文件
4. 浏览器发起一个DNS的一个系统调用。
    (1) 宽带运营商服务器查看本身缓存
    (2) 运营商服务器发起一个迭代DNS解析的请求
运营商服务器把结果返回操作系统内核同时缓存起来，操作系统内核把结果返回浏览器，最终浏览器拿到了www.imooc.com对应的IP地址。
5. 浏览器获得域名对应的IP地址后，发起HTTP“三次握手”（三次握手的具体过程可以查资料详细了解）
6. TCP/IP连接建立起来后，浏览器就可以向服务器发送HTTP请求了，使用了比如说，用HTTP的GET方法请求一个根域里的一个域名，协议可以采用HTTP 1.0的一个协议。
7. 服务器端接受到这个请求，根据路径参数，经过后端的一些处理之后，把处理后的一个结果的数据返回给浏览器，如果是慕课网的页面就会把完整的HTML页面代码返回给浏览器。
8. 浏览器拿到了慕课网的完整的HTM页面代码，在解析和渲染这个页面的时候，里面的JS、CSS、图片静态资源。他们同样也是一个个HTTP请求都需要经过上面的主要的七个步骤。
9. 浏览器根据拿到的资源对页面进行渲染，最后把一个完整的页面呈现给了用户。
各种状态码的错误信息
