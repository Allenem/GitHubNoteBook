# JavaScript 全局属性和方法

JavaScript 可用于创建Javascript对象。

## CONTENT

### JavaScript 全局属性
| 属性 | 描述 |
|-|-|
| [Infinity](#1Infinity) | 代表正的无穷大的数值。 |
| [NaN](#2NaN) | 指示某个值是不是数字值。 |
| [undefined](#3undefined) | 指示未定义的值。 |

### JavaScript 全局函数

| 函数 | 描述 |
|-|-|
| [decodeURI()](#1encodeURI()&decodeURI()&encodeURIComponent()&decodeURIComponent()) | 解码某个编码的 URI。 |
| [decodeURIComponent()](#1encodeURI()&decodeURI()&encodeURIComponent()&decodeURIComponent()) | 解码一个编码的 URI 组件。 |
| [encodeURI()](#1encodeURI()&decodeURI()&encodeURIComponent()&decodeURIComponent()) | 把字符串编码为 URI。 |
| [encodeURIComponent()](#1encodeURI()&decodeURI()&encodeURIComponent()&decodeURIComponent()) | 把字符串编码为 URI 组件。 |
| [escape()](#2escape()&unescape()) | 对字符串进行编码。 |
| [unescape()](#2escape()&unescape()) | 对由 escape() 编码的字符串进行解码。 |
| [eval()](#3eval()) | 计算 JavaScript 字符串，并把它作为脚本代码来执行。 |
| [isFinite()](#4isFinite()) | 检查某个值是否为有穷大的数。 |
| [isNaN()](#5isNaN()) | 检查某个值是否是数字。 |
| [Number()](#6Number()) | 把对象的值转换为数字。 |
| [parseFloat()](#7parseFloat()) | 解析一个字符串并返回一个浮点数。 |
| [parseInt()](#8parseInt()) | 解析一个字符串并返回一个整数。 |
| [String()](#9String()) | 把对象的值转换为字符串。 |


## JavaScript 全局属性
### 1.Infinity
在Javascript中，超出 1.7976931348623157E+103088 的数值即为 Infinity ，小于 -1.7976931348623157E+103088 的数值为无穷小。
```js
var x=1.7976931348623157E+10308;
console.log(x);                         // Infinity
var y=-1.7976931348623157E+10308;
console.log(y);                         // -Infinity
```

### 2.NaN
NaN 即非数值（Not a Number），NaN 属性用于引用特殊的非数字值，该属性指定的并不是不合法的数字。

NaN 属性 与 Number.Nan 属性相同。

&hearts; 提示： 请使用 isNaN() 来判断一个值是否是数字。原因是 NaN 与所有值都不相等，包括它自己。


### 3.undefined
```js
var t1="";
var t2;

if (t1===undefined)
{
  alert("t1 is undefined");
}
if (t2===undefined)
{
  alert("t2 is undefined");
}

// t2 is undefined
```

undefined 属性用于存放 JavaScript 中未定义的值。

## JavaScript 全局函数

### 1.encodeURI()&decodeURI()&encodeURIComponent()&decodeURIComponent()

```js
var uri = "https://ke.qq.com/course/list/米斯特吴";
document.write(encodeURI(uri)+ "<br>");
document.write(decodeURI(uri)+ "<br>");
var uri_encode=encodeURIComponent(uri);
document.write(uri_encode+ "<br>");
document.write(decodeURIComponent(uri_encode));
/*
https://ke.qq.com/course/list/%E7%B1%B3%E6%96%AF%E7%89%B9%E5%90%B4
https://ke.qq.com/course/list/米斯特吴
https%3A%2F%2Fke.qq.com%2Fcourse%2Flist%2F%E7%B1%B3%E6%96%AF%E7%89%B9%E5%90%B4
https://ke.qq.com/course/list/米斯特吴
*/
```

### 2.escape()&unescape()
```js
var str="Need tips? Visit RUNOOB!";
var str_esc=escape(str);
document.write(str_esc + "<br>")
document.write(unescape(str_esc))

/*
Need%20tips%3F%20Visit%20RUNOOB%21
Need tips? Visit RUNOOB!
*/
```

`escape()` 函数可对字符串进行编码，这样就可以在所有的计算机上读取该字符串。

该方法不会对 ASCII 字母和数字进行编码，也不会对下面这些 ASCII 标点符号进行编码： * @ - _ + . / 。其他所有的字符都会被转义序列替换。

`unescape()` 方法对字符串进行解码。

**语法**

`escape(string)`

`unescape(string)`

|参数|描述|
|-|-|
|string|必需。要被转义或编码的字符串。|

**提示和注释**

&hearts; 注意： escape()函数不能用于编码 URIs(通用资源标识符（UniformResourceIdentifier,简称"URI"））. 可以使用函数 encodeURI() 取代。

### 3.eval()
```js
eval("x=10;y=20;document.write(x*y)");
document.write("<br>" + eval("2+2"));
document.write("<br>" + eval(x+17));

/*
200
4
27
*/
```

`eval()` 函数计算 JavaScript 字符串，并把它作为脚本代码来执行。

如果参数是一个表达式，eval() 函数将执行表达式。如果参数是Javascript语句，eval()将执行 Javascript 语句。

**语法**

`eval(string)`

### 4.isFinite()
```js
document.write(isFinite(123)+ "<br>");                     // true
document.write(isFinite(-1.23)+ "<br>");                   // true
document.write(isFinite(5-2)+ "<br>");                     // true
document.write(isFinite(0)+ "<br>");                       // true
document.write(isFinite("Hello")+ "<br>");                 // false
document.write(isFinite("2005/12/12")+ "<br>");            // false
```
isFinite() 函数用于检查其参数是否是无穷大。

&hearts; 提示： 如果 number 是 NaN（非数字），或者是正、负无穷大的数，则返回 false。

**语法**

`isFinite(value)`

### 5.isNaN()
```js
document.write(isFinite(123)+ "<br>");                     // false
document.write(isFinite(-1.23)+ "<br>");                   // false
document.write(isFinite(5-2)+ "<br>");                     // false
document.write(isFinite(0)+ "<br>");                       // false
document.write(isFinite("Hello")+ "<br>");                 // true
document.write(isFinite("2005/12/12")+ "<br>");            // true
```

isNaN() 函数用于检查其参数是否是非数字值。

如果参数值为 NaN 或字符串、对象、undefined等非数字值则返回 true, 否则返回 false。

**语法**

`isNaN(value)`

### 6.Number()

```js
var test1= new Boolean(true);
var test2= new Boolean(false);
var test3= new Date();
var test4= new String("999");
var test5= new String("999 888");

document.write(Number(test1)+ "<br>");     // 1
document.write(Number(test2)+ "<br>");     // 0
document.write(Number(test3)+ "<br>");     // 1565949760558
document.write(Number(test4)+ "<br>");     // 999
document.write(Number(test5)+ "<br>");     // NaN
```

`Number()` 函数把对象的值转换为数字。

如果对象的值无法转换为数字，那么 Number() 函数返回 NaN。

**语法**

`Number(object)`

|参数|描述|
|-|-|
|object|可选。一个 JavaScript 对象。如果没有提供参数，则返回0。|

&hearts; 注意：如果参数是 Date 对象，Number() 返回从 1970 年 1 月 1 日至今的毫秒数。

### 7.parseFloat()
```js
document.write(parseFloat("10") + "<br>");
document.write(parseFloat("10.33") + "<br>");
document.write(parseFloat("34 45 66") + "<br>");
document.write(parseFloat(" 60 ") + "<br>");
document.write(parseFloat("40 years") + "<br>");
document.write(parseFloat("He was 40") + "<br>");
/*
10
10.33
34
60
40
NaN
```

`parseFloat()` 函数可解析一个字符串，并返回一个浮点数。

该函数指定字符串中的首个字符是否是数字。如果是，则对字符串进行解析，直到到达数字的末端为止，然后以数字返回该数字，而不是作为字符串。

**语法**

`parseFloat(string)`

|参数|描述|
|-|-|
|string|必需。要被解析的字符串。|

&hearts; 注意： 字符串中只返回第一个数字。

&hearts; 注意： 开头和结尾的空格是允许的。

&hearts; 注意： 如果字符串的第一个字符不能被转换为数字，那么 parseFloat() 会返回 NaN。

### 8.parseInt()
```js
document.write(parseInt("10") + "<br>");
document.write(parseInt("10.33") + "<br>");
document.write(parseInt("34 45 66") + "<br>");
document.write(parseInt(" 60 ") + "<br>");
document.write(parseInt("40 years") + "<br>");
document.write(parseInt("He was 40") + "<br>");
 
document.write("<br>");
document.write(parseInt("11",2)+ "<br>");
document.write(parseInt("10",10)+ "<br>");
document.write(parseInt("010")+ "<br>");
document.write(parseInt("10",8)+ "<br>");
document.write(parseInt("0x10")+ "<br>");
document.write(parseInt("10",16)+ "<br>");

/*
10
10
34
60
40
NaN

3
10
10
8
16
16
*/
```

`parseInt()` 函数可解析一个字符串，并返回一个整数。

当参数 radix 的值为 0，或没有设置该参数时，parseInt() 会根据 string 来判断数字的基数。

当忽略参数 radix , JavaScript 默认数字的基数如下:

  - 如果 string 以 "0x" 开头，parseInt() 会把 string 的其余部分解析为十六进制的整数。
  - 如果 string 以 0 开头，那么 ECMAScript v3 允许 parseInt() 的一个实现把其后的字符解析为八进制或十六进制的数字。
  - 如果 string 以 1 ~ 9 的数字开头，parseInt() 将把它解析为十进制的整数。

**语法**

`parseInt(string, radix)`

|参数|描述|
|-|-|
|string|必需。要被解析的字符串。|
|radix|可选。表示要解析的数字的基数。该值介于 2 ~ 36 之间。|

&hearts; 注意： 只有字符串中的第一个数字会被返回。

&hearts; 注意： 开头和结尾的空格是允许的。

&hearts; 注意： 如果字符串的第一个字符不能被转换为数字，那么 parseInt() 会返回 NaN。

&hearts; 注意： 在字符串以"0"为开始时旧的浏览器默认使用八进制基数。ECMAScript 5，默认的是十进制的基数。

### 9.String()
```js
var test1 = new Boolean(1);
var test2 = new Boolean(0);
var test3 = new Boolean(true);
var test4 = new Boolean(false);
var test5 = new Date();
var test6 = new String("999 888");
var test7 = 12345;

document.write(String(test1)+ "<br>");
document.write(String(test2)+ "<br>");
document.write(String(test3)+ "<br>");
document.write(String(test4)+ "<br>");
document.write(String(test5)+ "<br>");
document.write(String(test6)+ "<br>");
document.write(String(test7)+ "<br>");

/*
true
false
true
false
Fri Aug 16 2019 18:15:54 GMT+0800 (中国标准时间)
999 888
12345
*/
```

`String()` 函数把对象的值转换为字符串。

**语法**

`String(object)`

|参数|描述|
|-|-|
|object|必需。JavaScript 对象。|

&hearts; 注意： String() 函数返回与字符串对象的toString()方法值一样。