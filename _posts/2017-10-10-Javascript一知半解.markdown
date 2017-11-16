---
author: TCutter
comments: true
date: 2017-10-10
layout: post
categories:
- Tech
tags:
- javascript
- Html5
---

## 一、简介
JavScrip由三个部分组成
- ECMAScript : 提供核心语言功能
- DOM ：提供访问和操作网页内容的方法和接口
- BOM ：提供与浏览器交互的方法和接口

## 二、基础知识
### 2.1  Javascript类型
#### 2.1.1  基础类型
1. typeof操作符
```
var a = 'undefined';
var b = null;
 
 console.log(typeof(a)); //'undefined'
 console.log(typeof(b)); //'object'
 console.log(typeof NaN); //'number'
```

2. number
	- parseInt : 
	```
	parseInt(0.7);	//0
	parseInt(-1.7); //-1
	parseInt(1.7); //1
	parseInt('blue123'); //123
	parseInt('blue'); //NaN
	```
	- 数值范围 : 
	超过数值范围的数被自动保存为Infinity值，如果是正数则为Infinity；负数则为-Infinity。
	方法isFinity(); //是否是有穷数
	- NaN : 
	任何数除以0都会返回NaN
	```
	/*isNaN()会尝试将参数转换成数值，若不能转换成数值，则返回true*/
	console.log(NaN == NaN); //false;
	console.log(isNaN(NaN)); //true;
	console.log(isNaN('blue123')); //true;
	```

3. boolean

数据类型 | true | false
- | :-: | -: 
String | 任何非空字符串 | ''和'   '
Number | 任何非零数字值（包括Infinity和-Infinity）| 0和NaN
Object | 任何对象 | null
Undefined | \ | undefined

4. string
- 字符字面量

子面量 | 含义
- | :-: | -: 
\r | 回车：回到当前行的最左边
\n | 换行
\' | 单引号
\" | 双引号
5. null
6. undefined

#### 2.1.2  引用类型
1. array
2. function
3. Object

属性和方法
- Constructor : 保存着用于创建当前对象的函数

- hasOwnProperty(propertyName) : 检查给定的属性在当前对象实例中（而不是在实例的原型中）

- isPropertyOf(object):用于检查传入的对象是否是另一个对象的原型

### 2.2  原型和原型链

## 三、Ajax
## 四、Canvas
## 五、客户端存储
## 六、HTML5 API
## 七、常用开发技巧
1. 获取数组中的随机项

```
var temp = array[Math.floor(Math.random() * array.length)];
```

2. 类数组对象调用数组方法

```
/*类数组对象:如函数的参数arguments,DOM的NodeList和HTMLCollection*/
Array.prototype.forEach.call(arguments,function(value){}); //遍历
var args = Array.prototype.slice.call(arguments); //类数组对象转换成数组
```

3. 获取数组中的最大最小值

```
var maxNum=Math.max.apply(Math,array);
var minNum=Math.min.apply(Math,array);
```

4. 简化if语句

```
if(condition){
	fn();
}
改成
condition && fn();
```

5. 数组合并

```
//对于小数组：
var arr1 = [1,2,3];
var arr2 = [4,5,6];
var arr3 =arr1.concat(arr2);	// [1,2,3,4,5,6]

//对于大型数组，使用concat合并效率低下
Array.prototype.push.apply(arr1,arr2);
console.log(arr1);  //[1,2,3,4,5,6]
console.log(arr2); //[4,5,6]
```
6. 避免使用new操作符

```
var a = new Object();
var b = new  Array();
var c = new  String("123");

//改成
var a = {};
var b = [];
var c = "123";
```

7. 遍历对象属性

```
var a={
	name:"gx",
	age:24
};
Object.prototype.height = 180;
//用for...in遍历需要用hasOwnProperty判断是否是原型属性

Object.keys(a); //["name", "age"]
```

8. JS 静态成员变量（static member variable）

定义：只有一份，但是被类的所有实例共享的变量。非静态方法需要通过类的实例访问，而静态方法可以直接通过类名访问。
通过prototype添加的属性和方法不是静态的

````
function People(){
	var sex = "man"; //private variable
	this.age = "24"; //public variable

	this.getAge = function(){ //public method
		return this.age;
	}
}

//The method will be available to all instances but only load in one memory
People.prototype.getHeight = function(){
	alert("getHeight");
}

//Static variable shared by all instances
People.language = "Chineses";
````
[如何在Javascript中创建静态变量](https://stackoverflow.com/questions/1535631/static-variables-in-javascript)

9. [继承](https://johnresig.com/blog/simple-javascript-inheritance/)

## 八、编程规范
1. eval()函数只用来解8.8.析序列化串
```
var jsonData = eval('(' + data + ')');
```

原因：eval()会让程序执行的比较混乱


2. {}和[]
使用{}代替new Object()，使用[]代替new Array()


3. 单引号（'）
   尽量使用单引号（'），只在JSON文件中使用双引号。

## 九、问题整理
1. chrome 60兼容问题：

chrome 60硬件加速功能有缺陷，偶现canvas画图失败。

问题定位：CPU确认无误后，定位是GPU的问题，硬件加速功能与GPU处理有关


2. 远程调试
针对chrome60及以上在全屏状态下F12无效的问题


3. 打开一个网页，查看任务管理器发现有多个chrome进程
原因：webkit是多进程架构，主要包括Brower进层（主进程）、Renderer进程、NPAPI进程和GPU进程等。打开一个网页可能会钓调用上述不同的进程

## 十、性能
