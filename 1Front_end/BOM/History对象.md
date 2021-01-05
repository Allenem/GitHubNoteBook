# History对象

History 对象包含用户（在浏览器窗口中）访问过的 URL。

History 对象是 window 对象的一部分，可通过 window.history 属性对其进行访问。

![Note](https://upload-images.jianshu.io/upload_images/7728717-9e655689e7bb8916.gif?imageMogr2/auto-orient/strip) **注意：** 没有应用于History对象的公开标准，不过所有浏览器都支持该对象。

## CONTENT

### History 对象属性

| 属性 | 说明 |
|-|-|
| length | 返回历史列表中的网址数 |

### History 对象方法

| 方法 | 说明 |
|-|-|
| back() | 加载 history 列表中的前一个 URL |
| forward() | 加载 history 列表中的下一个 URL |
| go() | 加载 history 列表中的某个具体页面 |

* * * 

## History对象属性&对象方法

```js
console.log("历史列表中URL的数量: " + history.length);
// 历史列表中URL的数量: 1
document.write(`<input type="button" value="后退" onclick="window.history.back()">`);
// 后退
document.write(`<input type="button" value="前进" onclick="window.history.forward()">`);
// 前进
document.write(`<input type="button" value="前进2" onclick="window.history.go(2)">`);
// 前进2
document.write(`<input type="button" value="后退2" onclick="window.history.go(-2)">`);
// 后退2
```

**定义和用法**

`length` 属性声明了浏览器历史列表中的元素数量。

&hearts; 注意：Internet Explorer和Opera从0开始，而Firefox、Chrome和Safari从1开始。

`back()` 方法可加载历史列表中的前一个 URL（如果存在）。

调用该方法的效果等价于点击后退按钮或调用 history.go(-1)。

`forward()` 方法可加载历史列表中的下一个 URL。

调用该方法的效果等价于点击前进按钮或调用 history.go(1)。

`go()` 方法可加载历史列表中的某个具体的页面。

该参数可以是数字，使用的是要访问的 URL 在 History 的 URL 列表中的相对位置。（-1上一个页面，1前进一个页面)。或一个字符串，字符串必须是局部或完整的URL，该函数会去匹配字符串的第一个URL。

**语法**

`history.length`

`history.back()`

`history.forward()`

`history.go(number|URL)`