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
## 二、基础知识
### 2.1  Javascript类型
#### 2.1.1  基础类型
1. number
2. boolean
3. string
4. null
5. undefined

#### 2.1.2  引用类型
1. array
2. function
3. Object

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

## 八、编程规范
1. eval()函数只用来解析序列化串

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
