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
### 第二章
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
```
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
```
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












