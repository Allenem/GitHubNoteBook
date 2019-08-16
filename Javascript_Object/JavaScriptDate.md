# JavaScript Date

## Date 对象

Date 对象用于处理日期与时间。

创建 Date 对象： new Date()

以下四种方法同样可以创建 Date 对象：
```js
var d = new Date();  // 当前日期和时间
var d = new Date(milliseconds);  // 返回从 1970 年 1 月 1 日至今的毫秒数
var d = new Date(dateString);  // 返回时间字符串
var d = new Date(year, month, day, hours, minutes, seconds, milliseconds);  // 返回设定格式时间
```
实例化如下
```js
var d1 = new Date();  // Fri Aug 16 2019 09:07:53 GMT+0800 (中国标准时间)
var d2 = new Date(3600*24*1000*365)  // Fri Jan 01 1971 08:00:00 GMT+0800 (中国标准时间)
var d3 = new Date(79,5,24)  // Sun Jun 24 1979 00:00:00 GMT+0800 (中国标准时间)
var d3 = new Date(2079,5,24)  // Sat Jun 24 2079 00:00:00 GMT+0800 (中国标准时间)
var d4 = new Date(79,0,24,11,33,0)  // Wed Jan 24 1979 11:33:00 GMT+0800 (中国标准时间)
```

&hearts; 注意：月份0-11表示1-12月

## CONTENT

### Date 对象属性

| 属性 | 描述 |
|-|-|
| [constructor](#1constructor) | 返回对创建此对象的 Date 函数的引用。 |
| [prototype](#2prototype) | 使您有能力向对象添加属性和方法。 |

### Date 对象方法

| 方法 | 描述 |
|-|-|
| [getFullYear()](#1get) | 从 Date 对象以四位数字返回年份。 |
| [getMonth()](#1get) | 从 Date 对象返回月份 (0 ~ 11)。 |
| [getDate()](#1get) | 从 Date 对象返回一个月中的某一天 (1 ~ 31)。 |
| [getDay()](#1get) | 从 Date 对象返回一周中的某一天 (0 ~ 6)。 |
| [getHours()](#1get) | 返回 Date 对象的小时 (0 ~ 23)。 |
| [getMinutes()](#1get) | 返回 Date 对象的分钟 (0 ~ 59)。 |
| [getSeconds()](#1get) | 返回 Date 对象的秒数 (0 ~ 59)。 |
| [getMilliseconds()](#1get) | 返回 Date 对象的毫秒(0 ~ 999)。 |
| [getTime()](#1get) | 返回 1970 年 1 月 1 日至今的毫秒数。 |
| [getTimezoneOffset()](#1get) | 返回本地时间与格林威治标准时间 (GMT) 的分钟差。 |
| [getUTCFullYear()](#1get) | 根据世界时从 Date 对象返回四位数的年份。 |
| [getUTCMonth()](#1get) | 根据世界时从 Date 对象返回月份 (0 ~ 11)。 |
| [getUTCDate()](#1get) | 根据世界时从 Date 对象返回月中的一天 (1 ~ 31)。 |
| [getUTCDay()](#1get) | 根据世界时从 Date 对象返回周中的一天 (0 ~ 6)。 |
| [getUTCHours()](#1get) | 根据世界时返回 Date 对象的小时 (0 ~ 23)。 |
| [getUTCMinutes()](#1get) | 根据世界时返回 Date 对象的分钟 (0 ~ 59)。 |
| [getUTCSeconds()](#1get) | 根据世界时返回 Date 对象的秒钟 (0 ~ 59)。 |
| [getUTCMilliseconds()](#1get) | 根据世界时返回 Date 对象的毫秒(0 ~ 999)。 |
| getYear() | **已废弃**。 请使用 getFullYear() 方法代替。 |
| [parse()](#2parse) | 返回1970年1月1日午夜到指定日期（字符串）的毫秒数。 |
| [setFullYear()](#3set) | 设置 Date 对象中的年份（四位数字）。 |
| [setMonth()](#3set) | 设置 Date 对象中月份 (0 ~ 11)。 |
| [setDate()](#3set) | 设置 Date 对象中月的某一天 (1 ~ 31)。 |
| [setHours()](#3set) | 设置 Date 对象中的小时 (0 ~ 23)。 |
| [setMinutes()](#3set) | 设置 Date 对象中的分钟 (0 ~ 59)。 |
| [setSeconds()](#3set) | 设置 Date 对象中的秒钟 (0 ~ 59)。 |
| [setMilliseconds()](#3set) | 设置 Date 对象中的毫秒 (0 ~ 999)。 |
| [setTime()](#3set) | setTime() 方法以毫秒设置 Date 对象。 |
| [setUTCFullYear()](#3set) | 根据世界时设置 Date 对象中的年份（四位数字）。 |
| [setUTCMonth()](#3set) | 根据世界时设置 Date 对象中的月份 (0 ~ 11)。 |
| [setUTCDate()](#3set) | 根据世界时设置 Date 对象中月份的一天 (1 ~ 31)。 |
| [setUTCHours()](#3set) | 根据世界时设置 Date 对象中的小时 (0 ~ 23)。 |
| [setUTCMinutes()](#3set) | 根据世界时设置 Date 对象中的分钟 (0 ~ 59)。 |
| [setUTCSeconds()](#3set) | setUTCSeconds() 方法用于根据世界时 (UTC) 设置指定时间的秒字段。 |
| [setUTCMilliseconds()](#3set) | 根据世界时设置 Date 对象中的毫秒 (0 ~ 999)。 |
| setYear() | **已废弃**。请使用 setFullYear() 方法代替。 |
| [toDateString()](#4to) | 把 Date 对象的日期部分转换为字符串。 |
| toGMTString() | **已废弃**。请使用 toUTCString() 方法代替。 |
| [toISOString()](#4to) | 使用 ISO 标准返回字符串的日期格式。 |
| [toJSON()](#4to) | 以 JSON 数据格式返回日期字符串。 |
| [toLocaleDateString()](#4to) | 根据本地时间格式，把 Date 对象的日期部分转换为字符串。 |
| [toLocaleTimeString()](#4to) | 根据本地时间格式，把 Date 对象的时间部分转换为字符串。 |
| [toLocaleString()](#4to) | 据本地时间格式，把 Date 对象转换为字符串。 |
| [toString()](#4to) | 把 Date 对象转换为字符串。 |
| [toTimeString()](#4to) | 把 Date 对象的时间部分转换为字符串。 |
| [toUTCString()](#4to) | 根据世界时，把 Date 对象转换为字符串。 |
| [UTC()](#5utc) | 根据世界时返回 1970 年 1 月 1 日 到指定日期的毫秒数。 |
| [valueOf()](#6valueof) | 返回 Date 对象的原始值。 |


## Date 对象属性

### 1.constructor
```js
var d = new Date();
console.log(d.constructor);  // ƒ Date() { [native code] }
```

constructor 属性返回对创建此对象的 Date 函数的引用。

**语法**

`date.constructor`

### 2.prototype
```js
Date.prototype.myMet=function(){
	if (this.getMonth()==0){this.myProp="一月"};
	if (this.getMonth()==1){this.myProp="二月"};
	if (this.getMonth()==2){this.myProp="三月"};
	if (this.getMonth()==3){this.myProp="四月"};
	if (this.getMonth()==4){this.myProp="五月"};
	if (this.getMonth()==5){this.myProp="六月"};
	if (this.getMonth()==6){this.myProp="七月"};
	if (this.getMonth()==7){this.myProp="八月"};
	if (this.getMonth()==8){this.myProp="九月"};
	if (this.getMonth()==9){this.myProp="十月"};
	if (this.getMonth()==10){this.myProp="十一月"};
	if (this.getMonth()==11){this.myProp="十二月"};
}

var d = new Date();
d.myMet();
console.log(d.myProp);  // 八月
```

prototype 属性使您有能力向对象添加属性和方法。

当构造一个原型，所有的日期对象都会默认添加属性和方法。

注意： 可将属性和方法添加到原型中，但不能为对象分配其他原型。 但是，可以向用户定义的对象分配新的原型。

注意： Prototype是一个全局属性，这对于几乎全部的JavaScript对象。

**语法**

`Date.prototype.name=value`

## Date 对象方法

### 1.get

```js
	var d = new Date();
	console.log(
    d.getFullYear()+' '+d.getMonth()+' '+d.getDate()+' '+d.getDay()+' '+d.getHours()+' '+d.getMinutes()+' '+d.getSeconds()+' '+d.getMilliseconds()+' '+d.getTime()+' '+d.getTimezoneOffset()
  );
  // 2019 7 16 5 10 19 28 878 1565921968878 -480
  // 年 月(0~11) 日 星期日-六(0~6) 时(0~23) 分(0~59) 秒(0-59) 毫秒(0~999) 1970年1月1日至今的毫秒数 格林威治标准时间(GMT)-本地时间的分钟差。

	console.log(
    d.getUTCFullYear()+' '+d.getUTCMonth()+' '+d.getUTCDate()+' '+d.getUTCDay()+' '+d.getUTCHours()+' '+d.getUTCMinutes()+' '+d.getUTCSeconds()+' '+d.getUTCMilliseconds()
  );
  // 2019 7 16 5 2 19 28 878
  // 世界时
```

获取时间

### 2.parse()

```js
Date.parse("March 21, 2012"); // 1332259200000
```

`parse()` 方法可解析一个日期时间字符串，并返回 1970/1/1 午夜距离该日期时间的毫秒数。

### 3.set

```js
var d = new Date();
d.setFullYear(1999);
d.setMonth(0);
d.setDate(1);
d.setHours(0);
d.setMinutes(0);
d.setSeconds(0);
d.setMilliseconds(0);
console.log(d);
// Fri Jan 01 1999 00:00:00 GMT+0800 (中国标准时间)
```

```js
d.setTime(1000*3600*24*365*10+2);  // 315360000002
console.log(d);  // Sun Dec 30 1979 08:00:00 GMT+0800 (中国标准时间)
```

```js
var d = new Date();
d.setUTCFullYear(1999);
d.setUTCMonth(0);
d.setUTCDate(1);
d.setUTCHours(0);
d.setUTCMinutes(0);
d.setUTCSeconds(0);
d.setUTCMilliseconds(0);
console.log(d);
// Fri Jan 01 1999 08:00:00 GMT+0800 (中国标准时间)
```

设置时间

### 4.to

```js
var d = new Date();
console.log(
  d.toISOString()+'\n'+d.toDateString()+'\n'+d.toJSON()+'\n'+d.toUTCString()+'\n\n'+d.toLocaleDateString()+'\n'+d.toLocaleTimeString()+'\n'+d.toLocaleString()+'\n'+d.toString()+'\n'+d.toTimeString()
);
/*
2019-08-16T02:56:28.804Z
Fri Aug 16 2019
2019-08-16T02:56:28.804Z
Fri, 16 Aug 2019 02:56:28 GMT

2019/8/16
上午10:56:28
2019/8/16 上午10:56:28
Fri Aug 16 2019 10:56:28 GMT+0800 (中国标准时间)
10:56:28 GMT+0800 (中国标准时间)
*/
```

转换为指定形式

### 5.UTC()
```js
var d = Date.UTC(2012,02,30);  // d = 1333065600000
```

`UTC()` 方法可根据世界时返回 1970 年 1 月 1 日 到指定日期的毫秒数

&hearts; 提示: 协调世界时，又称世界统一时间，世界标准时间，国际协调时间，简称UTC( Universal Coordinated Time ) 。

&hearts; 注意: UTC时间与GMT(格林尼治时间)相同。

### 6.valueOf()
```js
var d = new Date();
console.log(d.valueOf());  // 1565924654655
```

`valueOf()` 方法返回 Date 对象的原始值。

&hearts; 注意: 原始值返回1970年1月1日午夜以来的毫秒数！
