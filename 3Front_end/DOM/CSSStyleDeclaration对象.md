# CSSStyleDeclaration对象

CSSStyleDeclaration 对象表示一个 CSS 属性-值（property-value）对的集合。

## CONTENT

### CSSStyleDeclaration 对象属性

|属性|描述|
|-|-|
|[cssText](#cssText)|设置或返回样式声明文本，cssText 对应的是 HTML 元素的 style 属性。|
|[length](#length)|返回样式中包含多少条声明。|
|[parentRule](#parentRule)|返回包含当前规则的规则。|

### CSSStyleDeclaration 对象方法

|方法|描述|
|-|-|
|[getPropertyPriority()](#getPropertyPrioritygetPropertyValue)|返回指定的 CSS 属性是否设置了 "important!" 属性。|
|[getPropertyValue()](#getPropertyPrioritygetPropertyValue)|返回指定的 CSS 属性值。|
|[item()](#item)|通过索引方式返回 CSS 声明中的 CSS 属性名。|
|[removeProperty()](#removePropertysetProperty)|移除 CSS 声明中的 CSS 属性。|
|[setProperty()](#removePropertysetProperty)|在 CSS 声明块中新建或者修改 CSS 属性。|

* * * 

## cssText
```html
<!-- 返回属性 -->
<body>

<h1 style="color: red; font-size:50px;">cssText 属性</h1>

<p>点击按钮返回元素的内联样式。</p>

<button onclick="myFunction()">点我</button>

<p id="demo"></p>
<!-- color: red; font-size:50px; -->

<script>
function myFunction() {
  var elmnt = document.getElementsByTagName("h1")[0];
  var x = elmnt.style.cssText;
  document.getElementById("demo").innerHTML = x;
}
</script>

</body>
```

```html
<!-- 设置属性 -->
<body>

<h1 style="color:red; font-size: 50px">cssText 属性</h1>

<p>点击按钮设置 h1 元素的内联样式。</p>

<button onclick="myFunction()">点我</button>

<p><strong>注意:</strong> 内联样式会被全部覆盖，字体大小不再是 50px。</p>

<script>
function myFunction() {
  var elmnt = document.getElementsByTagName("h1")[0];
  elmnt.style.cssText = "color: blue;";
}
</script>

</body>
```

**定义和使用**

`cssText` 属性用于设置或者返回元素声明的内联样式。

**语法**

返回 cssText 属性：

`element.style.cssText`

设置 cssText 属性：

`element.style.cssText = style`

* * * 

## length

```html
<body>

<h1 style="color: red; font-size: 50px;  ">循环输出所有 CSS 属性</h1>

<p>点击按钮显示所有 h1 元素的 CSS 属性。</p>

<button onclick="myFunction()">点我</button>

<p id="demo"></p>

<script>
function myFunction() {
  var elmnt, i, txt = "";
  elmnt = document.getElementsByTagName("h1")[0];
  for (i = 0; i < elmnt.style.length; i++) {
    txt += elmnt.style.item(i) + "<br>";
  }
  document.getElementById("demo").innerHTML += txt;
}
</script>

</body>
```

**定义和使用**

`length` 属性返回指定元素的样式声明数目。

**语法**

返回 length 属性：

`element.style.length`

返回值:	整数，表示 CSS 声明的数目

* * * 

## parentRule

```html
<style>
h1 {
  color: red;
  font-size: 50px;
}
</style>

<script>
function myFunction() {
  var s = document.styleSheets[0].rules[0].style;
  var ruleObj = s.parentRule;
  document.getElementById("demo").innerHTML = ruleObj.cssText;
}
</script> 
</head>
<body>

<h1>parentRule 属性</h1>

<p>parentRule 属性返回 CSSRule 对象，包含 CSS 选择器及声明的样式。 </p>

<button onclick="myFunction()">显示 CSS 样式</button>

<p id="demo"></p>
<!-- h1 { color: red; font-size: 50px; } -->

</body>
```

**定义和使用**

`parentRule` 属性返回 CSSRule 对象，包含 CSS 声明的样式及选择器。

**语法**

返回 parentRule 属性：

`object.parentRule`

* * * 

## getPropertyPrioritygetPropertyValue

```html
<style>
#ex1 {
  color: red !important;
}
</style>
</head>
<body>
<h1>getPropertyPriority() 属性</h1>

<p>点击按钮返回 color 属性是否设置了 "important!" 优先级</p>

<button onclick="myFunction()">点我</button>

<div id="ex1">一些文本</div>

<script>
function myFunction() {
  var declaration = document.styleSheets[0].cssRules[0].style;
  var priority = declaration.getPropertyPriority("color");
  var propvalue = declaration.getPropertyValue("color");
  alert(priority);   // important,没设置则返回空null
  alert(propvalue);  // red
}
</script>

</body>
```

**定义和使用**

`getPropertyPriority()` 方法返回指定的 CSS 属性是否设置了 "important!" 优先级。如果返回 "important" 则表明设置了优先级，否则没有。

**语法**

`object.getPropertyPriority(propertyname)`

`object.getPropertyValue(propertyname)`

**属性值**


|参数|描述|
|-|-|
|propertyname|必需。一个字符串，表示要检测的属性名。|

**技术细节**
|||
|-|-|
|DOM 版本:	|CSS Object Model|
|返回值:	|字符串, 表示设置了优先级，如果为空则表示没有设置优先级。|
|返回值:	|字符串, 表示属性值。|

* * * 

## item

```html
<div id="ex1" style="color:blue; font-family:monospace;">一些文本</div>

<button onclick="myFunction()">点我</button>

<script>
function myFunction() {
  var style = document.getElementById('ex1').style;
  var propname = style.item(0);
  // 或者 var propname = style[0];
  alert(propname); // color
}
</script>
```

**定义和使用**

`item()` 方法返回 CSS 样式中指定索引位置的属性名，索引值从 0 开始。

**语法**

`style.item(index)`

或

`style[index]`

**属性值**

|参数|描述|
|-|-|
|index|必需。一个数字，代码 CSS 样式属性的索引位置。|

**技术细节**

|||
|-|-|
|DOM 版本:	|CSS Object Model|
|返回值:	|字符串, 表示属性名。|

* * * 

## removePropertysetProperty

```html
<style>
#ex1 {
  color: red;
}
</style>
<button onclick="myFunction()">点我</button>

<div id="ex1">一些文本。</div>

<script>
function myFunction() {
  var declaration = document.styleSheets[0].cssRules[0].style;
  var removedvalue = declaration.removeProperty("color");
  alert(removedvalue);  // red
  var setprop = declaration.setProperty("background-color", "yellow");
}
</script>
```

**定义和使用**

`removeProperty()` 方法用于移除指定的 CSS 样式属性。

`setProperty()` 方法用于设置一个新的 CSS 属性，同时也可以修改 CSS 声明块中已存在的属性。

**语法**

`object.removeProperty(propertyname)`

`object.setProperty(propertyname, value, priority)`


**属性值**

|参数|描述|
|-|-|
|propertyname	| 必需。一个字符串，表示要移除的属性名。|

|参数|描述|
|-|-|
|propertyname|必需。一个字符串，表示创建或修改的属性。|
|value|可选，新的属性值。|
|priority|可选。字符串，规定是否需要设置属性的优先级 important。|
||可以是下面三个值:"important",undefined,""|

**技术细节**

|||
|-|-|
|DOM 版本:	|CSS Object Model|
|返回值:	|字符串, 是移除的属性名。|

|||
|-|-|
|DOM 版本:	|CSS Object Model|
|返回值:	|undefined|