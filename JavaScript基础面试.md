---
title: JavaScript基础面试
tags: 前端基础
grammar_cjkRuby: true
---
### 第一章
先从几道面试题说起
* JS中使用typeof能得到哪些类型？考点：JS变量类型
* 何时使用`===`何时使用`==`？考点：强制类型转换
* window.onload和DOMContentLoaded的区别？考点：浏览器的渲染过程
* 用JS创建10个`<a>`标签，点击的时候弹出来对应的序号？考点:作用域
* 简述如何实现一个模块加载器，实现类似require.js的基本功能？考点：JS模块化
* 实现数组的随机排序？JS基础算法
#### 思考
* 拿到一个面试题，你第一时间<font class="he_warn">看到的是什么</font>?==考点==
* 又如何看待网上搜出来的<font class="he_warn">永远看不完</font>的题海？==不变应万变==
* 如何对待接下来遇到的面试题？==题目到知识再到题目==
### 第二章（JS基础上）
#### 题目
* JS中使用typeof能得到哪些类型？
* 何时使用`===`何时使用`==`？
* JS中有哪些内置函数？
* JS变量按照存储方式区分为哪些类型，并描述其特点？
* 如何理解JSON?
#### 知识点
* 值类型和引用类型
值类型的赋值，是赋值一个值，而引用类型的赋值，类似于指针
typeof能很好地区分值类型，不能区分引用类型
```javascript
typeof undefined//"undefined"
typeof 'abc'//"string"
typeof 123//"number"
typeof true//"boolean"
typeof {}//"object"
typeof []//"object"
typeof null//"object"
typeof console.log//"function"
```
* 强制类型转换
(1) 字符拼接
(2) `==`运算符
(3)if语句
(4)逻辑运算
* JS中有哪些内置函数——数据封装类对象
==Object==
==Array==
==Boolean==
==Date==
==Error==
==Function==
==Number==
==String==
==RegExp==
* JS变量按照存储方式区分为哪些类型，并描述其特点？
值类型、引用类型
特点：值类型的赋值，是赋值一个值，而引用类型的赋值，类似于指针
引用类型包括对象、数组、函数，引用类型可以无限制地扩展属性
* 如何理解JSON?
JSON是一种数据格式(只不过是一个JS对象)
```javascript
JSON.stringify({a:10,b:20})
JSON.parse('{"a":10,"b":20}')
```
#### 题目
* 如何判断一个变量是数组类型？
* 写一个原型链继承的例子？
* 描述new一个对象的过程？
* zepto(或其他框架)源码中如何使用原型链？
#### 知识点
* 构造函数-扩展
（1） var a={}其实是var a=new Object()的语法糖
（2） var a=[]其实是var a=new Array()的语法糖
（3） function Foo(){...}其实是var Foo=new Function(...)
（4） 使用instanceof判断一个函数是否是一个变量的构造函数，判断一个变量是否为"数组"：变量instanceof Array
* 5条原型规则，原型规则是学习原型链的基础
（1）所有的引用类型（数组、对象、函数），都具有对象特性，即可自由扩展属性，除了“null”以外
（2）所有的引用类型（数组、对象、函数），都有`_proto_`(隐式原型)属性值是一个普通的对象。
（3）所有的函数，都有一个prototype属性（显示原型），属性值也是一个普通 的对象。
（4）所有的引用类型（数组、对象、函数），`_proto_`属性值指向它的构造函数的`prototype`属性值。
（5）当试图得到一个对象的某个属性时，如果这个对象本身没有这个属性，name会去它的`_proto_`（即它的构造函数的prototype）中寻找。
#### 解答
* 如何判断一个变量是数组类型？
```javascript
var arr=[];
arr instanceof Array;//true
typeof arr;//object，typeof 是无法判断是否是数组的
```
* 写一个原型链继承的例子？
```javascript
function Animal(){
	this.eat=function(){
		console.log("eat");
	}
}
function Dog(){
	this.bark=function(){
		console.log("bark");
	}
}
//注意这种继承的实现方式
Dog.prototype=new Animal();
//哈士奇
var hashqi=new Dog()
```
* 描述new一个对象的过程？
1. 创建一个新对象
2. this指向这个新对象
3. 执行代码，即对this赋值
4. 返回this
* zepto(或其他框架)源码中如何使用原型链？
1. 阅读源码是高效提高技能的方式
2. 但不能“埋头苦读”有技巧在其中
3. 慕课网搜索“zepto设计和源码分析”（免费课程）带你读源码
### 第三章（JS基础中）
#### 题目
* 说一下对变量提升的理解？
* 说明this几种不同的场景？
* 创建10个`<a>`标签，点击的时候弹出来对应的序号？
* 如何理解作用域？
* 实际开发中闭包的应用？
#### 知识点
* 执行上下文
1. 范围：一段`<script>`或者一个函数
2. 全局：变量定义、函数声明 一段`<script>`
3. 函数：变量定义、函数声明、this、arguments   函数
==PS:注意”函数声明“和”函数表达式”的区别==
* this
1. this要在执行时才能确认值，定义时无法确认
    11. 作为构造函数执行
    12. 作为对象属性执行
    13. 作为普通函数执行
    14. call apply bind
```javascript
/*作为构造函数执行*/
function Foo(name){
	this.name=name;
}
var f=new Foo('zhangsan')
/*作为对象属性执行*/
var obj={
	name:'A',
	printName:function(){
		consle.log(this.name);
	}
}
obj.printName();
/*作为普通函数执行*/
function fn(){
	console.log(this);
}
fn();
//call apply bind,最常用的是call
function fn1(name,age){
	alert(name);
	alert(age);
	console.log(this);
}
// fn1.call({x:100},'zhangsan',20);//第一个参数{x:100}是this，'zhangsan'传给fn1函数的第一个参数name，20传给参数age
fn1.apply({x:100},['wanghe','18']);//apply没什么特别的就是后面传的是一个数组

var fn2=function (name,age){
	alert(name);
	alert(age);
	console.log(this);
}.bind({y:200});//bind使用在函数表达式上，this指的是{y:200}
fn2('wuyuzhi',14);
```
* 作用域
无块级作用域
* 作用域链
当前作用域没有定义的变量，即“自由变量”，去父作用中找自由变量
* 闭包
闭包的使用场景：
    1. 函数作为返回值
    2. 函数作为参数传递












