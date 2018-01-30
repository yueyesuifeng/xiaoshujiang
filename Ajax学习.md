---
title: Ajax学习
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---
Ajax（Asynchronous JavaScript and XML）不是某种编程语言，允许浏览器与服务器通信而无须刷新当前页面的技术都叫做Ajax。
Ajax HTTP请求：
http是计算机通过网络进行通信的规则，一种无状态的协议，不保持长时间的连接。那么什么是协议？<font color="red">协议可以理解为一套规范</font>，当使用双方都遵守这套规范的时候，才能实现沟通，比如对于“嘿嘿”的理解不同，就会带来沟通障碍。网络协议具有很多规则，需要想干什么，再干什么。常见的协议，包括HTTP,HTTPS超文本传输协议，FTP文件传输协议，SMTP邮件传输协议。
HTTP协议的组成部分可以包括请求（Request）是从客户端发出的、响应（Request）是从服务器返回的。
监测工具
使用监测工具可以查看这些HTTP请求，以及编辑请求内容，重新发送。
* 浏览器：Chrom，Firefox开发工具
* 抓包工具: Fiddler、Charles
下图是HTTP请求报文的组成部分包括<font color="blue">请求行、请求头、请求主体。</font>请求行包括请求方法、请求URL及HTTP协议版本。

请求头设置的主要是一些信息，包含客户端与服务器，如下所示：
User-Agent：浏览器的具体类型　　如：User-Agent：Mozilla/5.0 (Windows NT 6.1; rv:17.0) Gecko/20100101 Firefox/17.0
Accept：浏览器支持哪些数据类型　　如：Accept: text/html,application/xhtml+xml,application/xml;q=0.9;
Accept-Charset：浏览器采用的是哪种编码　　如：Accept-Charset: ISO-8859-1
Accept-Encoding：浏览器支持解码的数据压缩格式　　如：Accept-Encoding: gzip, deflate
Accept-Language：浏览器的语言环境　　如：Accept-Language zh-cn,zh;q=0.8,en-us;q=0.5,en;q=0.3
Host：请求的主机名，允许多个域名同处一个IP地址，即虚拟主机。Host:www.baidu.com
Connection：表示是否需要持久连接。Keep-Alive/close，HTTP1.1默认是持久连接，它可以利用持久连接的优点，当页面包含多个元素时（例如Applet，图片），显著地减少下载所需要的时间。要实现这一点，Servlet需要在应答中发送一个Content-Length头，最简单的实现方法是：先把内容写入ByteArrayOutputStream，然后在正式写出内容之前计算它的大小。如：Connection: Keep-Alive
Content-Length：表示请求消息正文的长度。对于POST请求来说Content-Length必须出现。
Content-Type：WEB服务器告诉浏览器自己响应的对象的类型和字符集。例如：Content-Type: text/html; charset='gb2312'
Content-Encoding：WEB服务器表明自己使用了什么压缩方法（gzip，deflate）压缩响应中的对象。例如：Content-Encoding：gzip
Content-Language：WEB服务器告诉浏览器自己响应的对象的语言。
Cookie：最常用的请求头，浏览器每次都会将cookie发送到服务器上，允许服务器在客户端存储少量数据。
Referer：包含一个URL，用户从该URL代表的页面出发访问当前请求的页面。服务器能知道你是从哪个页面过来的。Referer: http://www.baidu.com/
请求体，这里是提交给服务器的数据，<font color="red">需要注意的是，如果是往服务器提交数据,需要在请求头中设置Content-Type: application/x-www-form-urlencoded(在ajax中需要手动设置)。</font>
一个完整的HTTP请求过程，通常由下面7个步骤：
1. 建立TCP连接
2. Web浏览器向Web服务器发送请求命令
3. Web浏览器发送请求头信息
4. Web服务器应答
5. Web服务器发送应答头信息
6. Web服务器向浏览器发送数据
7. Web服务器关闭TCP连接
一个HTTP请求一般由3部分组成：
1. HTTP请求的方法或动作，比如是GET还是POST请求
2. 正在请求的URL，总得知道请求的地址是什么吧
3.请求头，包含一些客户端环境信息，身份验证信息等
4. 请求体，也就是请求正文，请求正文中可以包含客户提交的查询字符串信息，表单信息等等。
GET:一般用于信息获取、使用URL传递参数、对所发送信息的数量也有限制，一般在2000个字符
POST：一般用于修改服务器上的资源。对所发送信息的数量无限制。
一个HTTP响应一般由三部分组成：
1. 一个数字和文字组成的状态码，用来显示请求是成功还是失败
2. 响应头，响应头也和请求头一样包含许多有用的信息，例如服务器类型，日期时间，内容类型和长度等。
3. 响应体，也就是响应正文
HTTP状态码由3位数字构成，其中首位数字定义了状态码的类型：
1XX：信息类，表示收到Web浏览器请求，正在进一步的处理中
2XX : 成功，表示用户请求被正确接受，理解和处理例如：200 OK
3XX : 重定向，表示请求没有成功，客户必须采取进一步的动作
4XX : 客户端错误，表示客户端提交的请求有错误，例如：404 NOT Found，意味着请求中所引用的文档不存在。
5XX : 服务器错误，表示服务器不能完成对请求的处理：如 500
XMLHTTPRequest五步使用法:
建立XMLHTTPRequest对象
注册回调函数（当服务器回应我们了,我们想要执行什么逻辑）
使用open方法设置和服务器端交互的基本信息（设置提交的网址,数据,post提交的一些额外内容）
设置发送的数据，开始和服务器端交互（发送数据）
更新界面（在注册的回调函数中,获取返回的数据,更新界面）
示例代码:GET：
<script type="text/javascript">
    // 创建XMLHttpRequest 对象
    var xml = new XMLHttpRequest();
    // 设置跟服务端交互的信息
    xml.open('get','01.ajax.php?name=fox');
    xml.send(null);    // get请求这里写null即可
    // 接收服务器反馈
    xhr.onreadystatechange = function () {
        // 这步为判断服务器是否正确响应
        if (xhr.readyState == 4 && xhr.status == 200) {
            // 打印响应内容
      alert(xml.responseText)
    }
};
</script>
示例代码:POST
<script type="text/javascript">
    // 异步对象
  var xhr = new XMLHttpRequest();
   // 设置属性
  xhr.open('post', '02.post.php' );
  // 如果想要使用post提交数据,必须添加
  xhr.setRequestHeader("Content-type","application/x-www-form-urlencoded");
  // 将数据通过send方法传递
  xhr.send('name=fox&age=18');
  // 发送并接受返回值
  xhr.onreadystatechange = function () {
  // 这步为判断服务器是否正确响应
  if (xhr.readyState == 4 && xhr.status == 200) {
   alert(xhr.responseText);
     } 
 };
</script>
   






















