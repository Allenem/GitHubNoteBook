# Navigator对象

`Navigator` 对象包含有关浏览器的信息。

![Note](https://upload-images.jianshu.io/upload_images/7728717-f1d7418769c7bd51.gif?imageMogr2/auto-orient/strip) **注意：** 没有应用于 navigator 对象的公开标准，不过所有浏览器都支持该对象。

* * *

## CONTENT

### [Navigator 对象属性](#Navigator对象属性)

| 属性 | 说明 |
|-|-|
| [appCodeName](#Navigator对象属性) | 返回浏览器的代码名 |
| [appName](#Navigator对象属性) | 返回浏览器的名称 |
| [appVersion](#Navigator对象属性) | 返回浏览器的平台和版本信息 |
| [cookieEnabled](#Navigator对象属性) | 返回指明浏览器中是否启用 cookie 的布尔值 |
| [platform](#Navigator对象属性) | 返回运行浏览器的操作系统平台 |
| [userAgent](#Navigator对象属性) | 返回由客户机发送服务器的user-agent 头部的值 |

### [Navigator 对象方法](#Navigator对象方法)

| 方法 | 描述 |
|-|-|
| [javaEnabled()](#Navigator对象方法) | 指定是否在浏览器中启用Java |
| [taintEnabled()](#Navigator对象方法) | 规定浏览器是否启用数据污点(data tainting) |

***

## Navigator对象属性

```js
console.log("浏览器代号: " + navigator.appCodeName);
// 浏览器代号: Mozilla
console.log("浏览器名称: " + navigator.appName);
// 浏览器名称: Netscape
console.log("版本信息: " + navigator.appVersion);  
// 版本信息: 5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36
console.log("是否启用 Cookie: " + navigator.cookieEnabled);
// 是否启用 Cookie: true
console.log("硬件平台: " + navigator.platform);
// 硬件平台: Win32
console.log("用户代理: " + navigator.userAgent);
// 用户代理: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/76.0.3809.100 Safari/537.36
```

**定义和用法**

`appCodeName` 属性是一个只读字符串，声明了浏览器的代码名。

`appName` 属性可返回浏览器的名称。

`appVersion` 属性可返回浏览器的平台和版本信息。该属性是一个只读的字符串。

`cookieEnabled` 属性可返回一个布尔值，如果浏览器启用了 cookie，该属性值为 true。如果禁用了 cookie，则值为 false。

`platform` 属性是一个只读的字符串，声明了运行浏览器的操作系统和（或）硬件平台。

`userAgent` 属性是一个只读的字符串，声明了浏览器用于 HTTP 请求的用户代理头的值。

**语法**

`navigator.appCodeName`

`navigator.appName`

`navigator.appVersion`

`navigator.cookieEnabled`

`navigator.platform`

`navigator.userAgent`

***

## Navigator对象方法

```js
console.log("启用Java: " + navigator.javaEnabled());
// 启用Java: false
console.log("启用数据污点: " + navigator.taintEnabled());
// VM871:1 Uncaught TypeError: navigator.taintEnabled is not a function at <anonymous>:1:36
```

**定义和用法**

`javaEnabled()` 方法可返回一个布尔值，该值指示浏览器是否支持并启用了 Java。如果是，则返回 true，否则返回 false。

`taintEnabled()` 方法可返回一个布尔值，该值声明了当前浏览器是否启用了数据污点 (data tainting)。

**语法**

`navigator.javaEnabled()`

`navigator.taintEnabled()`