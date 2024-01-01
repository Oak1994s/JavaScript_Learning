# 一、基础部分
## 1、JavaScript的书写位置
### 1.1 行内式
#### 1.1.1 a标签：将JavaScript代码书写在href属性上
```html
<a href="javascript:alert('hello  world!');">点我一下</a>
```
#### 1.1.2 非a标签：将JavaScript代码书写在行为属性上
```html
<div onclick="alert('hello world!')">点我一下</div>
```
### 1.2 内嵌式
将JavaScript代码书写在script标签内
```javascript
<script>
	alert('hello world!')
</script>
```
### 1.3 外链式
将JavaScript代码书写在一个.js格式的外部文件内，然后将其引入html文件
```html
<!DOCTYPE html>
<html> 
	<head> 
		<meta charset="utf-8"> 
		<title>test</title> 
		<script src="./test1.js"></script>
	</head> 
	<body>
		<script src="./test2.js"></script>
	</body> 
</html>
```

## 2、JavaScript中的基本数据类型
### 2.1 Number类型
详见：[Number类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures#number_%E7%B1%BB%E5%9E%8B)
### 2.2 String类型
详见：[String类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures#number_%E7%B1%BB%E5%9E%8B)
### 2.3 Boolean类型
详见：[Boolean类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures#number_%E7%B1%BB%E5%9E%8B)
### 2.4 Undefined
详见：[Undefined](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures#number_%E7%B1%BB%E5%9E%8B)
### 2.5 Null
详见：[Null](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures#number_%E7%B1%BB%E5%9E%8B)
==著名历史遗留Bug==
```javascript
// JavaScript 诞生以来便如此
typeof null === "object";
```

> 在 JavaScript 最初的实现中，JavaScript 中的值是由一个表示类型的标签和实际数据值表示的。对象的类型标签是 0。由于 null 代表的是空指针（大多数平台下值为 0x00），因此，null 的类型标签是 0，typeof null 也因此返回 "object"。曾有一个 ECMAScript 的修复提案（通过选择性加入的方式），但被拒绝了。该提案会导致 typeof null === 'null'。
### 2.6 BigInt类型
详见：[BigInt类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures#bigint_%E7%B1%BB%E5%9E%8B)
### 2.7 Symbol类型
详见：[Symbol类型](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Data_structures#symbol_%E7%B1%BB%E5%9E%8B)
### 2.8 typeof判断数据类型
**`typeof`** 运算符返回一个字符串，表示操作数的类型。

|类型|返回结果|
|:---|:---|
|Undefined|"undefined"|
|Null|"object"（历史原因）|
|Boolean|"boolean"|
|Number|"number"|
|BigInt|"bigint"|
|String|"string"|
|Symbol|"symbol"|
|Function（在 ECMA-262 中实现 [[Call]]；classes也是函数)|"function"|
|其他任何对象|"object"|
### 2.9 数据类型转换(显式)
#### 2.9.1 其他类型转为Number类型
|转换前类型|转换后的情况|
|:---:|:---:|
|String|如果字符串是一个合法的数字，则直接转换为对应的数字；如果字符串是一个非法的数字，则转换为NaN；如果是一个空串或纯空格的字符串，则转换为0。|
|Boolean|true转换为1；false转换为0|
|Null|null转换为0|
|Undefined|undefined转换为NaN|

>**常用方法：**
>1. 调用Number()方法
>2. 调用parseInt()或parseFloat()方法

#### 2.9.2 其他类型转为String类型
|转换前类型|转换后的情况|
|:---:|:---:|
|Number|'等于字面值'|
|Boolean|'等于字面值'|
|Null|'null'|
|Undefined|'undefined'|
>**常用方法：**
>1. 调用String()方法
>2. 调用toString()方法
#### 2.9.3 其他类型转为Boolean类型
|转换前类型|转换后的情况|
|:---:|:---:|
|Number|除了0和NaN其余都是true|
|String|除了空字符串其余都是true|
|Null|false|
|Undefined|false|
|对象|true|
>**常用方法：**
>1. 调用Boolean()方法

>任意数据类型做两次非运算结果一定为Boolean类型
```javascript
var a = 'hello'
a = !!a  //true
```

## 3、运算符
### 3.1 算数运算符
`+ - * / %`
### 3.2 赋值运算符
`= += -= *= /= %=`
### 3.3 比较运算符
`> < >= <= == === != !==`
### 3.4 逻辑运算符
`&& || !`
### 3.5 自增自减运算符
`++ --`

## 4、流程控制语句
### 4.1 if语句
```javascript
if (判断条件) {执行语句}
// 条件为true则执行语句，否则不执行。
if (判断条件) {执行语句} else {执行语句}
// 条件为true则执行if的语句，否则执行else的语句。
if (判断条件) {执行语句} else if (判断条件) {执行语句}
// 哪个条件为true就执行哪个的if的语句，前面有条件为true，则后面不再判断。
if (判断条件) {执行语句} else if (判断条件) {执行语句} else {执行语句}
// 只有所有条件都不为true的时候，就会执行else后面的{}
```
### 4.2 switch语句
```javascript
switch (表达式的值) { // 表达式的值会和下列选项的值进行完全匹配，匹配到则执行对应语句
	case 值1:
		执行语句
		...
		break // 执行语句结束后，需要写break，不然会向下穿透
	case 值2:
		执行语句
		...
		break	
	case 值3:
		执行语句
		...
		break
	default: // 可以写一个default，会在所有选项都不匹配的时候执行
}
```
### 4.3 while语句
```javascript
定义初始变量n
while (判断条件) {
	重复执行的代码
	改变初始变量n的值
}
```

```javascript
定义初始变量n
do {
	重复执行的代码
	改变初始变量n的值
} while (判断条件)
```
### 4.4 for语句
```javascript
for (var i = 0; i < 10; i++) {
	console.log('Hello World !')
}
// 控制台输出10遍 Hello World !
```

```javascript
const obj = {
	name: '张三',
	age: 18
}
for (let key in obj) {
	console.log(key + '：' +obj.key)
}
// 控制台输出obj的所有属性名及属性值
```

```javascript
// for...in和for...of的区别
let arr = [3, 5, 7];
arr.foo = "hello";

for (let i in arr) {
  console.log(i); // 输出 "0", "1", "2", "foo"
}

for (let i of arr) {
  console.log(i); // 输出 "3", "5", "7"
}
```

```javascript
/* 
Array.prototype.forEach()：对数组的每个元素执行一次给定的函数。
forEach()中的回调函数会传入以下参数：
	element:数组中正在处理的当前元素。
	index:数组中正在处理的当前元素的索引。
	array:调用了forEach()的数组本身。
*/
const arr = ['a', 'b', 'c'];
arr.forEach((element) => console.log(element));
// 控制台输出'a' 'b' 'c'
```
## 5、函数（方法）
### 5.1 递归函数
求n的阶乘：
```javascript
function fn (n) {
	if (n === 1) return 1;
	return n*fn(n-1);
}
```
求斐波那契数列第n项的值：
```javascript
function fib(n) {
	if (n === 1 || n === 2) 
	return n - 1 
	return fib(n - 1) + fib(n - 2)
}
```

## 6、Object对象数据类型
### 6.1 创建
`var obj = {name:'jack',age:18}`
### 6.2 操作
#### 6.2.1 增
`obj.属性名 = 值` or `obj['属性名'] = 值`
#### 6.2.2 删
`delete obj.属性名` or `delete obj.['属性名']`
#### 6.2.3 改
`obj.属性名 = 值` or `obj['属性名'] = 值`
#### 6.2.4 查
`obj.属性名` or `obj['属性名']`

## 7、数组数据类型
### 7.1 创建
`var arr = [1, 2, 3]` 创建一个包含3个元素的数组
`var arr = new Array()` 创建一个空数组
`var arr = new Array(20)` 创建一个初始长度为20的空数组
### 7.2 sort() 数字排序
```javascript
var arr = [18, 2, 10, 9, 88, 66, 22];
	arr.sort(function (a, b) {
	return a - b; // 升序排序
	// return b - a; // 降序排序
});
```
### 7.3 常用方法
#### 7.3.1 push() 从数组末尾追加元素
**参数为新增的元素，返回新数组的长度，改变原数组**
```javascript
let arr=[1,2,3]  
var longth=arr.push(4,5);  
console.log(arr, longth);

输出结果：
arr [1,2,3,4,5]
5
```
#### 7.3.2 pop() 删除数组中最后一个元素
**参数为空，返回被删除的元素，改变原数组**
```javascript
let arr=[1,2,3,4,5]  
var delElement=arr.pop();  
console.log(arr, delElement);

输出结果：
arr [1,2,3,4]
5
```
#### 7.3.3 unshift() 从数组开头追加元素
**参数为新增的元素，返回新数组的长度，改变原数组**
```javascript
let arr=[1,2,3,4,5]  
var length=arr.unshift(0)
console.log(arr,length)

输出结果：
arr [0,1,2,3,4,5]
6
```
#### 7.3.4 shift() 删除数组中第一个元素
**参数为空，返回被删除的元素，改变原数组**
```javascript
let arr=[1,2,3,4,5]  
var delElement=arr.shift();  
console.log(arr, delElement);

输出结果：
arr [2,3,4,5]
1
```
#### 7.3.5 concat() 数组合并
**参数为元素或数组，返回新数组，不改变原数组**
```javascript
let arr=[1,2,3]  
let newArr=arr.concat([4,5],6,7);  
console.log(newArr,arr);

输出结果：
newArr [1,2,3,4,5,6,7]
arr [1,2,3]
```
#### 7.3.6 slice()截取数组
**slice(开始位置，结束位置)，第二个参数不写默认到尾部，只能从前往后截取，返回值为截取到的内容形成的新数组，不改变原数组**
```javascript
let arr=[1,2,3,4,5]
let copyArr=arr.slice() // slice()或者slice(0)都可以复制数组；  
let newArr=arr.slice(1,3) // 截取索引1到索引3(不包括3，前闭后开原则)的值;  
console.log(newArr,arr)

输出结果：
newArr [2,3]
arr [1,2,3,4,5]
```
#### 7.3.7 splice() 增删或替换数组元素
**splice()在任意位置增删元素，返回删除或被替换的值，如果没有被删除或替换则返回空数组，splice()会改变原数组**
```javascript
语法：数组.splice(开始索引,多少个,要插入的数据)
     开始索引默认为0
     多少个为0
     要插入的数据默认为空
作用：删除数组中的若干数据，并选择是否插入新数据

示例1：
let arr=[1,2,3,4,5] 
let num=arr.splice(2,3) //删除从索引值2开始的3个元素  
console.log(num;arr) // num=[3,4,5],arr=[1,2]

示例2：
let arr=[1,2,3,4,5] 
let num=arr.splice(2,1,6,7,8) 
//从索引值2开始替换掉指定位置的前1个元素，并且插入6,7,8
//如果第二个值为0，则不替换，直接插入6,7,8;  
console.log(num;arr) // 被替换的值num=[3]  arr=[1,2,6,7,8,4,5]
```
#### 7.3.8 join() 数组元素连接为字符串
```javascript
let arr=[1,2,3,4,5];
let newArr=arr.join() // 默认用逗号连接  
console.log(newArr) // newArr=1,2,3,4,5;
//如果连接符为空字符串，则会无缝连接  
console.log(arr.join("")) // 输出为12345；
```
#### 7.3.9 reverse() 数组逆序排列
**可以将数组进行倒序，返回值为新数组，改变原数组**
```javascript
let arr=[1,2,3,4,5] 
let newArr=arr. reverse()  
console.log(newArr,arr) // newArr=[5,4,3,2,1]; arr=[5,4,3,2,1];
```
#### 7.3.10 indexOf() 查找数据对应索引
```
语法：数组.indexOf(数据)
作用：查找数据对应索引
返回值：有该数据，返回第一次出现的位置索引；没有该数据，返回-1
```
#### 7.3.11 forEach() 遍历数组
```javascript
array.forEach(callbackFn(item, index, arr)) 
// forEach接收一个回调，并且没有返回值
// forEach()不会改变其调用的数组，但是，作为callbackFn的函数可以更改数组。
```
#### 7.3.12 map() 遍历数组返回新数组
**`map()` 方法创建一个新数组，这个新数组由原数组中的每个元素都调用一次提供的函数后的返回值组成。**
```javascript
arr1 = array.map(callbackFn(item, index, arr)) 
// map接收一个回调，并且返回一个新数组
// map()不会改变其调用的数组，但是，作为callbackFn的函数可以更改数组。
```
#### 7.3.13 filter() 过滤数组
**返回给定数组的一部分的浅拷贝，其中只包括通过提供的函数实现的测试的元素。如果没有元素通过测试，则返回一个空数组**
```javascript
function isBigEnough(value){
	return value>10
}
const filtered = [12,5,8,130,44].filter(isBigEnough);
// 过滤结果 [12,130,44]
```
#### 7.3.14 every() 数组任意性判断
**`every()`方法测试一个数组内的所有元素是否都能通过指定函数的测试。它返回一个布尔值**
```javascript
function isBigEnough(element, index, array) {
  return element >= 10;
}
[12, 5, 8, 130, 44].every(isBigEnough); // false
[12, 54, 18, 130, 44].every(isBigEnough); // true
```
#### 7.3.15 some() 数组存在性判断
**`some()`方法测试数组中是否至少有一个元素通过了由提供的函数实现的测试。如果在数组中找到一个元素使得提供的函数返回 true，则返回 true；否则返回 false。它不会修改数组**
```javascript
const fruits = ["apple", "banana", "mango", "guava"];
function checkAvailability(arr, val) {
  return arr.some((arrVal) => val === arrVal);
}
checkAvailability(fruits, "kela"); // false
checkAvailability(fruits, "banana"); // true
```
## 8 字符串常用方法
### 8.1 charAt()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/charAt)
### 8.2 toLowerCase()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toLowerCase)
### 8.3 toUpperCase()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/toUpperCase)
### 8.4 replace()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/replace)
### 8.5 trim()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/trim)
### 8.6 split()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/split)
### 8.7 substr()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substr)
### 8.8 substring()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/substring)
### 8.9 slice()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/String/slice)
## 9 数字常用方法
### 9.1 random()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/random)
### 9.2 round()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/round)
### 9.3 ceil()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/ceil)
### 9.4 floor()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/floor)
### 9.5 pow()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/pow)
### 9.6 sqrt()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/sqrt)
### 9.7 abs()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/abs)
### 9.8 max()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/max)
### 9.9 min()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/min)
### 9.10 PI
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Math/PI)
## 10 时间常用方法
### 10.1 获取
#### 10.1.1 getFullYear()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getFullYear)
#### 10.1.2 getMonth()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getMonth)
#### 10.1.3 getDate()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getDate)
#### 10.1.4 getHours()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getHours)
#### 10.1.5 getMinutes()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getMinutes)
#### 10.1.6 getSeconds()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getSeconds)
#### 10.1.7 getDay()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getDay)
#### 10.1.8 getTime()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/getTime)
### 10.2 设置
#### 10.2.1 setFullYear()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/setFullYear)
#### 10.2.2 setMonth()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/setMonth)
#### 10.2.3 setDate()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/setDate)
#### 10.2.4 setHours()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/setHours)
#### 10.2.5 setMinutes()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/setMinutes)
#### 10.2.6 setSeconds()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/setSeconds)
#### 10.2.7 setTime()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Date/setTime)
# 二、BOM操作
## 1、获取浏览器窗口尺寸
### 1.1 宽度：window.innerWidth
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/innerWidth)
### 1.2 高度：window.innerHeight
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/innerHeight)
## 2、浏览器弹出层
### 2.1 提示框：window.alert()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/alert)
### 2.2 询问框：window.confirm()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/confirm)
### 2.3 输入框：window.prompt()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/prompt)
## 3、开启和关闭标签页
### 3.1 开启：window.open()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/open)
### 3.2 关闭：window.close()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/close)
## 4、浏览器的历史操作
### 4.1 回退：window.history.back()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/History/back)
### 4.2 前进：window.history.forward()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/History/forward)
## 5、浏览器的常见事件
### 5.1 资源加载完毕：window.onload = function(){}
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/load_event)
### 5.2 页面尺寸改变：window.onresize = function(){}
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/resize_event)
### 5.3 滚动条位置改变：window.onscroll = function(){}
[详见]()
## 6、浏览器卷去的尺寸
### 6.1 高度：
#### 6.1.1 document.documentElement.scrollTop
[详见](https://blog.csdn.net/weixin_44283589/article/details/126172784)
#### 6.1.2 document.body.scrollTop
[详见](https://blog.csdn.net/weixin_44283589/article/details/126172784)
### 6.2 宽度：
#### 6.2.1 document.documentElement.scrollLeft
[详见]()
#### 6.2.2 document.body.scrollLeft
[详见]()
## 7、浏览器滚动到 window.scrollTo()
### 7.1 window.scrollTo(left,top)
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/scrollTo)
### 7.2 window.scrollTo({left:xx,top:yy,behavior:'smooth'})
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Window/scrollTo)
# 三、定时器
## 1、间隔定时器：setInterval(函数,时间)
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/setInterval)
## 2、 延时定时器：setTimeout(函数,时间)
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/setTimeout)
# 四、DOM操作
## 1、获取元素
### 1.1 document.getElementById()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/getElementById)
### 1.2 document.getElementByClassName()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/getElementsByClassName)
### 1.3 document.getElementByTagName()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/getElementsByTagName)
### 1.4 document.querySelector()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/querySelector)
### 1.5 document.getquerySelectorAll()
[详见](https://developer.mozilla.org/zh-CN/docs/Web/API/Document/querySelectorAll)
## 2、操作元素内容
### 2.1 文本内容：元素.innerText
### 2.2 超文本内容：元素.innerHTML

## 3、操作元素原生属性
### 3.1 获取：元素.属性名
### 3.2 设置：元素.属性名 = '属性值'
## 4、操作元素自定义属性
### 4.1 获取：元素.getAttribute()
### 4.2 设置：元素.setAttribute()
### 4.3 删除：元素.removeAttribute()
## 5、操作原生类名
### 5.1 获取：元素.className
### 5.2 设置：元素.className = '新类名'
## 6、操作元素行内样式
### 6.1 获取：元素.style.样式名
### 6.2 设置：元素.style.样式名 = '样式值'
## 7、获取元素非行内样式
### 7.1 Window.getComputedStyle(元素).样式名
## 8、节点操作
### 8.1 创建节点：
```javascript
document.createElement('标签名称')
```
### 8.2 插入节点：
```javascript
父节点.appendChild(子节点)
父节点.insertBefore(要插入的子节点，哪一个子节点的前面)
```
### 8.3 删除节点：
```javascript
父节点.removeChild(子节点)
节点.remove()
```
### 8.4 替换节点：
```javascript
父节点.replaceChild(换上节点，换下节点)
```
### 8.5 克隆节点：
```javascript
节点.cloneNode(是否克隆后代节点)
```
## 9、获取元素尺寸
### 9.1 语法：元素.offsetHeight、元素.offsetWidth
### 获取：元素内容+padding+border区域的尺寸
### 9.2 语法：元素.clientHeight、元素.clientWidth
### 获取：元素内容+padding区域的尺寸
## 10、事件
```javascript
事件源.on事件类型 = 事件处理函数(事件对象)

例如：button.onclick = fn (e) {
	     console.log(e)
	 }
```
### 10.1 事件传播与事件委托
[详见](https://blog.csdn.net/weixin_38984030/article/details/90402966)
# 五、面向对象
# 六、ES6新语法
# 七、网络功能
# 八、jQuery的使用
