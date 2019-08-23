# HTMLDOM属性对象

## HTML DOM 节点

在 HTML DOM (Document Object Model) 中, 所有的都是 **节点**：

*   文档是文档节点
*   所有 HTML 元素是元素节点
*   所有 HTML 属性都是属性节点
*   插入到 HTML 元素中的文本为文本节点
*   注释是注释节点

* * *

## Attr 对象

在 HTML DOM 中, **Attr 对象** 代表一个 HTML 属性。

HTML属性总是属于HTML元素。

* * *

## NamedNodeMap 对象

在 HTML DOM 中, the **NamedNodeMap 对象** 表示一个无顺序的节点列表。

我们可通过节点名称来访问 NamedNodeMap 中的节点。

* * *

## 浏览器支持

![Internet Explorer](https://upload-images.jianshu.io/upload_images/7728717-d244e69d41316df3.gif?imageMogr2/auto-orient/strip "Internet Explorer")
![Firefox](https://upload-images.jianshu.io/upload_images/7728717-1d3939dfca340786.gif?imageMogr2/auto-orient/strip "Firefox")
![Opera](https://upload-images.jianshu.io/upload_images/7728717-51fe7ad9bb8562e1.gif?imageMogr2/auto-orient/strip "Opera")
![Google Chrome](https://upload-images.jianshu.io/upload_images/7728717-78974fef397a0135.gif?imageMogr2/auto-orient/strip "Google Chrome")
![Safari](https://upload-images.jianshu.io/upload_images/7728717-f06980586ac379f6.gif?imageMogr2/auto-orient/strip "Safari")

所有主流浏览器都支持 Attr 对象和 NamedNodeMap 对象。

* * *
## CONTENT

| 属性 / 方法 | 描述 |
|-|-|
| [*attr*.isId](#isId) | 如果属性是 ID 类型，则 isId 属性返回 true，否则返回 false。 |
| [*attr*.name](#name) | 返回属性名称 |
| [*attr*.value](#value) | 设置或者返回属性值 |
| [*attr*.specified](#specified) | 如果属性被指定返回 true ，否则返回 false |
| - | - |
| [*nodemap*.getNamedItem()](#getNamedItem) | 从节点列表中返回的指定属性节点。 |
| [*nodemap*.item()](#item) | 返回节点列表中处于指定索引号的节点。 |
| [*nodemap*.length](#length) | 返回节点列表的节点数目。 |
| [*nodemap*.removeNamedItem()](#removeNamedItem) | 删除指定属性节点 |
| [*nodemap*.setNamedItem()](#setNamedItem) | 设置指定属性节点(通过名称) |

* * *

## DOM 4 警告 !!!

在 W3C DOM 内核中, Attr (属性) 对象继承节点对象的所有属性和方法 。

在 DOM 4 中, Attr (属性) 对象不再从节点对象中继承。

**从长远的代码质量来考虑，在属性对象中你需要避免使用节点对象属性和方法:**

| 属性 / 方法 | 避免原因 |
|-|-|
| *attr*.appendChild() | 属性没有子节点 |
| *attr*.attributes | 属性没有属性 |
| *attr*.baseURI | 使用 document.baseURI 替代 |
| *attr*.childNodes | 属性没有子节点 |
| *attr*.cloneNode() | 使用 attr.value 替代 |
| *attr*.firstChild | 属性没有子节点 |
| *attr*.hasAttributes() | 属性没有属性 |
| *attr*.hasChildNodes | 属性没有子节点 |
| *attr*.insertBefore() | 属性没有子节点 |
| *attr*.isEqualNode() | 没有意义 |
| *attr*.isSameNode() | 没有意义 |
| *attr*.isSupported() | 通常为 true |
| *attr*.lastChild | 属性没有子节点 |
| *attr*.nextSibling | 属性没有兄弟节点 |
| *attr*.nodeName | 使用 *attr*.name 替代 |
| *attr*.nodeType | 通常为 2 (ATTRIBUTE-NODE) |
| *attr*.nodeValue | 使用 *attr*.value 替代 |
| *attr*.normalize() | 属性没有规范 |
| *attr*.ownerDocument | 通常为你的 HTML 文档 |
| *attr*.ownerElement | 你用来访问属性的 HTML 元素 |
| *attr*.parentNode | 你用来访问属性的 HTML 元素 |
| *attr*.previousSibling | 属性没有兄弟节点 |
| *attr*.removeChild | 属性没有子节点 |
| *attr*.replaceChild | 属性没有子节点 |
| *attr*.textContent | 使用 *attr*.value 替代 |

* * *

## isId

```js
// 检查属性是否为元素的 ID 属性：
document.getElementById("demo").attributes[0].isId;
// true
```

**定义和使用**

如果属性是 ID 类型（例如，包含了其所属的元素的标识符），则 `isId` 属性返回 true，否则返回 false。

**语法**

`attribute.isId`

**技术细节**

返回值：	Boolean, true|false

* * *

## name

```html
<p id="demo">单击按钮来显示按钮第一个属性的名称</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var btn=document.getElementsByTagName("button")[0];
	var x=document.getElementById("demo");
	x.innerHTML=btn.attributes[0].name;   // onclick
}
</script>
```

**定义和使用**

`name` 属性返回属性名称。

**语法**

`attribute.name`

**技术细节**

返回值：	字符串，代表属性名称。

* * *

## value

```html
<!-- 返回属性值 -->
<p id="demo">单击按钮获取按钮的第一属性的值。</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var btn=document.getElementsByTagName("BUTTON")[0];
	var x=document.getElementById("demo");
	x.innerHTML=btn.attributes[0].value;  // myFunction()
}
</script>


<!-- 设置属性值 -->
<h1 style="color:red;">Hello World</h1>
<p id="demo">单击按钮改变上面标题的样式属性。</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var h=document.getElementsByTagName("H1")[0];
	h.getAttributeNode("style").value="color:green";
}
</script>
```

**定义和使用**

`value` 属性用于设置或者返回属性的值。

**语法**

设置属性值

`attribute.value=value`

返回属性值

`attribute.value`

**技术细节**

返回值：	字符串, 代表属性的值。

* * *

## specified

```html
<p id="demo">单击按钮查找按钮是否有onclick属性</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var btn=document.getElementsByTagName("BUTTON")[0];
	var x=document.getElementById("demo");
	x.innerHTML=btn.getAttributeNode("onclick").specified;  // true
}
</script>
```

**定义和使用**

如果在文档中设置了属性值，则 `specified` 属性返回 true，如果是 DTD/Schema 中的默认值，则返回 false。

**语法**

`attribute.specified`

**技术细节**

返回值：	Boolean, true|false


* * *

## getNamedItem

```html
<p id="demo">单击按钮获取按钮元素中onclick属性的值</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var a=document.getElementsByTagName("BUTTON")[0];
	var x=document.getElementById("demo");  
	x.innerHTML=a.attributes.getNamedItem("onclick").textContent;  // myFunction()
}
</script>
```

**定义和使用**

`getNamedItem()` 方法返回节点列表中指定属性名的值。

**语法**

`namednodemap.getNamedItem(name)`

**参数**

|参数	|类型	|描述|
|-|-|-|
|nodename	|String	|必须。节点列表中你想返回的节点名。|

**返回值**

|类型	|描述|
|-|-|
|节点对象	|指定名的节点。|

* * *

## item

```
<p id="demo">单击按钮获取按钮元素的第一个属性的名称</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var a=document.getElementsByTagName("BUTTON")[0];
	var x=document.getElementById("demo");  
	x.innerHTML=a.attributes.item(0).nodeName;
}
</script>
```

**定义和使用**

`item()` 方法可返回节点列表中处于指定索引号的节点。

语法:

`document.getElementsByTagName("BUTTON")[0].attributes.item(0);`

另外一种写法:

`document.getElementsByTagName("BUTTON")[0].attributes[0];`


所有主要浏览器都支持 item() 方法

**语法**

`namednodemap.item(index)`

**参数**

|参数	|类型	|描述|
|-|-|-|
|index	|Number	|必须。节点列表中指定的节点索引号。|

**返回值**

|类型	|描述|
|-|-|
|节点对象	|指定索引的节点|

* * *

## length

```html
<p id="demo">单击按钮查看按钮元素有多少属性</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var a=document.getElementsByTagName("BUTTON")[0].attributes;
	var x=document.getElementById("demo");  
	x.innerHTML=a.length;
}
</script>
<p>结果将是1 (按钮元素的onclick属性)。</p>
```

**定义和使用**

`length` 属性可返回集合中节点的选项数目。

**语法**

`namednodemap.length`

**技术细节**

返回值：	数字, 代表节点的数目。

* * *

## removeNamedItem
```html
<input type="button" value="OK">
<p id="demo">单击下面的按钮删除上面元素的属性类型。</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var btn=document.getElementsByTagName("INPUT")[0];
	btn.attributes.removeNamedItem("type");
}
</script>
<!-- 注意: 当删除一个输入元素的type属性,元素的类型将变成 text ,这是默认值。 -->
<!-- 注意:In Internet Explorer 8 及更早的版本中，removedNamedItem也将返回属性值，但是不会移除属性。 -->
```

**定义和使用**

`removeNamedItem()` 方法可删除指定的节点。

**语法**

`namednodemap.removeNamedItem(nodename)`

**参数**

|参数	|类型	|描述|
|-|-|-|
|nodename	|String	|必须，节点列表中你要删除的节点名。|

**返回值**

|类型	|描述|
|-|-|
|节点对象	|移除的节点|

* * *

## setNamedItem

```html
<style type="text/css">
.democlass{
	color:red;
}
</style>
</head>
<body>

<h1>Hello World</h1>
<p id="demo">单击按钮设置H1的class属性为“democlass”</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var h=document.getElementsByTagName("H1")[0];
	var typ=document.createAttribute("class");
	typ.nodeValue="democlass";
	h.attributes.setNamedItem(typ);  //Hello World 变红
}
</script>

</body>
```

**定义和使用**

`setNamedItem()` 方法用于添加指定节点。

如果节点已经存在，它将被替换，并返回替换节点的值，否则将返回 null。

**语法**

`namednodemap.setNamedItem(node)`

**参数**

|参数	|类型	|描述|
|-|-|-|
|node	|节点对象	|必须。在节点列表中你想替换的节点。|

**返回值**

|类型	|描述|
|-|-|
|节点对象	|返回替换的节点，如果没有替换则返回 null|