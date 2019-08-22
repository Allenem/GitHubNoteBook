# HTMLDOMDocument对象

## HTML DOM 节点

在 HTML DOM (Document Object Model) 中 , 每一个元素都是 **节点**:

*   文档是一个文档节点。
*   所有的HTML元素都是元素节点。
*   所有 HTML 属性都是属性节点。
*   文本插入到 HTML 元素是文本节点。are text nodes。
*   注释是注释节点。

* * *
## Document 对象

当浏览器载入 HTML 文档, 它就会成为 **Document 对象**。

Document 对象是 HTML 文档的根节点。

Document 对象使我们可以从脚本中对 HTML 页面中的所有元素进行访问。

**提示：**Document 对象是 Window 对象的一部分，可通过 window.document 属性对其进行访问。

* * *

## 浏览器支持

![Internet Explorer](https://upload-images.jianshu.io/upload_images/7728717-944860db906fda6b.gif?imageMogr2/auto-orient/strip "Internet Explorer")
![Firefox](https://upload-images.jianshu.io/upload_images/7728717-165ff9083573b3d6.gif?imageMogr2/auto-orient/strip "Firefox")
![Opera](https://upload-images.jianshu.io/upload_images/7728717-10211f8bc09ea5ab.gif?imageMogr2/auto-orient/strip "Opera")
![Google Chrome](https://upload-images.jianshu.io/upload_images/7728717-b7a42c2ca466331b.gif?imageMogr2/auto-orient/strip "Google Chrome")
![Safari](https://upload-images.jianshu.io/upload_images/7728717-9d4682ab9dab02c7.gif?imageMogr2/auto-orient/strip "Safari")

所有主要浏览器都支持 Document 对象。

参考地址：

https://developer.mozilla.org/zh-CN/docs/Web/API/Node

https://www.runoob.com/jsref/dom-obj-document.html

* * *

## Document 对象属性和方法

HTML文档中可以使用以下属性和方法:

| 属性 / 方法 | 描述 |
|-|-|
| [document.activeElement](#activeElement) | 返回当前获取焦点元素 |
| [document.addEventListener()](#addEventListenerremoveEventListener) | 向文档添加句柄 |
| [document.removeEventListener()](#addEventListenerremoveEventListener) | 移除文档中的事件句柄(由 addEventListener() 方法添加) |
| [document.adoptNode(node)](#adpotNode) | 从另外一个文档返回 adapded 节点到当前文档。 |
| document.anchors|  **已废弃**。返回对文档中所有 Anchor 对象的引用。 |
| document.applets | 返回对文档中所有 Applet 对象的引用。**注意:** HTML5 已不支持 \<applet>元素。 |
| [document.title](#baseURI) | 返回当前文档的标题。 |
| [document.baseURI](#baseURI) | 返回文档的绝对基础 URI |
| [document.URL](#baseURI) | 返回文档完整的URL |
| [document.body](#body) | 返回文档的body元素 |
| [document.open()](#openclose) | 打开一个流，以收集来自任何 document.write() 或 document.writeln() 方法的输出。 |
| [document.close()](#openclose) | 关闭用 document.open() 方法打开的输出流，并显示选定的数据。 |
| [document.write()](#writewriteln) | 向文档写 HTML 表达式 或 JavaScript 代码。 |
| [document.writeln()](#writewriteln) | 等同于 write() 方法，不同的是在每个表达式之后写一个换行符。 |
| [document.cookie](#cookie) | 设置或返回与当前文档有关的所有 cookie。 |
| [document.createAttribute()](#createAttribute) | 创建一个属性节点 |
| [document.createComment()](#createComment) | createComment() 方法可创建注释节点。 |
| [document.createDocumentFragment()](#createdocumentfragment) | 创建空的 DocumentFragment 对象，并返回此对象。 |
| [document.createElement()](#createElementcreateTextNode) | 创建元素节点。 |
| [document.createTextNode()](#createElementcreateTextNode) | 创建文本节点。 |
| [document.getElementsByClassName()](#get) | 返回文档中所有指定类名的元素集合，作为 NodeList 对象。 |
| [document.getElementById()](#get) | 返回对拥有指定 id 的第一个对象的引用。 |
| [document.getElementsByName()](#get) | 返回带有指定名称的对象集合。 |
| [document.getElementsByTagName()](#get) | 返回带有指定标签名的对象集合。 |
| [document.querySelector()](#get) | 返回文档中匹配指定的CSS选择器的第一元素 |
| [document.querySelectorAll()](#get) | document.querySelectorAll() 是 HTML5中引入的新方法，返回文档中匹配的CSS选择器的所有元素节点列表 |
| [document.doctype](https://www.runoob.com/jsref/prop-document-doctype.html) | 返回与文档相关的文档类型声明 (DTD)。 |
| [document.documentElement](https://www.runoob.com/jsref/prop-document-documentelement.html) | 返回文档的根节点 |
| [document.documentMode](https://www.runoob.com/jsref/prop-doc-documentmode.html) | 返回用于通过浏览器渲染文档的模式 |
| [document.documentURI](https://www.runoob.com/jsref/prop-document-documenturi.html) | 设置或返回文档的位置 |
| [document.domain](https://www.runoob.com/jsref/prop-doc-domain.html) | 返回当前文档的域名。 |
| document.domConfig | **已废弃**。返回 normalizeDocument() 被调用时所使用的配置。 |
| [document.embeds](https://www.runoob.com/jsref/coll-doc-embeds.html) | 返回文档中所有嵌入的内容（embed）集合 |
| [document.forms](https://www.runoob.com/jsref/coll-doc-forms.html) | 返回对文档中所有 Form 对象引用。 |
| [document.images](https://www.runoob.com/jsref/coll-doc-images.html) | 返回对文档中所有 Image 对象引用。 |
| [document.implementation](https://www.runoob.com/jsref/prop-document-implementation.html) | 返回处理该文档的 DOMImplementation 对象。 |
| [document.importNode()](https://www.runoob.com/jsref/met-document-importnode.html) | 把一个节点从另一个文档复制到该文档以便应用。 |
| [document.inputEncoding](https://www.runoob.com/jsref/prop-document-inputencoding.html) | 返回用于文档的编码方式（在解析时）。 |
| [document.lastModified](https://www.runoob.com/jsref/prop-doc-lastmodified.html) | 返回文档被最后修改的日期和时间。 |
| [document.links](https://www.runoob.com/jsref/coll-doc-links.html) | 返回对文档中所有 Area 和 Link 对象引用。 |
| [document.normalize()](https://www.runoob.com/jsref/met-document-normalize.html) | 删除空文本节点，并连接相邻节点 |
| [document.normalizeDocument()](https://www.runoob.com/jsref/met-document-normalizedocument.html) | 删除空文本节点，并连接相邻节点的 |
| [document.readyState](https://www.runoob.com/jsref/prop-doc-readystate.html) | 返回文档状态 (载入中……) |
| [document.referrer](https://www.runoob.com/jsref/prop-doc-referrer.html) | 返回载入当前文档的文档的 URL。 |
| [document.renameNode()]() | **主流浏览器不支持**重命名元素或者属性节点。 |
| [document.scripts](https://www.runoob.com/jsref/coll-doc-scripts.html) | 返回页面中所有脚本的集合。 |
| [document.strictErrorChecking](https://www.runoob.com/jsref/prop-document-stricterrorchecking.html) | 设置或返回是否强制进行错误检查。 |

* * *

## 警告 ! ! !

在 W3C DOM核心，文档对象 继承节点对象的所有属性和方法。

很多属性和方法在文档中是没有意义的。

**HTML 文档对象可以避免使用这些节点对象和属性：**

|  属性 / 方法 | 避免的原因 |
|-|-|
| document.attributes | 文档没有该属性 |
| document.hasAttributes() | 文档没有该属性 |
| document.nextSibling | 文档没有下一节点 |
| document.nodeName | 这个通常是 #document |
| document.nodeType | 这个通常是 9(DOCUMENT_NODE) |
| document.nodeValue | 文档没有一个节点值 |
| document.ownerDocument | 文档没有主文档 |
| document.ownerElement | 文档没有自己的节点 |
| document.parentNode | 文档没有父节点 |
| document.previousSibling | 文档没有兄弟节点 |
| document.textContent | 文档没有文本节点 |

* * *

## Document对象属性和方法具体解释

## activeElement

```js
// 当前获得焦点的元素
var x = document.activeElement.tagName;
// x 输出结果为：BUTTON
```

**定义和使用**

`activeElement` 属性返回文档中当前获得焦点的元素。

&hearts; 注意： 该属性是只读的。

&hearts; 提示： 为元素设置焦点，可以使用 element.focus() 方法。

&hearts; 提示：可以使用 `document.hasFocus()` 方法来查看当前元素是否获取焦点。

**语法**

`document.activeElement`

* * * 

## addEventListenerremoveEventListener

```html
<body>

<p>文档添加 onmousemove 事件句柄，当在文档中移动鼠标时会显示随机数。</p>
<p>点击按钮移除事件句柄。</p>
<button onclick="removeHandler()">点我</button>
<p id="demo"></p>
<script>
document.addEventListener("mousemove", myFunction);
function myFunction() {
    document.getElementById("demo").innerHTML = Math.random();
}
function removeHandler() {
    document.removeEventListener("mousemove", myFunction);
}
</script>

</body>
```

**定义和使用**

`document.addEventListener()` 方法用于向文档添加事件句柄。

&hearts; 提示：可以使用 `document.removeEventListener()` 方法来移除 addEventListener() 方法添加的事件句柄。

&hearts; 提示：使用 `element.*addEventListener()` 方法为指定元素添加事件句柄。

`document.removeEventListener()` 方法用于移除由 document.addEventListener() 方法添加的事件句柄。

&hearts; 注意: 如果要移除事件句柄，addEventListener() 的执行函数必须使用外部函数，如上实例所示 (myFunction)。

匿名函数，类似 "document.removeEventListener("event", function(){ myScript });" 该事件是无法移除的。

&hearts; 提示： 使用 `element.addEventListener()` 和 `element.removeEventListener()` 方法来添加或移除指定元素的事件句柄。

**语法**

`document.addEventListener(event, function, useCapture)`

`document.removeEventListener(event, function, useCapture)`

**参数值**

| 参数 | 描述 |
|-|-|
| *event* | 必需。描述事件名称的字符串。|
| |**注意：** 不要使用 "on" 前缀。例如，使用 "click" 来取代 "onclick"。|
| |**提示：** 所有 HTML DOM 事件，可以查看我们完整的 [HTML DOM Event 对象参考手册](./HTMLDOM事件对象.md)。 |
| *function* | 必需。描述了事件触发后执行的函数。 |
| |当事件触发时，事件对象会作为第一个参数传入函数。 事件对象的类型取决于特定的事件。例如， "click" 事件属于 MouseEvent(鼠标事件) 对象。 |
| *useCapture* | 可选。布尔值，指定事件是否 在捕获或冒泡阶段执行。|
| |可能值：|
| | *   true - 事件句柄在捕获阶段执行|
| | *   false- 默认。事件句柄在冒泡阶段执行|

* * * 

## adpotNode

```js
// 获取 iframe 中的第一个 H1 元素的，并将其插入到当期文档中：

var frame = document.getElementsByTagName("IFRAME")[0]
var h = frame.contentWindow.document.getElementsByTagName("H1")[0];
var x = document.adoptNode(h);
```

**定义与用法**

`adoptNode()` 方法用于从另外一个文档中获取一个节点。

节点可以是任何节点类型。

&hearts; 注意: 节点下的所有子节点都会获取到。

&hearts; 注意: 节点及其子节点会再源文档中删除。

&hearts; 提示：使用 document.importNode() 方法来拷贝节点，但原文档中的节点不删除。.

&hearts; 提示：使用 element.cloneNode() 方法来拷贝当前文档的节点，且节点不会被删除。

**语法**

`document.adoptNode(node)`

* * *

### baseURI

```html
<p id="demo">单击按钮显示基础URL</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var x=document.getElementById("demo");
	x.innerHTML=document.baseURI;   // https://www.runoob.com/try/demo_source/
    document.write(document.URL);   // 文档的完整的URL: https://www.runoob.com/try/try.php?filename=tryjsref_doc_url
    document.write(document.title); // 菜鸟教程(runoob.com)
}
```

**定义与用法**

`baseURI` 属性返回 HTML 文档的基础URI。

**语法**

`node.baseURI`

* * *

## body

```html
<body>

<p>点击按钮修改当前文档的背景颜色。</p>

<button onclick="myFunction()">点我</button>

<script>
function myFunction() {
    document.body.style.backgroundColor = "yellow";
}
</script>

</body>
```

**定义与用法**

`body` 属性用于设置或返回文档体。

如果是返回, 该属性返回当前文档的 <body> 元素。

如果是设置, 该属性会覆盖所有在 <body> 元素中的子元素, 并用新的内容来替换它。

&hearts; 提示: 与 document.documentElement 属性不同的是， document.body 属性返回 <body> 元素， document.documentElement 属性返回 <html> 元素。

**语法**

返回 body 属性：

`document.body`

设置 body 属性：

`document.body = newContent`

**属性**

|值|描述|
|-|-|
|newContent|指定 \<body> 的新内容|

**技术细节**

|||
|-|-|
|DOM 版本：|Core Level 1 Document Object|
|返回值：|Body 对象的引用，表示 \<body> 元素|

* * *

## openclose

```html
<!-- 打开一个输出流,添加一些文本，然后关闭输出流： -->
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
<script>
function createDoc(){
    var doc=document.open("text/html","replace");
    var txt="<!DOCTYPE html><html><body>学习 HTML DOM 很有趣!</body></html>";
    doc.write(txt);
    doc.close();
}
</script>
</head>

<body>
<input type="button" value="新文档" onclick="createDoc()">
</body>
</html>
```
```html
<!-- 打开输出流 (新窗口打开; about:blank),添加文本，然后关闭输出流: -->

<html>
<body>

<script>
var w=window.open();
w.document.open();
w.document.write("<b>Hello World!</b>");
w.document.close();
</script>

</body>
</html>
```

**定义和用法**

`open()` 方法打开一个输出流来收集 document.write() 或 document.writeln() 方法输出的内容。

调用 open() 方法打开一个新文档并且用 write() 方法设置文档内容后，必须记住用 document.close() 方法关闭文档，并迫使其内容显示出来。

&hearts; 注意：如果目标文件已经存在，它将被清除。如果这个方法没有参数，会显示一个新窗口(about:blank)。

`close()` 方法用于关闭一个由 document.open 方法打开的输出流，并显示选定的数据。

**语法**

`document.open(MIMEtype,replace)`

`document.close()`

|参数|描述|
|-|-|
|MIMEtype|可选。规定正在写的文档的类型。默认值是 "text/html"。|
|replace|可选。当此参数设置后，可引起新文档从父文档继承历史条目。|

* * *

## writewriteln

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
</head>
<body>

<p>注意write()方法不会在每个语句后面新增一行：</p>
<pre>
<script>
document.write("Hello World!");
document.write("Have a nice day!");
</script>
</pre>
<p>注意writeln()方法在每个语句后面新增一行：</p>
<pre>
<script>
document.writeln("Hello World!");
document.writeln("Have a nice day!");
</script>
</pre>

</body>
</html>
<!-- 输出如下：
注意write()方法不会在每个语句后面新增一行：

Hello World!Have a nice day!
注意writeln()方法在每个语句后面新增一行：

Hello World!
Have a nice day!
 -->
```

**定义和用法**

`write()` 方法可向文档写入 HTML 表达式或 JavaScript 代码。

`writeln()` 方法与 write() 方法作用相同，外加可在每个表达式后写一个换行符。

**语法**

`document.write(exp1,exp2,exp3,...)`

`document.writeln(exp1,exp2,exp3,...)`

|参数|描述|
|-|-|
|exp1,exp2,exp3,...|可选。要写入的输出流。多个参数可以列出，他们将按出现的顺序被追加到文档中|

* * * 

## cookie

```html
<html>
<body>

与此文档相关的Cookies: 
<script>
document.write(document.cookie);
</script>

</body>
</html>
```

**定义和用法**

`cookie` 属性返回当前文档所有 键/值 对的所有 cookies。

**语法**

`document.cookie`

* * * 

## createAttribute

```html
<style type="text/css">
.democlass{
	color:red;
}
</style>
</head>
<body>

<h1>Hello World</h1>
<p id="demo">单击按钮来创建一个“类”属性值“democlass”插入到上面的H1元素。</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var h1=document.getElementsByTagName("H1")[0];
	var att=document.createAttribute("class");
	att.value="democlass";
	h1.setAttributeNode(att);
}
</script>

</body>
```

**定义和用法**

`createAttribute()` 方法用于创建一个指定名称的属性，并返回Attr 对象属性。

**语法**

`document.createAttribute(attributename)`

**参数**

|参数|类型|描述|
|-|-|-|
|attributename|Attr object|必须。要创建的属性名称。|

**返回值**

|类型	|描述|
|-|-|
|节点对象	|创建的属性|

* * *

## createComment

```js
var c=document.createComment("My personal comments");
document.body.appendChild(c);
/*输出结果：
<!--My personal comments-->
*/
```

**定义和用法**

`createComment()` 方法可创建注释节点。

**语法**

`document.createComment(text)`

**参数**

|参数|类型|描述|
|-|-|-|
|text|String|可选. 添加的注释文本。|

**返回值**

|类型	|描述|
|-|-|
|Comment object|创建的注释节点|

* * * 

## createdocumentfragment

```html
<ul><li>Coffee</li><li>Tea</li></ul>
<p id="demo">单击按钮更改列表项,使用createDocumentFragment方法,然后在列表的最后一个孩子添加列表项。</p>
<button onclick="myFunction()">点我</button>
<script>
function myFunction(){
	var d=document.createDocumentFragment();
	d.appendChild(document.getElementsByTagName("LI")[0]);
	d.childNodes[0].childNodes[0].nodeValue="Milk";
	document.getElementsByTagName("UL")[0].appendChild(d);
};
<!-- 
输出结果：
修改前:
Coffee
Tea
修改后:
Tea
Milk
-->
```

**定义和用法**

`createdocumentfragment()`方法创建了一虚拟的节点对象，节点对象包含所有属性和方法。

当你想提取文档的一部分，改变，增加，或删除某些内容及插入到文档末尾可以使用createDocumentFragment() 方法。

你也可以使用文档的文档对象来执行这些变化，但要防止文件结构被破坏，createDocumentFragment() 方法可以更安全改变文档的结构及节点。

**语法**

`document.createDocumentFragment()`

* * * 

## createElementcreateTextNode

```js
var btn=document.createElement("BUTTON");
var t=document.createTextNode("CLICK ME");
btn.appendChild(t);
```

**定义和用法**

`createElement()` 方法通过指定名称创建一个元素

`createTextNode()` 可创建文本节点。

**语法**

`document.createElement(nodename)`

`document.createTextNode(text)`

**参数**

|参数|类型|描述|
|-|-|-|
|nodename|String|必须。创建元素的名称。|

|参数|类型|描述|
|-|-|-|
|text	|String	|必须。文本节点的文本。|

**返回值**

|类型	|描述|
|-|-|
|元素对象|创建的元素节点|

|类型	|描述|
|-|-|
|文本节点对象	|创建文本节点|

* * * 

## get

```js
// 获取包含 "example" 和 "color" 类名的所有元素
document.getElementsByClassName("example color");


// 返回指定 ID 为 demo 的元素
document.getElementById("demo");


// 返回带有指定名称的对象的集合
document.getElementsByName(name);


// 返回带有指定标签名 P 的对象的集合
document.getElementsByTagName("P");
```
```js
// 获取文档中第一个 <p> 元素：
document.querySelector("p");
// 获取文档中 id="demo" 的元素：
document.querySelector("#demo");
// 获取文档中 class="example" 的第一个元素:
document.querySelector(".example");
// 获取文档中 class="example" 的第一个 <p> 元素:
document.querySelector("p.example");
// 获取文档中有 "target" 属性的第一个 <a> 元素：
document.querySelector("a[target]");


// 以下实例演示了多个选择器的使用方法。

// 假定你选择了两个选择器: <h2> 和 <h3> 元素。
// 以下代码将为文档的第一个 <h2> 元素添加背景颜色：
<h2>A h2 element</h2>
<h3>A h3 element</h3>
document.querySelector("h2, h3").style.backgroundColor = "red";

// 但是，如果文档中 <h3> 元素位于 <h2> 元素之前，<h3> 元素将会被设置指定的背景颜色。
<h3>A h3 element</h3>
<h2>A h2 element</h2>
document.querySelector("h2, h3").style.backgroundColor = "red";
```
```js
// 获取文档中 class="example" 的所有元素:
document.querySelectorAll(".example");

// 获取文档中所有的 <p> 元素， 并为匹配的第一个 <p> 元素 (索引为 0) 设置背景颜色:
var x = document.querySelectorAll("p"); 
x[0].style.backgroundColor = "red";

// 获取文档中所有 class="example" 的 <p> 元素， 并为匹配的第一个 <p> 元素 (索引为 0) 设置背景颜色:
var x = document.querySelectorAll("p.example"); 
x[0].style.backgroundColor = "red";

// 计算文档中 class="example" 的 <p> 元素的数量（使用 NodeList 对象的 length 属性）:
document.querySelectorAll(".example").length;

// 设置文档中所有 class="example" 元素的背景颜色:
var x = document.querySelectorAll(".example");
var i;
for (i = 0; i < x.length; i++) {
    x[i].style.backgroundColor = "red";
}

// 设置文档中所有 <p> 元素的背景颜色：
var x = document.querySelectorAll(".example");
var i;
for (i = 0; i < x.length; i++) {
    x[i].style.backgroundColor = "red";
}

// 查找文档中共包含 "target" 属性的 <a> 标签，并为其设置边框:
var x = document.querySelectorAll("a[target]");
var i;
for (i = 0; i < x.length; i++) {
    x[i].style.border = "10px solid red";
}

// 查找每个父元素为 <div> 的 <p> 元素，并为其设置背景颜色:
var x = document.querySelectorAll("div > p");
var i;
for (i = 0; i < x.length; i++) {
    x[i].style.backgroundColor = "red";
}

// 给文档中所有的 <h2>, <div> 和 <span> 元素设置背景颜色：
var x = document.querySelectorAll("h2, div, span");
var i;
for (i = 0; i < x.length; i++) {
    x[i].style.backgroundColor = "red";
}
```

### 1getElementsByClassName

**定义和用法**

`getElementsByClassName()` 方法返回文档中所有指定类名的元素集合，作为 NodeList 对象。

NodeList 对象代表一个有顺序的节点列表。NodeList 对象 我们可通过节点列表中的节点索引号来访问列表中的节点(索引号由0开始)。

提示： 你可以使用 NodeList 对象的 length 属性来确定指定类名的元素个数，并循环各个元素来获取你需要的那个元素。

**语法**

`document.getElementsByClassName(classname)`

**参数值**

|参数|类型|描述|
|-|-|-|
|classname|String|必须。你需要获取的元素类名。 |

&hearts; 多个类名使用空格分隔，如 "test demo"。

**技术细节**

|||
|-|-|
|DOM 版本:|Selectors Level 1 Document Object|
|返回值:|NodeList 对象，表示指定类名的元素集合。元素在集合中的顺序以其在代码中的出现次序排序。|

### 2getElementById

**定义和用法**

`getElementById()` 方法可返回对拥有指定 ID 的第一个对象的引用。

HTML DOM 定义了多种查找元素的方法，除了 getElementById() 之外，还有 getElementsByName() 和 getElementsByTagName()。

如果没有指定 ID 的元素返回 null

如果存在多个指定ID的元素则返回 undefined。

**语法**

`document.getElementById(elementID)`

**参数值**

|参数|类型|描述|
|-|-|-|
|elementID|String|必须。元素ID属性值。|

**返回值**

|类型|描述|
|-|-|
|元素对象|指定ID的元素|

### 3getElementsByName

**定义和用法**

`getElementsByName()` 方法可返回带有指定名称的对象的集合。

**语法**

`document.getElementsByName(name)`

|参数|描述|
|-|-|
|name|必须。元素的名称。|

### 4getElementsByTagName

**定义和用法**

`getElementsByTagName()` 方法可返回带有指定标签名的对象的集合。

&hearts; 提示： 参数值 "*" 返回文档的所有元素。

**语法**

`document.getElementsByTagName(tagname)`

**参数值**

|参数|类型|描述|
|-|-|-|
|tagname|String|必须。你要获取元素的标签名。|

**返回值**

|参数|描述|
|-|-|
|NodeList 对象|指定标签名的元素集合|

### 5querySelector 

**定义和用法**

`querySelector()` 方法返回文档中匹配指定 CSS 选择器的一个元素。

&hearts; 注意： querySelector() 方法仅仅返回匹配指定选择器的第一个元素。如果你需要返回所有的元素，请使用 querySelectorAll() 方法替代。

更多 CSS 选择器，请访问我们的 CSS 选择器教程 和我们的 CSS 选择器参考手册。

**语法**

`document.querySelector(CSS selectors)`

**参数值**

|参数|类型|描述|
|-|-|-|
|CSS 选择器|String|必须。指定一个或多个匹配元素的 CSS 选择器。 可以使用它们的 id, 类, 类型, 属性, 属性值等来选取元素。|

对于多个选择器，使用逗号隔开，返回一个匹配的元素。

提示： 更多 CSS 选择器，请参阅我们的 CSS 选择器参考手册。

**技术细节**

|||
|-|-|
|DOM 版本:|Selectors Level 1 Document Object|
|返回值:|匹配指定 CSS 选择器的第一个元素。 如果没有找到，返回 null。如果指定了非法选择器则 抛出 SYNTAX_ERR 异常。|

### 6querySelectorAll

**定义和用法**

`querySelectorAll()` 方法返回文档中匹配指定 CSS 选择器的所有元素，返回 NodeList 对象。

NodeList 对象表示节点的集合。可以通过索引访问，索引值从 0 开始。

提示: 你可以使用 NodeList 对象的 length 属性来获取匹配选择器的元素属性，然后你可以遍历所有元素，从而获取你想要的信息。

更多 CSS 选择器可以参考 CSS 选择器教程 ， CSS 选择器参考手册。

**语法**

`elementList = document.querySelectorAll(selectors);`

elementList 是一个静态的 NodeList 类型的对象。
selectors 是一个由逗号连接的包含一个或多个 CSS 选择器的字符串。

**参数值**

|参数|类型|描述|
|-|-|-|
|CSS 选择器|String|必须。 指定一个或多个匹配 CSS 选择器的元素。可以通过 id, class, 类型, 属性, 属性值等作为选择器来获取元素。 |

多个选择器使用逗号(,)分隔。

提示: CSS 选择器更多内容可以参考 CSS 选择器参考手册。

**方法**

|||
|-|-|
|DOM 版本:|Selectors Level 1 Document Object|
|返回值:|一个 NodeList 对象，表示文档中匹配指定 CSS 选择器的所有元素。 NodeList 是一个静态的 NodeList 类型的对象。如果指定的选择器不合法，则抛出一个 SYNTAX_ERR 异常。|


