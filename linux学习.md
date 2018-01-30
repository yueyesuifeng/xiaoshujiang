---
title: linux学习
tags: 新建,模板,小书匠
grammar_cjkRuby: true
---
博很重要，专更重要（专业做网站）
#### 为什么学习linux？
1. 开源、免费的操作系统，稳定性、安全性、处理多并发已经得到业界的认可
2. 工作需要  linux系统管理员、linux程序员（编程，需要c/c++/java/php/jsp）包括linux软件工程师和linux嵌入式开发
3. 本课程是基础，看完可以再看一些更加深入的书籍或课程
#### 如何学习linux？
学习linux的四个阶段
1. linux平台上的开发，包括vi、gcc、gdb、make、jdk、tomcat、mysql和linux基本操作
2. 加厚c语言功底《c专家编程》或是java语言
3. 学习unix环境高级编程
4. 系统开发还是软件开发
#### linux专家的秘诀
思考----实践----再思考----再实践
先建立一个整体框架，然后细节
高效而愉快地学习
用到什么再学什么
先konw how，再konw why
计算机是一门“做中学”的学科，不是会了再做，而是做了才会
适当地囫囵吞枣
学习linux系统是在琢磨别人怎么做，而不是我认为应该怎么做的过程
#### 推荐书籍
鸟哥的Linux私房菜、Linux编程从入门到精通、Linux内核完全剖析(有很好地基础再看)
### 第一天
#### linux的初步介绍
linux的特点
1. 免费的/开源。
2. 支持多线程/多用户的。
3. 安全性好。
4. 对内存和文件管理优越。
linux的缺点:
操作相对困难
linux最小只需4M-->嵌入式开发
vm（虚拟机，虚拟一个操作系统的软件） 虚拟一个linux操作系统
#### linux的第一次接触
#### vi编辑器的使用
约瑟夫问题、丢手帕问题
vi编辑器是linux下最有名的编辑器，是我们学习linux必须掌握的工具，在unix下可以使用vi进行程序的开发。
开发步骤:
1. vi Hello.java
2. 输入i  进入插入模式
3. 输入esc键 进入命令模式
4.  输入冒号(:)   [:wq表示退出保存  :q!退出不保存]
5.  编译 javac Hello.java
6.  运行 java Hello
如何在linux下开发c程序或c++程序？
1. vi Hello.cpp
2. 输入i  进入插入模式
3. 输入esc键 进入命令模式
4.  输入冒号(:)   [:wq表示退出保存  :q!退出不保存]
5.  编译 gcc Hello.cpp   或者gcc -o mytest Hello.cpp （-o mytest 编译后的文件名为mytest）
6.  运行 ./a.out
  #### linux用户管理
#### 常用命令
ubuntu 进入命令行界面  Ctrl+Alt+F2~F6
退出命令行界面，进入桌面版 Ctrl+Alt+F7
sudo passwd root 给root用户设密码
shutdown -h now 立刻关机
shutdown -r now 现在重新启动计算机
reboot 现在重新启动计算机
用户注销   在提示符下输入logout
显示当前在哪个路径下面  pwd
#### linux下的文件目录
采用层级式的树状目录结构
目录(同一级的) root home bin sbin mnt etc var boot
root 存放root用户的相关文件
home 存放普通用户的相关文件
bin  存放常用命令的目录
sbin 要具有一定权限才可以使用的命令
mnt  默认挂载软驱和光驱的目录
boot 存放引导相关的文件
etc  存放配置相关文件
var  存放经常变化的文件长度
user 存放用户使用的系统命令和应用程序等信息
#### linux的用户管理
添加用户xiaoming        useradd xiaoming
设密码    passwd xiaoming(不写的话，是给当前用户设密码)
userdel xiaoming(用户名)  删除用户
userdel -r xiaoming  删除用户以及用户主目录
#### linux的常用命令   指定运行级别
命令： init[012356]
运行级别
0：关机
1：单用户
2：多用户状态没有网络服务
3： 多用户状态有网络服务
4： 系统未使用保留给用户
5： 图形界面
6： 系统重启
常用运行级别是3和5，要修改默认的运行级别可改动文件/etc/inittab的id:5:initdefault:这一行中的数字
解决修改错误配置的方法，在进入引导界面的时候，请输入e，在选中第二行 输入e，进入修改界面，在最后输入一个1（单用户级别，1前面要加一个空格），再按b，进入单用户模式，然后再修改配置文件
ls 列出文件和目录
ls -a  显示隐藏文件
ls -l  显示长列表格式
ls -al 显示隐藏文件并长列格式
mkdir 建立目录
rmdir 删除空目录
touch 建立空文件
cp 复制命令
cp -r dir1 dir2 递归复制命令（复制子目录信息）
mv 移动文件和改文件名
rm 删除文件和目录
rm -rf * 删除所有内容（包括目录和文件） r递归  f 强制
ln 建立符号连接
ln -s 源目标
ln -s /etc/inittab inittab  init指向实际文件/etc/initab

在linux和unix系统中 | 就是管道命令

怎么理解？
把上一个命令的结果交给| 的后面的命令处理

more 显示文件内容，带分页
less 显示文件内容，带分页
grep 在文本中查询
| 管道命令
man命令相当于dos下的help
find 搜索文件及目录
重定向命令 ls -l > a.txt 列表的内容写入文件a.txt中(覆盖写)
ls -al >> aa.txt 列表的内容追加到文件aa.txt 的末尾


### 第二天
在linux中的每个用户必须属于一个组，不能独立于组外
在添加用户时，可以指定将该用户添加到哪个组，同样的用root的管理

jdk的安装步骤
要在官网下载压缩包，解压
配置环境变量
/etc/profile/    linux下的配置环境变量文件
配置文件中的注释，使用#号来注释掉的，改变环境变量后，要重新登录

安装eclipse
下载压缩包
tar -zxvf  eclipse.tar.gz  

































