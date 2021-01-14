# Javascript存储对象

Web 存储 API 提供了 sessionStorage （会话存储） 和 localStorage（本地存储）两个存储对象来对网页的数据进行添加、删除、修改、查询操作。

*   localStorage 用于长久保存整个网站的数据，保存的数据没有过期时间，直到手动去除。

*   sessionStorage 用于临时保存同一窗口(或标签页)的数据，在关闭窗口或标签页之后将会删除这些数据。

## CONTENT

### 存储对象属性

| 属性 | 描述 |
|-|-|
| length | 返回存储对象中包含多少条数据。 |

### 存储对象方法

| 方法 | 描述 |
|-|-|
| key(*n*) | 返回存储对象中第 *n* 个键的名称 |
| getItem(*keyname*) | 返回指定键的值 |
| setItem(*keyname*, *value*) | 添加键和值，如果对应的值存在，则更新该键对应的值。 |
| removeItem(*keyname*) | 移除键 |
| clear() | 清除存储对象中所有的键 |

### [Web 存储 API](#Web存储API)

| 属性 | 描述 |
|-|-|
| [window.localStorage](#Web存储API) | 在浏览器中存储 key/value 对。没有过期时间。 |
| [window.sessionStorage](#Web存储API) | 在浏览器中存储 key/value 对。 在关闭窗口或标签页之后将会删除这些数据。 |

***

## Web存储API

```js
// localStorage
// 判断浏览器是否支持
if (typeof(Storage) !== "undefined") {
    // 存储
    localStorage.setItem("lastname", "Smith");
    // 检索
    document.getElementById("result").innerHTML = localStorage.getItem("lastname")?localStorage.getItem("lastname"):"there is no this data";
} else {
    document.getElementById("result").innerHTML = "Sorry, your browser does not support Web Storage...";
}


// sessionStorage
// 检测浏览器支持
if (typeof(Storage) !== "undefined") {
    // 存储
    sessionStorage.setItem("lastname", "Smith");
    // 检索
    document.getElementById("result").innerHTML = sessionStorage.getItem("lastname")?sessionStorage.getItem("lastname"):"there is no this data";
} else {
    document.getElementById("result").innerHTML = "Sorry, your browser does not support Web Storage...";
}
```

**定义和使用**

`localStorage` 和 `sessionStorage` 属性允许在浏览器中存储 key/value 对的数据。

`localStorage` 用于长久保存整个网站的数据，保存的数据没有过期时间，直到手动去删除。

`localStorage` 属性是只读的。

`sessionStorage` 用于临时保存同一窗口(或标签页)的数据，在关闭窗口或标签页之后将会删除这些数据。

**语法**

`window.localStorage`

保存数据语法：

`localStorage.setItem("key", "value");`

读取数据语法：

`var lastname = localStorage.getItem("key");`

删除数据语法：

`localStorage.removeItem("key");`

***

`window.sessionStorage`

保存数据语法：

`sessionStorage.setItem("key", "value");`

读取数据语法：

`var lastname = sessionStorage.getItem("key");`

删除指定键的数据语法：

`sessionStorage.removeItem("key");`

删除所有数据：

`sessionStorage.clear();`