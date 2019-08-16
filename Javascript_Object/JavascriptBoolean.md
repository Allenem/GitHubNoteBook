# Javascript Boolean

## Boolean 对象属性

| 属性 | 描述 |
|-|-|
| [constructor](#1constructor ) | 返回对创建此对象的 Boolean 函数的引用 |
| [prototype](#2prototype) | 使您有能力向对象添加属性和方法。 |

### 1.constructor 
```js
var myvar=new Boolean(1);
console.log(myvar.constructor);
// ƒ Boolean() { [native code] }
```

`constructor` 属性返回对创建此对象的 Boolean 函数的引用。

### 2.prototype
```js
Boolean.prototype.myColor=function(){
	if (this.valueOf()==true){
		this.color="green";
	}
	else{
		this.color="red";
	}
}	
var a = new Boolean(1);
a.myColor();
console.log(a.color);
// "green"
```

`prototype` 属性使您有能力向对象添加属性和方法。

当构造一个原型，所有的布尔对象默认都添加了属性或方法。

&hearts; 注意： Boolean.prototype 不是引用布尔值，但 Boolean() 对象是。

&hearts; 注意： Prototype是一个全局属性，这对于几乎全部的JavaScript对象。

## Boolean 对象方法

| 方法 | 描述 |
|-|-|
| [toString()](#1tostring) | 把布尔值转换为字符串，并返回结果。 |
| [valueOf()](#2valueof) | 返回 Boolean 对象的原始值。 |

### 1.toString()
```js
var myvar=new Boolean(0);console.log(myvar.toString());  // false
var myvar=new Boolean(1);console.log(myvar.toString());  // true
```

`toString()` 方法可把一个逻辑值转换为字符串，并返回结果

### 2.valueOf()
```js
var bool = new Boolean(0);
console.log( bool.valueOf());  // false
```
`valueOf()` 方法可返回 Boolean 对象的原始值。