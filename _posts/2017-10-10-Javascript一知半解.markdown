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
1. number
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

2. boolean

| 数据类型        | true           | true  |
| ------------- |:-------------:| -----:|
| String      | 任何非空字符串 |''和'   ' |
| Number | 任何非零数字值（包括Infinity和-Infinity）| 0和NaN
| Undefined | \ | undefined

3. string
- 字符字面量

|字面量 | 含义 |
| ------------- |:-------------:|
| \r | 回车：回到当前行的最左边 |
| \n | 换行 |
|  \\' | 单引号 |
| \\" | 双引号|

4. null
5. undefined

#### 2.1.2 操作符

1. typeof操作符

```
var a = 'undefined';
var b = null;
 
 console.log(typeof(a)); //'undefined'
 console.log(typeof(b)); //'object'
 console.log(typeof NaN); //'number'
```

2. 位操作符

基础：在ECMAScript中的所有数据是以64位格式存储，位操作符先将64位的值转化成32位的整数，然后执行操作，最后再将结果转换回64位。

对于有符号的整数，32位中的第32位（称为’符号位‘）表示树数值的符号：0位正，1为负。正数以纯二进制格式存储，前31位中的每一位都表示2次幂（第一位叫做位0表示2ˇ0，以此类推）；

负数使用二进制补码，计算一个负数的二进制码需要一下步骤：
    
- 求这个数绝对值的二进制码；
- 求二进制的反码；
- 得到的二进制反码加 1。


&#8194; a. 按位非（NOT）

用 ～ 表示，结果就是返回数值的反码。其本质是将操作数的负值减 1

&#8194; b. 按位与（AND）

用 & 表示

|第一个数值 | 第二个数值 | 结果 |
| ------------- |:-------------:| -----:|
| 1 | 1 | 1 |
| 1 |0| 0|
|0 | 1 | 0|
|0 | 0 | 0|

&#8194; c. 按位或（OR）

用 | 表示

|第一个数值 | 第二个数值 | 结果 |
| ------------- |:-------------:| -----:|
|1 | 1 | 1|
|1 |0| 1|
|0 | 1 | 1|
|0 | 0 | 0|

&#8194; d. 按位异或（XOR）

用 ^ 表示：两个数值在对应位上只有一个1 时才返回

|第一个数值 | 第二个数值 | 结果|
| ------------- |:-------------:| -----:|
|1 | 1 | 0|
|1 |0| 1|
|0 | 1 | 1|
|0 | 0 | 0|

&#8194; e. 左移和右移

左移用 << 表示，（除符号位外）将操作数的所有位向左移动指定的位数；

右移用 >> 表示，（除符号位外）将操作数的所有位向右移动指定的位数

&#8194; f. 无符号右移(没有无符号左移)

无符号右移用 >>> 表示，将操作数的所有位向右移动指定的位数；

#### 2.1.3 变量类型和内存

1. 基本类型和引用类型变量的区别
- 基本类型不能添加属性，而🎵类型可以；
- 复制变量值：

```
// 基本类型变量复制的是副本
var a = 5;
var b = a;
b = 2;
console.log(a); //5

/* 引用类型变量复制时，同样会将存储在变量对象中的值复制一份到新变量分配的空间中。不同的是，这个副本实际上是一个指向存储在堆中的某个对象的指针。复制操作结束后，两个变量实际上将引用同一个对象
 */
 var a = {
	 name : 'gx'
 };
 var b = a;
 b.name = 'cm';
 console.log(a.name); //cm
```

#### 2.1.4  引用类型
1. array
2. function
3. Object

属性和方法
- constructor : 保存着用于创建当前对象的函数
- hasOwnProperty(propertyName) : 检查给定的属性在当前对象实例中（而不是在实例的原型中）
- isPropertyOf(object):用于检查传入的对象是否是另一个对象的原型
- propertyIsEnumerable(propertyName) : 检查给定的方法能否用for...in枚举
- toString() ： 返回对象的字符串表示
- valueOf() ：返回对象的字符串、数值或布尔值表示。通常与toString()返回的结果相同

```
function a(){
	this.name = 'TCutter'
};

var b = new a();
console.log(b.constructor === a); //true
```

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

10. window.open


	chrome60开始取消了对顶部框架导航（top-frame navigation）的支持，直接使用window.open会报错：
	```Not allowed to navigate top frame to data URL ```

	[需要将数据放到iframe中](https://stackoverflow.com/questions/45493234/jspdf-not-allowed-to-navigate-top-frame-to-data-url)

	```
	 var canvasConvertResult = canvas.toDataURL('image/png');
	 var iframe = "<iframe width='100%' height='100%' src='" + canvasConvertResult + "'></iframe>"
    var x = window.open();
    x.document.open();
    x.document.write(iframe);
    x.document.close();

	```
11. event对象

a. 移动端event

[touches,targetTouches和changedTouches的区别](https://www.cnblogs.com/mengff/p/6005516.html)

- touches: 当前屏幕上所有触摸点的列表

- targetTouches: 当前对象上所有触摸点列表

- changedTouches: 涉及当前(引发)事件的触摸点的列表

b. event坐标

[关于几个属性坐标的理解](https://www.cnblogs.com/frontendnotes/articles/6536006.html)

- event.clientX、event.clientY：鼠标相对于浏览器窗口可视区域的X，Y坐标（窗口坐标），可视区域不包括工具栏和滚动条;

- event.pageX、event.pageY：类似于event.clientX、event.clientY，但它们使用的是文档坐标而非窗口坐标;

- event.offsetX、event.offsetY:鼠标相对于事件源元素（触发事件的对象srcElement）的X,Y坐标;

- event.screenX、event.screenY:鼠标相对于用户显示器屏幕左上角的X,Y坐标

- event.x、event.y:设置或获取鼠标指针位置相对于父文档的 x、y坐标

![event坐标图鉴](../images/js/event_position.PNG)

12. [call、apply和bind](https://www.cnblogs.com/pssp/p/5215621.html);

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
原因：webkit是多进程架构，主要包括Brower进层（主进程）、Renderer进程、NPAPI进程和GPU进程等。打开一个网页可能会调用上述不同的进程

## 十、性能
