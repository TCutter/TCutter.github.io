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

## 九、性能
