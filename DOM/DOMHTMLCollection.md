# DOMHTMLCollection

`HTMLCollection` 是 HTML 元素的集合。

`HTMLCollection` 对象类似一个包含 HTML 元素的数组列表。

`getElementsByTagName()` 方法返回的就是一个 `HTMLCollection` 对象。

## CONTENT

| 属性 / 方法 | 描述 |
|-|-|
|[item()](#item)|返回 HTMLCollection 中指定索引的元素。|
|[length](#length)|返回 HTMLCollection 中元素的数量。|
|[namedItem()](#namedItem)|返回 HTMLCollection 中指定 ID 或 name 属性的元素。|

* * * 

## item

**定义和用法**

`item()` 方法返回 HTMLCollection 对象中指定索引位置的元素。

元素在 HTMLCollection 对象中的顺序与它们在文档源代码中出现的顺序一样，索引起始位置为 0。

也可以使用以下简写的方式，获取的结果是一样的：

`var x = document.getElementsByTagName("P")[0];`

**语法**

`HTMLCollection.item(index)`

或：

`HTMLCollection[index]`

## length

**定义和用法**

`length` 属性返回 HTMLCollection 对象中元素的数量。

该属性是只读的。

该属性在循环 HTMLCollection 对象时很有用。

**语法**

`HTMLCollection.length`

## namedItem

**定义和用法**

`namedItem()` 方法返回 HTMLCollection 对象中指定 ID 或 name 的元素。

也可以使用以下简写方式来获取：

`var x = document.getElementsByTagName("P")["myElement"];`

**语法**

`HTMLCollection.namedItem(name)`

或：

`HTMLCollection[name]`

**参数说明：**

|参数|描述|
|-|-|
|name|必需，你要返回元素的 ***id*** 或 ***name*** 属性的值。|