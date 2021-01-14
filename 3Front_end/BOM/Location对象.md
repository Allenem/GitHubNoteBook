# Location对象

Location 对象包含有关当前 URL 的信息。

Location 对象是 window 对象的一部分，可通过 `window.Location` 属性对其进行访问。

![Note](https://upload-images.jianshu.io/upload_images/7728717-1c5bf151dbe35ba1.gif?imageMogr2/auto-orient/strip) **注意：** 没有应用于Location对象的公开标准，不过所有浏览器都支持该对象。

## CONTENT

### [Location 对象属性](#Location对象属性)

| 属性 | 描述 |
|-|-|
| hash | 返回一个URL的锚部分 |
| host | 返回一个URL的主机名和端口 |
| hostname | 返回URL的主机名 |
| href | 返回完整的URL |
| pathname | 返回的URL路径名。 |
| port | 返回一个URL服务器使用的端口号 |
| protocol | 返回一个URL协议 |
| search | 返回一个URL的查询部分 |

### [Location 对象方法](#Location对象方法)

| 方法 | 说明 |
|-|-|
| [assign()](https://www.runoob.com/jsref/met-loc-assign.html) | 载入一个新的文档 |
| [reload()](https://www.runoob.com/jsref/met-loc-reload.html) | 重新载入当前文档 |
| [replace()](https://www.runoob.com/jsref/met-loc-replace.html) | 用新的文档替换当前文档 |

* * * 

## Location对象属性

```js
console.log(location.hash);
// #part2
console.log(location.host);
// www.runoob.com
console.log(location.hostname);
// www.runoob.com
console.log(location.href);
// https://www.runoob.com/jsref/prop-loc-href.html
console.log(location.pathname);
// /jsref/prop-loc-pathname.html
console.log(location.port);
// 
console.log(location.protocol);
// https:

// 假设当前的URL就是http://www.runoob.com/submit.htm?email=someone@ example.com：
console.log(location.search);
// ?email=someone@example.com
```

**定义和用法**

`hash` 属性是一个可读可写的字符串，该字符串是 URL 的锚部分（从 # 号开始的部分）。

`host` 属性是一个可读可写的字符串，可设置或返回当前 URL 的主机名称和端口号。

`hostname` 属性是一个可读可写的字符串，可设置或返回当前 URL 的主机名。

`href` 属性是一个可读可写的字符串，可设置或返回当前显示的文档的完整 URL。

`pathname` 属性是一个可读可写的字符串，可设置或返回当前 URL 的路径部分。

`port` 属性是一个可读可写的字符串，可设置或返回当前 URL 的端口部分。

&hearts; 注意：如果端口号就是80（这是默认的端口号)，无需指定。

`protocol` 属性是一个可读可写的字符串，可设置或返回当前 URL 的协议。

`search` 属性是一个可读可写的字符串，可设置或返回当前 URL 的查询部分（问号 ? 之后的部分）。

**语法**

`location.hash`

`location.host`

`location.hostname`

`location.href`

`location.pathname`

`location.port`

`location.protocol`

`location.search`

## Location对象方法

```html
<input type="button" value="载入新文档" onclick="window.location.assign('http://www.runoob.com')">

<input type="button" value="重新加载页面" onclick="location.reload()">

<input type="button" value="载入新文档替换当前页面" onclick="window.location.replace('http://www.runoob.com')">
```

**定义和用法**

`assign()` 方法加载一个新的文档。

`reload()` 方法用于刷新当前文档。

`replace()` 方法可用一个新文档取代当前文档。

语法

**语法**

`location.assign(URL)`

`location.reload(forceGet)`

| 参数 | 类型 | 描述 |
|-|-|-|
| *forceGet* | Boolean | 可选。如果把该方法的参数设置为 true，那么无论文档的最后修改日期是什么，它都会绕过缓存，从服务器上重新下载该文档。 |

`location.replace(newURL)`