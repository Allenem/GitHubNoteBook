# Javascript Number

## Number 创建方式 new Number()。

**语法**

`var num = new Number(value);`

&hearts; 注意： 如果一个参数值不能转换为一个数字将返回 NaN (非数字值)。

## CONTENT

### [Number 对象属性](#Number对象属性)
|属性|描述|
|-|-|
|constructor|返回对创建此对象的 Number 函数的引用。|
|MAX_VALUE|可表示的最大的数。|
|MIN_VALUE|可表示的最小的数。|
|NEGATIVE_INFINITY|负无穷大，溢出时返回该值。|
|POSITIVE_INFINITY|正无穷大，溢出时返回该值。|
|NaN|非数字值。|
|prototype|允许您可以向对象添加属性和方法。|
|**ES6新属性**|
|EPSILON|表示 1 和比最接近 1 且大于 1 的最小 Number 之间的差别|
|MIN_SAFE_INTEGER|表示在 JavaScript中最小的安全的 integer 型数字 (-(2^53 - 1))。|
|MAX_SAFE_INTEGER|表示在 JavaScript 中最大的安全整数（2^53 - 1）。|

### [Number 对象方法](#Number对象方法)
|方法|描述|
|-|-|
|isFinite|检测指定参数是否为无穷大。|
|toExponential(x)|把对象的值转换为指数计数法。|
|toFixed(x)|把数字转换为字符串，结果的小数点后有指定位数的数字。|
|toPrecision(x)|把数字格式化为指定的长度。|
|toString()|把数字转换为字符串，使用指定的基数。|
|valueOf()|返回一个 Number 对象的基本数字值。|
|**ES6新方法**|
|isInteger()|用来判断给定的参数是否为整数。|
|isSafeInteger()|判断传入的参数值是否是一个"安全整数"。安全整数范围为 -(2^53 - 1)到 2^53 - 1 之间的整数，包含 -(2^53 - 1)和 2^53 - 1。|

## Number对象属性

```js
console.log(
  Number.constructor+'\n'+
  Number.MAX_VALUE+'\n'+
  Number.MIN_VALUE+'\n'+
  Number.NEGATIVE_INFINITY+'\n'+
  Number.POSITIVE_INFINITY+'\n'+
  Number.NaN+'\n'+
  Number.prototype+'\n'+
  Number.EPSILON+'\n'+
  Number.MIN_SAFE_INTEGER+'\n'+
  Number.MAX_SAFE_INTEGER
);

/*
function Function() { [native code] }
1.7976931348623157e+308
5e-324
-Infinity
Infinity
NaN
0
2.220446049250313e-16
-9007199254740991
9007199254740991
*/
```

## Number对象方法

### 1.isFinite
```js
Number.isFinite(123) //true
Number.isFinite(-1.23) //true
Number.isFinite(5-2) //true
Number.isFinite(0) //true
Number.isFinite('123') //false
Number.isFinite('Hello') //false
Number.isFinite('2005/12/12') //false
Number.isFinite(Infinity) //false
Number.isFinite(-Infinity) //false
Number.isFinite(0 / 0) //false
```

`isFinite()` 函数用于检测指定参数是否为无穷大。

&hearts; 提示： 如果 number 是 NaN（非数字），或者是正、负无穷大的数，则返回 false。

Number.isFinite() 与全局的 isFinite() 函数不同，全局的 isFinite() 会先把检测值转换为 Number ，然后再检测。

Number.isFinite() 不会将检测值转换为 Number对象，如果检测值不是 Number 类型，则返回 false。

### 2.toExponential(x) & toFixed(x) & toPrecision(x) & toString() & valueOf()
```js
var num = 5.56789;
var n=num.toExponential()
// n = 5.56789e+0  把对象的值转换为指数计数法。

var num = 5.56789;
var n=num.toFixed(2);
// n = 5.57  把数字转换为字符串，结果的小数点后有指定位数的数字。

var num = new Number(13.3714);
var n=num.toPrecision(2);
// n = 13  把数字格式化为指定的长度。
var n=num.toPrecision(3);
// n = 13.4  把数字格式化为指定的长度。

var num = 15;
var n = num.toString();
// n = 15  把数字转换为字符串，使用指定的基数。

var num = 15;
var n = num.valueOf();
// n = 15  返回一个 Number 对象的基本数字值。
```
|isFinite|检测指定参数是否为无穷大。|
|toExponential(x)|把对象的值转换为指数计数法。|
|toFixed(x)|把数字转换为字符串，结果的小数点后有指定位数的数字。|
|toPrecision(x)|把数字格式化为指定的长度。|
|toString()|把数字转换为字符串，使用指定的基数。|
|valueOf()|返回一个 Number 对象的基本数字值。|
|**ES6新方法**|
|isInteger()|用来判断给定的参数是否为整数。|
|isSafeInteger()|判断传入的参数值是否是一个"安全整数"。安全整数范围为 -(2^53 - 1)到 2^53 - 1 之间的整数，包含 -(2^53 - 1)和 2^53 - 1。|
### 3.ES6新方法
```js
// 用来判断给定的参数是否为整数。
Number.isInteger(10);        // 返回 true
Number.isInteger(10.5);      // 返回 false
// 判断传入的参数值是否是一个"安全整数"。安全整数范围为 -(2^53 - 1)到 2^53 - 1 之间的整数，包含 -(2^53 - 1)和 2^53 - 1。
Number.isSafeInteger(10);    // 返回 true  
Number.isSafeInteger(12345678901234567890);  // 返回 false
```