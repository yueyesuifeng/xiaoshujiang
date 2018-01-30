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
typrof true//"boolean"
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
```javascript
function F1(){
	var a=100
	return function(){
		console.log(a);//自由变量，去父作用域中寻找
	}
}
var f1=F1()
var a=200;
f1()
//闭包：很难用一两句话讲清楚什么是闭包
//1.函数作为返回值
//2. 函数作为参数传递
function F2(){
	var a=100
	return function(){
		console.log(a);//自由变量，去父作用域中寻找
	}
}
var f2=F2()
function F3(fn){
	var a=200;
	fn();
}
F3(f2)
```
#### 解答
* 说一下对变量提升的理解？
1. 变量定义
2. 函数声明（注意和函数表达式的区别）
* 说明this几种不同的场景？
1. 作为构造函数执行
2. 作为对象属性执行
3. 作为普通函数执行
4. call apply bind
* 创建10个`<a>`标签，点击的时候弹出来对应的序号？
```javascript
 var i;
    for(i=0;i<10;i++){
    	(function(i){
    		var a=document.createElement('a');
    		a.innerHTML=i+'<br>';
    		a.addEventListener('click',function(e){
    			e.preventDefault();
    			alert(i)
    		});
    		document.body.appendChild(a);
    	})(i)//这个i是指将参数i传递给里面的function，进行自执行
    }
```
* 如何理解作用域？
三个要点:（面试的时候一定要将这三个要点说出来）
（1）自由变量
（2）作用域链，即自由变量的查找
（3）闭包的两个场景
* 实际开发中闭包的应用？
看下面的例子：
```javascript
//闭包实际应用中主要用于封装变量，收敛权限
    function isFirstLoad(){
    	var _list=[];
    	return function(id){
    		if(_list.indexOf(id)>=0){
    			return false
    		}else{
    			_list.push(id)
    			return true
    		}
    	}
    }
    var firstLoad=isFirstLoad();
    console.log(firstLoad(10));
    console.log(firstLoad(10));
    console.log(firstLoad(20));
    console.log(firstLoad(20));
```
### 第四章（JS基础下）
#### 题目
1. 同步和异步的区别是什么？分别举一个同步和异步的例子？
2. 一个关于setTimeout的笔试题？
3. 前端使用异步的场景有哪些？
#### 知识点
1. 什么是异步（对比同步）
```javascript
console.log(100);
setTimeout(function(){console.log(200)},1000);
console.log(300);
```
以上程序（异步）的运行结果：
100
300
200
```javascript
console.log(100);
alert(200);//1秒钟之后点击确认
console.log(300);
```
以上程序（同步）的运行结果：
100
点击200的确认框
300
同步会阻塞代码的执行
2. 前端使用异步的场景
在可能发生等待的情况。
等待过程中不能像alert一样阻塞程序运行，为了使等待不被阻塞，所以有了异步，js是单线程的语言。
因此，所有"等待的情况"都需要异步
(1) 定时任务：setTimeout setInverval
(2) 网络请求：ajax请求，动态加载<img>加载
(3) 事件绑定
ajax请求代码示例:
```javascript
console.log('start');
$.get('./data1.json',function(data1){
    console.log(data1);
});
console.log('end')
```
`<img>`加载示例
```javascript
console.log('start')
var img=document.createElement('img');
img.onload=function(){
    console.log('loaded');
}
img.src='/xxx/img';
console.log('end');
```
事件绑定示例
```javascript
console.log('start');
document.getElementById('btn1').addEventListener('click',function(){
    console.log('clicked')
});
console.log('end')
```
3. 异步和单线程
单线程:事情一个一个来
```javascript
console.log(100);
setTimeout(function(){console.log(200)},1000);
console.log(300);
```
程序执行的过程如下:
* 执行第一行，打印100
* 执行setTimeout后，传入setTimeout的函数会被暂存起来，不会立即执行（单线程的特点，不能同时干两件事）
* 待所有程序执行完，处于空闲状态时，会立马看有没有暂存起来的要执行
* 发现暂存起来的setTimeout中的函数无需等待时间，就立即执行
#### 解答
1. 同步和异步的区别是什么？分别举一个同步和异步的例子？
同步会阻塞代码，而异步不会
alert是同步，setTimeout是异步
2. 一个关于setTimeout的笔试题？
```javascript
console.log(1)
setTimeout(function(){console.log(2)},0);//先暂存，封禁0毫秒
console.log(3);
setTimeout(function(){//先暂存，封禁1000毫秒
    console.log(4)
},1000);
console.log(5)
```
以上程序的运行结果是:
1
3
5
2
4
3. 前端使用异步的场景有哪些？
(1) 定时任务：setTimeout setInverval
(2) 网络请求：ajax请求，动态加载<img>加载
(3) 事件绑定
#### 其他知识
#### 题目
1. 获取2017-06-10格式的提起？
2. 获取随机数，要求是长度一致的字符串格式？
3. 写一个能遍历对象和数组的通用forEach函数？
#### 知识点
1. Date对象
```javascript
		Date.now();//获取当前时间的毫秒数
		var dt=new Date();
		console.log(dt.getTime());//获取毫秒数
		console.log(dt.getFullYear());//年
		console.log(dt.getMonth());//年
		console.log(dt.getDate());//月（0-11）
		console.log(dt.getHours());//日（0-31）
		console.log(dt.getMinutes());//小时（0-23）
		console.log(dt.getSeconds());//秒（0-59）
```
2. Math对象
获取随机数  Math.random()   用的多，清除缓存
3. 数组API
forEach 遍历所有元素
```javascript
        var arr=[1,2,3];
		arr.forEach(function(item,index){
			console.log(index,item);//遍历数组的所有元素
		})
```
every 判断所有元素是否都符合条件
```javascript
		var arr=[1,2,3]; 
		var result=arr.every(function(item,index){
			//用来判断所有的数组元素，都满足条件
			if(item<4){
				return true;
			}
		});
		console.log(result);
```
some 判断是否有至少一个元素符合条件
```javascript
        var arr=[1,2,3];
		var result=arr.some(function(item,index){
			//用来判断所有数组元素，只要有一个满足条件即可
			if(item<2){
				return true;
			}
		})
		console.log(result);
```
sort 排序
```javascript
var arr=[1,4,2,3,5];
		var arr2=arr.sort(function(a,b){
			//从小到大排序
			return a-b;
			// //从大到小排序
			// return b-a;
		})
		console.log(arr2);
```
map 对元素重新组装，生成新数组
```javascript
        var arr=[1,2,3,4];
		var arr2=arr.map(function(item,index){
			//将元素重新组装，并返回
			return '<b>'+item+'</b>b>'
		});
		console.log(arr2);
```
filter 过滤符合条件的元素
```javascript
        var arr=[1,2,3];
		var arr2=arr.filter(function(item,index){
			//通过某一条件过滤数组
			if(item>=2){
				return true;
			}
		})
		console.log(arr2);
```
for in
```javascript
var obj={
			x:100,
			y:200,
			z:300
		}
		var key;
		for(key in obj){
			//注意这里  hasOwnProperty
			if(obj.hasOwnProperty(key)){
				console.log(key,obj[key]);
			}
		}
```
#### 解答
1. 获取2017-06-10格式的日期？
```javascript
        function formatDate(dt){
			if(!dt){
				dt=new Date();
			}
			var year=dt.getFullYear();
			var month=dt.getMonth()+1;
			var date=dt.getDate();
			if(month<10){
				//强制类型转换
				month='0'+month;
			}
			if(date<10){
				//强制类型转换
				date='0'+date;
			}
			//强制类型转换
			return year+'-'+month+'-'+date;
		}
		var dt=new Date();
		var formatDate=formatDate(dt);
		console.log(formatDate);
```
2. 获取随机数，要求是长度一致的字符串格式？
```javascript
        var random=Math.random();
		var random=random+'0000000000';//后面加上10个零
		var random=random.slice(0,10);//包括小数点共10位
		console.log(random);
```
3. 写一个能遍历对象和数组的通用forEach函数？
```javascript
    function forEach(obj,fn){
			var key;
			if(obj instanceof Array){
				//准确判断是不是数组
				obj.forEach(function(item,index){
					fn(index,item)
				})
			}else{
				//不是数组就是对象
				for(key in obj){
					fn(key,obj[key])
				}
			}
		}
```
### 第五章（JS API上）
#### 题目
1. DOM是哪种基本的数据结构？树
2. DOM操作的常用API有哪些？
3. DOM节点的attr和property有何区别？
#### 知识点
1. DOM本质
DOM可以理解为：
浏览器把拿到的html代码，结构化一个浏览器能识别并且js可操作的一个模型而已！
2. DOM节点操作
(1) 获取DOM节点的操作 prototype Attribute
```javascript
var div1=document.getElementById('div1');//元素
var div=document.getElementsByTagName('div');//集合
var containerList=document.getElementsByClassName('.container')；//集合
var pList=document.querySelectorAll('p');//集合
```
3. DOM结构操作
4. BOM操作
问题1 如何检测浏览器的类型？
问题2 拆解url的个部分？
知识点 navigator screen location history
#### 解答
1. DOM是哪种基本的数据结构？
树
2. DOM操作的常用API有哪些？
(1) 获取DOM节点，以及节点的property和Attribute
(2) 获取父节点，获取子节点
(3) 新增节点，删除节点
3. DOM节点的attr和property有何区别？
(1) proterty只是对一个JS对象的属性的修改
(2) Attribute 是对html标签属性的修改

### 第六章
#### 题目
1. 编写一个通用的事件监听函数？
2. 描述事件冒泡流程
3. 对于一个无限下拉加载图片的页面，如何给每一个图片绑定事件？










