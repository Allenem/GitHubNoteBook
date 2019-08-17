# Window对象

Window 对象表示浏览器中打开的窗口。

如果文档包含框架（\<frame> 或 \<iframe> 标签），浏览器会为 HTML 文档创建一个 window 对象，并为每个框架创建一个额外的 window 对象。

![Note](https://upload-images.jianshu.io/upload_images/7728717-c55ac7b6006f6f63.gif?imageMogr2/auto-orient/strip) **注意：** 没有应用于 window 对象的公开标准，不过所有浏览器都支持该对象。

* * *
## CONTENT

### Window 对象属性

| 属性 | 描述 |
|-|-|
| [closed](#closed) | 返回窗口是否已被关闭。 |
| [defaultStatus](#defaultStatus) | 设置或返回窗口状态栏中的默认文本。 |
| [document](../../DOM/Document对象.md) | 对 Document 对象的只读引用。(请参阅[对象](../../DOM/Document对象.md)) |
| [frames](#frameslength) | 返回窗口中所有命名的框架。该集合是 Window 对象的数组，每个 Window 对象在窗口中含有一个框架。 |
| [length](frameslength) | 设置或返回窗口中的框架数量。 |
| [history](./History对象.md) | 对 History 对象的只读引用。请参数 [History 对象](./History对象.md)。 |
| [innerHeight](#innerHeightinnerWidthouterHeightouterWidth) | 返回窗口的文档显示区的高度。 |
| [innerWidth](#innerHeightinnerWidthouterHeightouterWidth) | 返回窗口的文档显示区的宽度。 |
| [outerHeight](#innerHeightinnerWidthouterHeightouterWidth) | 返回窗口的外部高度，包含工具条与滚动条。 |
| [outerWidth](#innerHeightinnerWidthouterHeightouterWidth) | 返回窗口的外部宽度，包含工具条与滚动条。 |
| [localStorage](./存储对象.md) | 在浏览器中存储 key/value 对。没有过期时间。 |
| [location](./Location对象.md) | 用于窗口或框架的 Location 对象。请参阅 [Location 对象](./Location对象.md)。 |
| [name](#name) | 设置或返回窗口的名称。 |
| [navigator](./Navigator对象.md) | 对 Navigator 对象的只读引用。请参数 [Navigator 对象](./Navigator对象.md)。 |
| [opener](#openr) | 返回对创建此窗口的窗口的引用。 |
| [pageXOffset](#pagexoffsetpageyoffset) | 设置或返回当前页面相对于窗口显示区左上角的 X 位置。 |
| [pageYOffset](#pagexoffsetpageyoffset) | 设置或返回当前页面相对于窗口显示区左上角的 Y 位置。 |
| [screenX](#screenxscreeny) | 返回相对于屏幕窗口的x坐标 |
| [screenY](#screenxscreeny) | 返回相对于屏幕窗口的y坐标 |
| [parent](#parent) | 返回父窗口。 |
| [screen](./Screen对象.md) | 对 Screen 对象的只读引用。请参数 [Screen 对象](./Screen对象.md)。 |
| [screenLeft](#screenleftscreentop) | 返回相对于屏幕窗口的x坐标 |
| [screenTop](#screenleftscreentop) | 返回相对于屏幕窗口的y坐标 |
| [sessionStorage](./存储对象.md) | 在浏览器中存储 key/value 对。 在关闭窗口或标签页之后将会删除这些数据。 |
| [self](#selftop) | 返回对当前窗口的引用。等价于 Window 属性。 |
| [top](#selftop) | 返回最顶层的父窗口。 |
| [status](#status) | 设置窗口状态栏的文本。 |

### Window 对象方法

| 方法 | 描述 |
|-|-|
| alert() | 显示带有一段消息和一个确认按钮的警告框。 |
| [atob()](#atobbtoa) | 解码一个 base-64 编码的字符串。 |
| [btoa()](#atobbtoa) | 创建一个 base-64 编码的字符串。 |
| [blur()](https://www.runoob.com/jsref/met-win-blur.html) | 把键盘焦点从顶层窗口移开。 |
| [setInterval()](#setclear) | 按照指定的周期（以毫秒计）来调用函数或计算表达式。 |
| [setTimeout()](#setclear) | 在指定的毫秒数后调用函数或计算表达式。 |
| [clearInterval()](#setclear) | 取消由 setInterval() 设置的 timeout。 |
| [clearTimeout()](#setclear) | 取消由 setTimeout() 方法设置的 timeout。 |
| [close()](#close) | 关闭浏览器窗口。 |
| [confirm()](#confirm) | 显示带有一段消息以及确认按钮和取消按钮的对话框。 |
| createPopup()| 创建一个 pop-up 窗口。**只有 IE 浏览器支持 createPopup() 方法，其他浏览器都不支持。** |
| [focus()](#focus) | 把键盘焦点给予一个窗口。 |
| getSelection() | 返回一个 Selection 对象，表示用户选择的文本范围或光标的当前位置。 |
| [getComputedStyle()](#getcomputedstyle) | 获取指定元素的 CSS 样式。 |
| [matchMedia()](#matchmedia) | 该方法用来检查 media query 语句，它返回一个 MediaQueryList对象。 |
| [moveBy()](#movebymoveto) | 可相对窗口的当前坐标把它移动指定的像素。 |
| [moveTo()](#movebymoveto) | 把窗口的左上角移动到一个指定的坐标。 |
| [open()](#open) | 打开一个新的浏览器窗口或查找一个已命名的窗口。 |
| [print()](#print) | 打印当前窗口的内容。 |
| [prompt()](#prompt) | 显示可提示用户输入的对话框。 |
| [resizeBy()](#resizebyto) | 按照指定的像素调整窗口的大小。 |
| [resizeTo()](#resizebyto) | 把窗口的大小调整到指定的宽度和高度。 |
| scroll() | 已废弃。 该方法已经使用了 [scrollTo()](#scrollbyto) 方法来替代。 |
| [scrollBy()](#scrollbyto) | 按照指定的像素值来滚动内容。 |
| [scrollTo()](#scrollbyto) | 把内容滚动到指定的坐标。 |
| [stop()](#stop) | 停止页面载入。 |

***

## Window 对象属性

### closed
```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
<script>
var myWindow;
function openWin(){
	myWindow=window.open("","","width=400,height=200");
}
function closeWin(){
	if (myWindow){
		myWindow.close();
	}
}
function checkWin(){
	if (!myWindow){
		document.getElementById("msg").innerHTML="我的窗口没有被打开!";
	}
	else{
		if (myWindow.closed){
			document.getElementById("msg").innerHTML="我的窗口被关闭!";
		}
		else{
			document.getElementById("msg").innerHTML="我的窗口没有被关闭!";
		}
	}	
}
</script>
</head>
<body>

<input type="button" value="打开我的窗口" onclick="openWin()" />
<input type="button" value="关闭我的窗口" onclick="closeWin()" />
<br><br>
<input type="button" value="我的窗口被关闭了吗?" onclick="checkWin()" />
<br><br>
<div id="msg"></div>
```

**语法**

`window.closed`

### defaultStatus
```html
<html>
<body>

<script>
  window.defaultStatus="这是默认状态栏文本! !";
</script>

</body>
</html>
```

`defaultStatus` 属性可设置或返回窗口状态栏中的默认文本。该属性可读可写。

该文本会在页面加载时被显示。

**语法**

`window.defaultStatus`

**浏览器支持**

Safari

&hearts; 注意： defaultStatus属性在IE，火狐，Chrome，和Safari默认配置是不能正常工作。要允许脚本来改变状态栏文本，用户必须把配置屏幕首选项设置为false dom.disable_window_status_change。（或在Firefox："工具 - 选项 - 内容 - 启用的JavaScript /"高级" - 允许脚本更改状态栏文本"）。


### frameslength
```html
<!-- 在页面中查找所有框架的数量，然后修改 iframe 元素的 src 属性为 "https://www.runoob.com": -->

<button onclick="myFunction()">点我</button>
<br><br>

<iframe src="https://www.baidu.com"></iframe>
<iframe src="https://www.taobao.com"></iframe>
<iframe src="https://c.runoob.com"></iframe>

<script>
function myFunction() {
    var frames = window.frames;
    var i;

    for (i = 0; i < frames.length; i++) {
        frames[i].location = "https://www.runoob.com";
    }
}
</script>
```

`frames` 属性返回窗口中所有命名的框架。

该集合是 Window 对象的数组，每个 Window 对象在窗口中含有一个框架或 `<iframe>`。属性 frames.length 存放数组 frames[] 中含有的元素个数。注意，frames[] 数组中引用的框架可能还包括框架，它们自己也具有 frames[] 数组。

&hearts; 提示： 使用 `frames.length` 来获取框架的数量。

&hearts; 注意:该属性也可用于 `<frame>` 元素，但是 HTML5 不支持 `<frame>` 元素。

该属性是只读的。

**语法**

`window.frames`

### innerHeightinnerWidthouterHeightouterWidth

```js
var w1=window.innerWidth;
var h1=window.innerHeight;
var w2=window.outerWidth;
var h2=window.outerHeight;
console.log("innerWidth: " + w1 + " innerHeight: " + h1 +"outerWidth: " + w2 + " outerHeight: " + h2)
// innerWidth: 1050 innerHeight: 969outerWidth: 1920 outerHeight: 1040
```

**定义和用法**

`innerheight`	返回窗口的文档显示区的高度。

`innerwidth`	返回窗口的文档显示区的宽度。

`outerHeight` 属性设置或返回一个窗口的外部高度，包括所有界面元素（如工具栏/滚动条）。

`outerWidth` 属性设置或返回窗口的外部宽度，包括所有的界面元素（如工具栏/滚动）。

&hearts; 注意： 使用 `innerWidth` 和 `innerHeight` 属性获取去除工具条与滚动条的窗口高度与宽度。

&hearts; 注意：使用 `outerWidth` 和 `outerHeight` 属性获取加上工具条与滚动条窗口的宽度与高度。

**语法**

Get:

`window.innerWidth`

`window.innerHeight`

`window.outerWidth`

`window.outerHeight`

Set:

`window.innerWidth=pixels`

`window.innerHeight=pixels`

`window.outerWidth=pixels`

`window.outerHeight=pixels`

### name

```js
myWindow=window.open('','MsgWindow','width=200,height=100');
myWindow.document.write("<p>窗口名称为: " + myWindow.name + "</p>");
// 窗口名称为: MsgWindow
```

**定义和用法**

`name` 属性可设置或返回存放窗口的名称的一个字符串。

**语法**

`window.name`

### openr

```js
myWindow=window.open('','hhh','width=200,height=100');
myWindow.document.write("<p>这是我的窗口</p>");          // 新窗口：这是我的窗口
myWindow.focus();
myWindow.opener.document.write("<p>这个是源窗口!</p>");  // 源窗口：这个是源窗口!
```

**定义和用法**

`opener` 属性是一个可读可写的属性，可返回对创建该窗口的 Window 对象的引用。

当使用window.open()打开一个窗口，您可以使用此属性返回来自目标窗口源（父）窗口的详细信息。

代码提示： `window.opener.close()` 将关闭源（父）窗口。

**语法**

`window.opener`

### pagexoffsetpageyoffset
```js
window.scrollBy(100, 100);
alert("pageXOffset: " + window.pageXOffset + ", pageYOffset: " + window.pageYOffset);
// pageXOffset: 100, pageYOffset: 100
```

**定义和用法**

`pageXOffset` 和 `pageYOffset` 属性返回文档在窗口左上角水平和垂直方向滚动的像素。

`pageXOffset` 设置或返回当前页面相对于窗口显示区左上角的 X 位置。pageYOffset 设置或返回当前页面相对于窗口显示区左上角的 Y 位置。

`pageXOffset` 和 `pageYOffset` 属性相等于 `scrollX` 和 `scrollY` 属性。

这些属性是只读的。


**语法**

`window.pageXOffset`

`window.pageYOffset`

### screenxscreeny
```js
myWindow=window.open('','');
myWindow.document.write("<p>This is 'myWindow'");
myWindow.document.write("<br>ScreenX: " + myWindow.screenX);
myWindow.document.write("<br>ScreenY: " + myWindow.screenY + "</p>");
```

**定义和用法**

`screenX` 和 `screenY` 属性返回窗口相对于屏幕的X和Y坐标。

**语法**

`window.screenX`

`window.screenY`

浏览器支持
Internet ExplorerFirefoxOperaGoogle ChromeSafari

除了 Internet Explorer外，所有主要浏览器都支持screenX和screenY属性。

&hearts; 注意： IE浏览器使用。 `window.screenLeft` 和 `window.screenTop` 获得相同的值

### parent
```js
var newwin = window.open('','','width=200,height=100');
alert(window.parent.location);
// https://www.runoob.com/try/try.php?filename=tryjsref_win_parent
```

**定义和用法**

`parent` 属性返回当前窗口的父窗口。

**语法**

`window.parent`

### screenleftscreentop
```js
myWindow=window.open('','');
myWindow.document.write("<p>这是'我的窗口'");
myWindow.document.write("<br>ScreenLeft: " + myWindow.screenLeft);
myWindow.document.write("<br>ScreenTop: " + myWindow.screenTop + "</p>");
/*
这是'我的窗口'
ScreenLeft: 0
ScreenTop: 0
*/
```

**定义和用法**

`screenLeft` 和 `screenTop` 属性返回窗口相对于屏幕的X和Y坐标。

**语法**

`window.screenLeft`
`window.screenTop`

**浏览器支持**

所有主流浏览器都支持 `screenLeft` 和 `screenTop` 属性，Firefox除外。

&hearts; 注意： Firefox 浏览器请使用 `window.screenX` and `window.screenY`。

### selftop
```html
<script>
function check(){
	if (window.top!=window.self) {
		document.write("<p>这个窗口不是最顶层窗口!我在一个框架?</p>")
	}
	else{ 
		document.write("<p>这个窗口是最顶层窗口!</p>")
	} 
}
</script>
	
<input type="button" onclick="check()" value="检查窗口">

<!-- 这个窗口不是最顶层窗口!我在一个框架? -->
```

**定义和用法**

`self` 属性返回指向当前 window 对象的引用，利用这个属性，可以保证在多个窗口被打开的情况下，正确调用当前窗口内的函数或属性而不会发生混乱。

`self` 属性是只读的。

`top` 属性返回当前窗口的最顶层浏览器窗口。

**语法**

`window.self`

`window.top`

&hearts; 注： `window` 、 `self` 、 `window.self` 是等价的。

### status
```js
window.status="一些文本在状态栏!";
```

**定义和用法**

`status` 属性可设置或返回窗口状态栏中的文本。

**语法**

`window.status`

**浏览器支持**

&hearts; 注意： `status` 属性在IE，火狐，Chrome，和Safari默认配置是不能正常工作。要允许脚本来改变状态栏文本，用户必须把配置屏幕首选项设置为false dom.disable_window_status_change。（或在Firefox："工具 - 选项 - 内容 - 启用的JavaScript /"高级" - 允许脚本更改状态栏文本"）。

## Window对象方法

### atobbtoa

```js
var str = "RUNOOB";
var enc = window.btoa(str);  // 编码字符串为: UlVOT09C
var dec = window.atob(enc);  // 解码后字符串为: RUNOOB
```

**定义和用法**

`atob()` 方法用于解码使用 base-64 编码的字符串。

`btoa()` 方法用于创建一个 base-64 编码的字符串。

该方法使用 "A-Z", "a-z", "0-9", "+", "/" 和 "=" 字符来编码字符串。

**语法**

`window.atob(encodedStr)`

`window.btoa(str)`

### setclear

```html
<p>显示当前时间:</p>

<p id="demo"></p>

<button onclick="myStopFunction()">停止时间</button>

<script>
var myVar = setInterval(function(){ myTimer() }, 1000);

function myTimer() {
    var d = new Date();
    var t = d.toLocaleTimeString();
    document.getElementById("demo").innerHTML = t;
}

function myStopFunction() {
    clearInterval(myVar);
}
</script>
```

```html
<body>

<p>点击按钮，等待 3 秒后弹出 "Hello" 。</p>
<p>点击第二个按钮来阻止弹出函数 myFunction 的执行。 (你必须在 3 秒前点击)</p>

<button onclick="myFunction()">先点我</button>
<button onclick="myStopFunction()">阻止弹出</button>

<script>
var myVar;

function myFunction() {
    myVar = setTimeout(function(){ alert("Hello") }, 3000);
}

function myStopFunction() {
    clearTimeout(myVar);
}
</script>

</body>
```

**定义和用法**

①

`setInterval()` 方法可按照指定的周期（以毫秒计）来调用函数或计算表达式。

`setInterval()` 方法会不停地调用函数，直到 clearInterval() 被调用或窗口被关闭。由 setInterval() 返回的 ID 值可用作 clearInterval() 方法的参数。

&hearts; 提示： 1000 毫秒= 1 秒。

&hearts; 提示： 如果你只想执行一次可以使用 [setTimeout()](https://www.runoob.com/jsref/met-win-settimeout.html) 方法。

②

`clearInterval()` 方法可取消由 setInterval() 函数设定的定时执行操作。

`clearInterval()` 方法的参数必须是由 setInterval() 返回的 ID 值。

注意: 要使用 clearInterval() 方法, 在创建执行定时操作时要使用全局变量：

myVar = setInterval("javascript 函数", milliseconds);

可以通过 clearInterval(myVar) 方法来停止执行。

③

`setTimeout()` 方法用于在指定的毫秒数后调用函数或计算表达式。

&hearts; 提示： 1000 毫秒= 1 秒。

&hearts; 提示： 如果你只想重复执行可以使用 setInterval() 方法。

&hearts; 提示： 使用 clearTimeout() 方法来阻止函数的执行。

④

clearTimeout() 方法可取消由 setTimeout() 方法设置的定时操作。

clearTimeout() 方法的参数必须是由 setTimeout() 返回的 ID 值。

&hearts; 注意: 要使用 clearTimeout() 方法, 在创建执行定时操作时要使用全局变量：

myVar = setTimeout("javascript function", milliseconds);

**语法**

①

`setInterval(code, milliseconds);`

`setInterval(function, milliseconds, param1, param2,  ...)`

| 参数 | 描述 |
|-|-|
| code/function | 必需。要调用一个代码串，也可以是一个函数。 |
| milliseconds | 必须。周期性执行或调用 code/function 之间的时间间隔，以毫秒计。 |
| param1, param2, ... | 可选。 传给执行函数的其他参数（IE9 及其更早版本不支持该参数）。 |

②

`clearInterval(id_of_setinterval)`

| 参数 | 描述 |
|-|-|
|id_of_setinterval|调用 setInterval() 函数时所获得的返回值，使用该返回标识符作为参数，可以取消该 setInterval() 所设定的定时执行操作。|

③

`setTimeout(code, milliseconds, param1, param2, ...)`

`setTimeout(function, milliseconds, param1, param2, ...)`

| 参数 | 描述 |
|-|-|
|code/function|必需。要调用一个代码串，也可以是一个函数。|
|milliseconds|可选。执行或调用 code/function 需要等待的时间，以毫秒计。默认为 0。|
|param1, param2, ...|可选。 传给执行函数的其他参数（IE9 及其更早版本不支持该参数）。|

④

`clearTimeout(id_of_settimeout)`

| 参数 | 描述 |
|-|-|
|id_of_setinterval|调用 setTimeout() 函数时所获得的返回值，使用该返回标识符作为参数，可以取消该 setTimeout() 所设定的定时执行操作。|

### close
```html
<script>
function openWin(){
	myWindow=window.open("","","width=200,height=100");
	myWindow.document.write("<p>这是'我的窗口'</p>");
}
function closeWin(){
	myWindow.close();
}
</script>
</head>
<body>

<input type="button" value="打开我的窗口" onclick="openWin()" />
<input type="button" value="关闭我的窗口" onclick="closeWin()" />

</body>
```

### confirm
```html
<body>

<p>点击按钮，显示确认框。</p>
<button onclick="myFunction()">点我</button>
<p id="demo"></p>
<script>
function myFunction(){
	var x;
	var r=confirm("按下按钮!");
	if (r==true){
		x="你按下了\"确定\"按钮!";
	}
	else{
		x="你按下了\"取消\"按钮!";
	}
	document.getElementById("demo").innerHTML=x;
}
</script>

</body>
```

**定义和用法**

`confirm()` 方法用于显示一个带有指定消息和确认及取消按钮的对话框。

如果访问者点击"确定"，此方法返回true，否则返回false。

**语法**

`confirm(message)`

### focus
```html
<script>
function openWin(){
    myWindow=window.open('','','width=200,height=100');
    myWindow.document.write("<p>这是'我的窗口'</p>");
    myWindow.focus();
}
</script>
<body>

<input type="button" value="打开窗口" onclick="openWin()" />

</body>
```

**定义和用法**

`focus()` 方法可把键盘焦点给予一个窗口。

**语法**

`window.focus()`

### getcomputedstyle
```html
<p>点击按钮计算 DIV 的背景颜色。</p>
<p><button onclick="myFunction()">点我</button></p>
<div id="test" style="height: 50px;background-color: rgb(178, 116, 230);">测试 DIV</div>
<p>计算值为: <span id="demo"></span></p>

<script>
function myFunction(){
    var elem = document.getElementById("test");
    var theCSSprop = window.getComputedStyle(elem, null).getPropertyValue("background-color");
    document.getElementById("demo").innerHTML = theCSSprop;
}
```

**定义和用法**

`getComputedStyle()` 方法用于获取指定元素的 CSS 样式。

获取的样式是元素在浏览器中最终渲染效果的样式。

**语法**

`window.getComputedStyle(element, pseudoElement)`

|参数|说明|
|-|-|
|element|必需，要获取样式的元素。|
|pseudoElement|可选，伪类元素，当不查询伪类元素的时候可以忽略或者传入 null。|

**返回值**

返回的对象是 CSSStyleDeclaration 类型的对象。 

### matchmedia
```html
<p>判断屏幕（screen/viewport）窗口大小。</p>

<button onclick="myFunction()">点我</button>

<p id="demo"></p>

<script>
function myFunction() {
    var x = document.getElementById("demo");
    if (window.matchMedia("(max-width: 700px)").matches) {
        x.innerHTML = "窗口小于或等于 700 像素";
    } else {
        x.innerHTML = "窗口大于 700 像素";
    }
}
</script>
```

**定义和用法**

`matchMedia()` 返回一个新的 MediaQueryList 对象，表示指定的媒体查询字符串解析后的结果。

`matchMedia()` 方法的值可以是任何一个 CSS @media 规则 的特性, 如 min-height, min-width, orientation 等。

MediaQueryList 对象有以下两个属性：

`media`：查询语句的内容。

`matches`：用于检测查询结果，如果文档匹配 media query 列表，值为 true，否则为 false。
MediaQueryList 对象还可以监听事件。通过监听，在查询结果发生变化时，就调用指定的回调函数。

|方法|描述|
|-|-|
|addListener(functionref)|添加一个新的监听器函数，该函数在媒体查询的结果发生变化时执行。|
|removeListener(functionref)|从媒体查询列表中删除之前添加的监听器。如果指定的监听器不在列表中，则不执行任何操作。|

**语法**

`window.matchMedia(mediaQueryString)`

|参数|说明|
|-|-|
|mediaQueryString|必需，一个字符串，表示即将返回一个新 MediaQueryList 对象的媒体查询。|

**返回值**


返回 MediaQueryList 对象。 

### movebymoveto

```html
<script>
function openWin(){
	myWindow=window.open('','我的窗口','width=200,height=100');
	myWindow.document.write("<p>这是我的窗口</p>");
}
function movebyWin(){
	myWindow.moveBy(250,250);    // 相对移动
	myWindow.focus();
}
function movetoWin(){
	myWindow.moveTo(100,100);    // 移到指定位置
	myWindow.focus();
}
</script>

<body>

<input type="button" value="打开我的窗口" onclick="openWin()" />
<br><br>
<input type="button" value="移动我的窗口" onclick="movebyWin()" />
<input type="button" value="移动我的窗口" onclick="movetoWin()" />

</body>
```

**定义和用法**

`moveBy()` 方法可相对窗口的当前坐标把它移动指定的像素。

`moveTo()` 方法可把窗口的左上角移动到一个指定的坐标。

**语法**

`window.moveBy(x,y)`

`window.moveTo(x,y)`

### open

```js
myWindow=window.open('','MsgWindow','width=200,height=100');
myWindow.document.write("<p>窗口名称为: " + myWindow.name + "</p>");
// 窗口名称为: MsgWindow
```

**定义和用法**

`open()` 方法用于打开一个新的浏览器窗口或查找一个已命名的窗口。

**语法**

`window.open(URL,name,specs,replace)`

| 参数 | 说明 | |
|-|-|-|
| URL | 可选。打开指定的页面的URL。如果没有指定URL，打开一个新的空白窗口 |
| name | 可选。指定target属性或窗口的名称。支持以下值：|
| |*   _blank - URL加载到一个新的窗口。这是默认
| |*   _parent - URL加载到父框架
| |*   _self - URL替换当前页面
| |*   _top - URL替换任何可加载的框架集
| |*   *name* - 窗口名称
| specs | 可选。一个逗号分隔的项目列表。支持以下值：
| | channelmode=yes| 是否要在影院模式显示 window。默认是没有的。仅限IE浏览器 |
| | directories=yes| 是否添加目录按钮。默认是肯定的。仅限IE浏览器 |
| | fullscreen=yes| 浏览器是否显示全屏模式。默认是没有的。在全屏模式下的 window，还必须在影院模式。仅限IE浏览器 |
| | height=pixels | 窗口的高度。最小.值为100 |
| | left=pixels | 该窗口的左侧位置 |
| | location=yes| 是否显示地址字段.默认值是yes |
| | menubar=yes| 是否显示菜单栏.默认值是yes |
| | resizable=yes| 是否可调整窗口大小.默认值是yes |
| | scrollbars=yes| 是否显示滚动条.默认值是yes |
| | status=yes| 是否要添加一个状态栏.默认值是yes |
| | titlebar=yes| 是否显示标题栏.被忽略，除非调用HTML应用程序或一个值得信赖的对话框.默认值是yes |
| | toolbar=yes| 是否显示浏览器工具栏.默认值是yes |
| | top=pixels | 窗口顶部的位置.仅限IE浏览器 |
| | width=pixels | 窗口的宽度.最小.值为100 |
| replace | Optional.Specifies规定了装载到窗口的 URL 是在窗口的浏览历史中创建一个新条目，还是替换浏览历史中的当前条目。支持下面的值：
| | *   true - URL 替换浏览历史中的当前条目。
| | *   false - URL 在浏览历史中创建新的条目。

### print
```js
// 打印当前页：
function printpage(){
    window.print();
}
```

**定义和用法**

`print()` 方法用于打印当前窗口的内容。

**语法**

`window.print()`

### prompt
```html
<body>

<p>点击按钮查看输入的对话框。</p>
<button onclick="myFunction()">点我</button>
<p id="demo"></p>
<script>
function myFunction(){
	var x;
	var person=prompt("请输入你的名字","Harry Potter");
	if (person!=null && person!=""){
	    x="你好 " + person + "! 今天感觉如何?";
	    document.getElementById("demo").innerHTML=x;
	}
}
</script>

</body>
```

**定义和用法**

`prompt()` 方法用于显示可提示用户进行输入的对话框。

这个方法返回用户输入的字符串。

**语法**

`prompt(msg,defaultText)`

| 参数 | 描述 |
|-|-|
|msg|可选。要在对话框中显示的纯文本（而不是 HTML 格式的文本）。|
|defaultText|可选。默认的输入文本。|

### resizebyto

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="utf-8">
<title>菜鸟教程(runoob.com)</title>
<script>
var w;
function openwindow(){
	w=window.open('','', 'width=100,height=100');
	w.focus();
}
function resizeWindow(){
	w.top.resizeBy(100,100);
}
function myFunction(){
	w.resizeTo(500,500);
	w.focus();
}
	
</script>
</head>
<body>

<button onclick="openwindow()">创建窗口</button>
<button onclick="resizeWindow()">调整窗口</button>
<button onclick="myFunction()">调整窗口</button>

</body>
</html>
```


**定义和用法**

`resizeBy()` 方法用于根据指定的像素来调整窗口的大小。

&hearts; 注意： 此方法定义指定窗口的右下角角落移动的像素，左上角将不会被移动(它停留在其原来的坐标).

`resizeTo` 方法用于把窗口大小调整为指定的宽度和高度。

**语法**

`resizeBy(width,height)`

| 参数 | 描述 |
|-|-|
|width|必需。要使窗口宽度增加的像素数。可以是正、负数值。|
|height|可选。要使窗口高度增加的像素数。可以是正、负数值。|

`window.resizeTo(width,height)`

| 参数 | 说明 |
|-|-|
|width|必需的。设置窗口的宽度，以像素为单位|
|height|必需的。设置窗口的高度，以像素为单位|

**浏览器支持**

所有主要浏览器都支持 `resizeBy()` 方法，除了Opera和Chrome。

所有主要浏览器都支持 `resizeTo()` 方法

从 Firefox 7 开始，不能改变浏览器窗口的大小了，要依据下面的规则：

不能设置那些不是通过 window.open 创建的窗口或 Tab 的大小。

当一个窗口里面含有一个以上的 Tab 时，无法设置窗口的大小。

### scrollbyto

```html
<script>
function scrollByWindow(){
	window.scrollBy(100,100);
}
function scrollToWindow(){
	window.scrollTo(100,100);
}
</script>

<body>
<input type="button" onclick="scrollByWindow()" value="滚动条" />
<input type="button" onclick="scrollToWindow()" value="滚动条" />

<p>滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 </p>
<br><br><br><br><br><br><br><br>
<p>滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 </p>
<br><br><br><br><br><br><br><br>
<p>滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 </p>
<br><br><br><br><br><br><br><br>
<p>滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 </p>
<br><br><br><br><br><br><br><br>
<p>滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 </p>
<br><br><br><br><br><br><br><br>
<p>滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 </p>
<br><br><br><br><br><br><br><br>
<p>滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 </p>
<br><br><br><br><br><br><br><br>
<p>滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 滚动 </p>
<br><br><br><br><br><br><br><br>

</body>
```

**定义和用法**

`scrollBy()` 方法可把内容滚动指定的像素数。

`scrollTo()` 方法可把内容滚动到指定的坐标。

&hearts; 注意： 要使此方法工作 window 滚动条的可见属性必须设置为true！

**语法**

`scrollBy(xnum,ynum)`

| 参数 | 描述 |
|-|-|
|xnum|必需。把文档向右滚动的像素数。|
|ynum|必需。把文档向下滚动的像素数。|

`scrollTo(xpos,ypos)`

| 参数 | 描述 |
|-|-|
|xpos|必需。要在窗口文档显示区左上角显示的文档的 x 坐标。|
|ypos|必需。要在窗口文档显示区左上角显示的文档的 y 坐标。|

### stop

```html
<!DOCTYPE html>
<html>
<head>
	<meta charset="utf-8">
	<title>菜鸟教程(runoob.com)</title>
	<script>
		window.stop();
	</script>
</head>
<body>

<p>stop() 方法阻止了 iframe 页面的载入。</p>
<p><b>注意:</b> Internet Explorer 浏览器不支持该方法。</p>

<iframe src="https://www.runoob.com"></iframe>

</body>
</html>
```

**定义和用法**

`stop()` 方法用于停止页面载入。

该方法类似在浏览器上点击停止载入按钮。

如果页面在载入图片或框架(iframe)时间过长，我门可以使用该方法来停止载入。

没有返回值。

**语法**

`window.stop()`
