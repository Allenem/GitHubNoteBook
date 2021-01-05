# HTMLDOMConsole对象

Console 对象提供了访问浏览器调试模式的信息到控制台。

## CONTENT

| 方法 | 描述 |
|-|-|
| [assert()](#assert) | 如果断言为 false，则在信息到控制台输出错误信息。 |
| [clear()](#clear) | 清除控制台上的信息。 |
| [count()](#count) | 记录 count() 调用次数，一般用于计数。 |
| [error()](#error) | 输出错误信息到控制台 |
| [group()](#group) | 在控制台创建一个信息分组。 一个完整的信息分组以 console.group() 开始，console.groupEnd() 结束 |
| [groupCollapsed()](#group)) | 在控制台创建一个信息分组。 类似 console.group() ，但它默认是折叠的。 |
| [groupEnd()](#group)) | 设置当前信息分组结束 |
| [info()](#infolog) | 控制台输出一条信息 |
| [log()](#infolog) | 控制台输出一条信息 |
| [table()](#table) | 以表格形式显示数据 |
| [time()](#time) | 计时器，开始计时间，与 timeEnd() 联合使用，用于算出一个操作所花费的准确时间。 |
| [timeEnd()](#time) | 计时结束 |
| [trace()](#trace) | 显示当前执行的代码在堆栈中的调用路径。 |
| [warn()](#warn) | 输出警告信息，信息最前面加一个黄色三角，表示警告 |

* * * 

## assert

```js
// 如果第一个参数为 false，则再控制台输出信息：
console.assert(document.getElementById("demo"), "没有 ID 为 'demo' 的元素");
// Assertion failed: 没有 ID 为 'demo' 的元素


// 将对象写到控制台：
var myObj = { name : "菜鸟教程", site : "www.runoob.com" };
console.assert(document.getElementById("demo"), myObj);
// Assertion failed: Objectname: "菜鸟教程"site: "www.runoob.com"__proto__: Object


// 将数组写到控制台：
var myArr = ["Google", "Taobao", "Runoob", "Facebook" ];
console.assert(document.getElementById("demo"), myArr);
// Assertion failed: (4) ["Google", "Taobao", "Runoob", "Facebook"]
```

**定义和用法**

`console.assert()` 方法在第一个参数为 false 的情况下会在控制台输出信息。

**语法**

`console.assert(expression, message)`

**参数说明**

|参数	|类型	|描述|
|-|-|-|
|表达式	|布尔值表达式	|必需。布尔表达式，返回 true 或 false。|
|信息	|字符串或对象	|必需。 要写到控制台的信息或对象。|

* * * 

## clear

```js
// 清除控制台上所有信息：
console.clear();
```

**定义和用法**

`console.clear()` 方法用于清除控制台所有信息。

`console.clear()` 方法在执行成功后，会在控制台输出: "Console was cleared"。

**语法**

`console.clear()`

* * * 

## count

```js
console.count();
console.count();
console.count("Runoob");
console.count("Runoob");
console.count("Runoob2");
// default: 1
// default: 2
// Runoob: 1
// Runoob: 2
// Runoob2: 1
```

**定义和用法**

`console.count()` 在调用时会将数字（调用次数）写入到控制台。

`console.count()` 方法可以添加标签。

**语法**

`console.count(label)`

**参数说明**

|参数	|类型	|描述|
|-|-|-|
|label	|String	|可选，如果有指定，则会在控制台上输出标签，该标签显示在调用次数之前。|

* * * 

## error

```js
// 将错误信息输出到控制台：
console.error("这是一个错误。");
// 这是一个错误。


// 使用对象作为错误信息：
var myObj = { name : "菜鸟教程", site : "www.runoob.com" };
console.error(myObj);
/*
Object 
name: "菜鸟教程" 
site: "www.runoob.com" 
__proto__: Object
*/


// 数组作为错误信息：
var myArr = ["Google", "Taobao", "Runoob", "Facebook" ];
console.error(myArr);
/*
Array(4)
0: "Google"
1: "Taobao"
2: "Runoob"
3: "Facebook"
length: 4
__proto__: Array(0)
*/
```

**定义和用法**

`console.error()` 方法用于输出错误信息到控制台。

该方法对于开发过程进行测试很有帮助。

提示: 在测试的该方法的过程中，控制台需要可见 (浏览器按下 F12 打开控制台)。

**语法**

`console.error(message)`

**参数说明**

|参数	|类型	|描述|
|-|-|-|
|message	|String 或 Object	|必须，一个错误信息，可以是字符串或对象。|

* * * 

## group

```js
console.log("Runoob");
console.group();
console.log("Runoob，这个在分组里面。");
console.groupEnd();
console.log("跳出分组啦！");
console.group("RunoobLabel");
console.log("我在指定标签分组里。");
/*
Runoob
▼console.group
└ Runoob，这个在分组里面。
跳出分组啦！
▼RunoobLabel
└ 我在指定标签分组里。
*/
```

```js
console.log("Runoob");
console.groupCollapsed();
console.log("Runoob，这个在分组里面。");
console.groupEnd();
console.log("跳出分组啦！");
console.groupCollapsed("RunoobLabel");
console.log("我在指定标签分组里。");
/*
Runoob
▶console.groupCollapsed
跳出分组啦！
▶RunoobLabel
*/
```

**定义和用法**

`console.group()` 方法用于设置分组信息的起始位置，该位置之后的所有信息将写入分组。

`console.groupCollapsed()` 方法用于设置折叠的分组信息，在这个代码以下执行输出的信息都会再折叠的分组里。点击扩展按钮打开分组信息。

`console.groupEnd()` 方法用于结束分组标签。

**语法**

`console.group(label)`

`console.groupCollapsed(label)`

`console.groupEnd()`

**参数说明**

|参数	|类型	|描述|
|-|-|-|
|label	|String	|可选，分组标签。|

|参数	|类型	|描述|
|-|-|-|
|label	|String	|可选，分组标签。|

* * * 

## infolog

```js
console.info("Hello World!");   // Hello World!
console.log("Hello World!");    // Hello World!
```

**定义和用法**

`console.info()` , `console.log()` 方法用于在控制台输出信息。

该方法对于开发过程进行测试很有帮助。

&hearts; 提示: 在测试该方法的过程中，控制台需要可见 (浏览器按下 F12 打开控制台)。

**语法**

`console.info(message)`

***

## table

```js
// 在控制台输出一个表格
console.table(["Google", "Runoob", "Taobao"]);
/*
Array(3)
0: "Google"
1: "Runoob"
2: "Taobao"
length: 3
__proto__: Array(0)
*/


// 使用对象作为输出的信息：
console.table({ name : "菜鸟教程", site : "www.runoob.com" });
/*
Object
name: "菜鸟教程"
site: "www.runoob.com"
__proto__: Object
*/


// 使用对象数组：
var site1 = { name : "Runoob", site : "www.runoob.com" }
var site2 = { name : "Google", site : "www.google.com" }
var site3 = { name : "Taobao", site : "www.taobao.com" }
console.table([site1, site2, site3]);
/*
Array(3)
0: {name: "Runoob", site: "www.runoob.com"}
1: {name: "Google", site: "www.google.com"}
2: {name: "Taobao", site: "www.taobao.com"}
length: 3
__proto__: Array(0)
*/


// 指定表格表头标题名，参数只能是对应的键名：
var site1 = { name : "Runoob", site : "www.runoob.com" }
var site2 = { name : "Google", site : "www.google.com" }
var site3 = { name : "Taobao", site : "www.taobao.com" }
console.table([site1, site2, site3], ["site"]);
/*

Array(3)                                       Array(1)
0: {name: "Runoob", site: "www.runoob.com"}    0: "site"
1: {name: "Google", site: "www.google.com"}    length: 1
2: {name: "Taobao", site: "www.taobao.com"}    __proto__: Array(0)
length: 3
__proto__: Array(0)

*/
```

**定义和用法**

`console.table()` 方法用于在控制台输出表格信息。

第一个参数是必需的，且对象类型需要是对象或数组，对应的数据会填充到表格中。

&hearts; 提示: 在测试该方法的过程中，控制台需要可见 (浏览器按下 F12 打开控制台)。

**语法**

`console.table(tabledata, tablecolumns)`

**参数说明**

|参数	|类型	|描述|
|-|-|-|
|tabledata	|Array 或 Object	|必需，填充到表格中的数据。|
|tablecolumns	|Array	|可选，一个数组，表格标题栏的名称。|

***

## time

```js
// 测试哪个代码执行的更快

var i;
console.time("for 循环测试");
for (i = 0; i < 100000; i++) {
  // 代码部分
}
console.timeEnd("for 循环测试");
 
i = 0;
console.time("while 循环测试");
while (i < 1000000) {
  i++
}
console.timeEnd("while 循环测试");

/*
for 循环测试: 1.8349609375ms
while 循环测试: 3.84228515625ms
*/
```

**定义和用法**

`console.time()` 方法是作为计算器的起始方法。

该方法一般用于测试程序执行的时长。

`console.timeEnd()` 方法为计算器的结束方法，并将执行时长显示在控制台。

如果一个页面有多个地方需要使用到计算器，可以添加标签参数来设置。

&hearts; 提示: 在测试该方法的过程中，控制台需要可见 (浏览器按下 F12 打开控制台)。

**语法**

`console.time(label)`

`console.timeEnd(label)`

***

## trace

```html
<button onclick="myFunction()">跟踪轨迹</button>
<script>
function myFunction() {
  myOtherFunction();
}
function myOtherFunction() {
  console.trace();
  console.trace('控制');
}
</script>
<!-- 
console.trace
myOtherFunction @ VM10256:8
myFunction @ VM10256:4
onclick @ try.php?filename=tryjsref_console_trace:1

控制
myOtherFunction @ VM10256:9
myFunction @ VM10256:4
onclick @ try.php?filename=tryjsref_console_trace:1
 -->
```

**定义和用法**

`console.trace()` 方法用于显示当前执行的代码在堆栈中的调用路径。

&hearts; 提示: 在测试该方法的过程中，控制台需要可见 (浏览器按下 F12 打开控制台)。

**语法**

`console.trace(label)`

***

## warn

```js
// 在控制台上输出警告信息：
console.warn("！！！这是一个警告信息");  // ！！！这是一个警告信息
```

**定义和用法**

`console.warn()` 方法用于在控制台输出警告信息。

该方法对于开发过程进行测试很有帮助。

&hearts; 提示: 在测试该方法的过程中，控制台需要可见 (浏览器按下 F12 打开控制台)。

**语法**

`console.warn(message)`

**参数说明**

|参数	|类型	|描述|
|-|-|-|
|message	|String 或 Object	|必需，控制台上要显示的信息。|
