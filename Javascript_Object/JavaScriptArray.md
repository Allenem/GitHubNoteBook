# JavaScript Array

## CONTENT

### Ⅰ.Attributes of Array Object (3)

| 属性 | 描述 |
|-|-|
| [constructor](#1constructor) | 返回创建数组对象的原型函数。 |
| [length](#2length) | 设置或返回数组元素的个数。 |
| [prototype](#3prototype) | 允许你向数组对象添加属性或方法。 |

### Ⅱ.Methods of Array Object (30)

| 方法 | 描述 |
|-|-|
| [concat()](#1concat) | 连接两个或更多的数组，并返回结果。 |
| [copyWith()](#2copywith) | 从数组的指定位置拷贝元素到数组的另一个指定位置中。 |
| [entries()](#3entries) | 返回数组的可迭代对象。 |
| [keys()](#4keys) | 返回数组的可迭代对象，包含原始数组的键(key)。 |
| [every()](#5every) | 检测数值元素的每个元素是否都符合条件。 |
| [some()](#6some) | 检测数组元素中是否有元素符合指定条件。 |
| [fill()](#7fill) | 使用一个固定值来填充数组。 |
| [filter()](#8filter) | 检测数值元素，并返回符合条件所有元素的数组。 |
| [find()](#9find) | 返回符合传入测试（函数）条件的数组元素。 |
| [findIndex()](#10findindex) | 返回符合传入测试（函数）条件的数组元素索引。 |
| [forEach()](#11foreach) | 数组每个元素都执行一次回调函数。 |
| [map()](#12map) | 通过指定函数处理数组的每个元素，并返回处理后的数组。 |
| [from()](#13from) | 通过给定的对象中创建一个数组。 |
| [includes()](#14includes) | 判断一个数组是否包含一个指定的值。 |
| [indexOf()](#15indexof) | 搜索数组中的元素，并返回它所在的位置。 |
| [lastIndexOf()](#16lastindexof) | 搜索数组中的元素，并返回它最后出现的位置。 |
| [isArray()](#17isarray) | 判断对象是否为数组。 |
| [join()](#18join) | 把数组的所有元素放入一个字符串。 |
| [push()](#19push) | 向数组的末尾添加一个或更多元素，并返回新的长度。 |
| [pop()](#20pop) | 删除数组的最后一个元素并返回删除的元素。 |
| [unshift()](#21unshift) | 向数组的开头添加一个或更多元素，并返回新的长度。 |
| [shift()](#22shift) | 删除并返回数组的第一个元素。 |
| [reduce()](#23reduce) | 将数组元素计算为一个值（从左到右）。 |
| [reduceRight()](#24reduceright) | 将数组元素计算为一个值（从右到左）。 |
| [reverse()](#25reverse) | 反转数组的元素顺序。 |
| [sort()](#26sort) | 对数组的元素进行排序。 |
| [toString()&toLocaleString()](#27tostringtolocalestring) | 把数组转换为字符串，并返回结果。 |
| [valueOf()](#28valueof) | 返回数组对象的原始值。 |
| [slice()](#29slice) | 选取数组的的一部分，并返回一个新数组。 |
| [splice()](#30splice) | 从数组中添加或删除元素。 |

## Ⅰ.Attributes of Array Object

### 1.constructor
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.constructor);  // ƒ Array() { [native code] }
```

`array.constructor` 返回创建数组对象的原型函数。

### 2.length
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.length);  // 4
```

`array.length` 设置或返回数组元素的个数。

### 3.prototype
```js
Array.prototype.myUcase=function()
{
    for (i=0;i<this.length;i++)
    {
        this[i]=this[i].toUpperCase();
    }
}

var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.myUcase();
console.log(fruits);  // ["BANANA", "ORANGE", "APPLE", "MANGO"]
```

`Array.prototype.……` 允许你向数组对象添加属性或方法。

## Ⅱ.Methods of Array Object

### 1.concat()
```js
var hege = ["Cecilie", "Lone"];
var stale = ["Emil", "Tobias", "Linus"];
var kai = ["Robin"];
var children = hege.concat(stale,kai);
console.log(hege,children);  
// hege: ["Cecilie", "Lone"] 
// children: ["Cecilie", "Lone", "Emil", "Tobias", "Linus", "Robin"]
```

`concat()` 方法用于连接两个或多个数组。该方法不会改变现有的数组，而仅仅会返回被连接数组的一个副本。

```js
var a = [1, 2, 3];
a.concat(4, 5);           // 返回[1, 2, 3, 4, 5]
a.concat([4,5])           // 返回[1, 2, 3, 4, 5]
a.concat([4,5],[6,7])     // 返回[1, 2, 3, 4, 5, 6, 7]
a.concat(4, [5,[6,7]])    // 返回[1, 2, 3, 4, 5, [6,7] ]
```

创建并返回一个新数组，它的元素包括调用 concat() 的原始数组的元素和 concat() 的每个参数。如果这些参数中的任何一个自身是数组，则连接的是数组的元素，而非数组本身。但要注意，concat() 不会递归扁平化数组的数组。

>PS.一道面试题：传递两个参数m，n，返回长度为m，所有元素都为n的数组，要求不能用循环。利用函数的递归和 concat() 方法可以实现，代码如下：
>```js
>function fn(m, n) {
>  return m ? fn(m - 1, n).concat(n) : [];
>}
>```

**语法**

`array1.concat(array2,array3,...,arrayX)`

**参数**

|参数|描述|
|-|-|
|array2, array3, ..., arrayX|	必需。该参数可以是具体的值，也可以是数组对象。可以是任意多个。|

### 2.copyWith()
```js
var fruits = ["Banana", "Orange", "Apple", "Mango", "Kiwi", "Papaya"];
console.log(fruits.copyWithin(2,0,2));  // ["Banana", "Orange", "Banana", "Orange", "Kiwi", "Papaya"]
```

`copyWithin()` 方法用于从数组的指定位置拷贝元素到数组的另一个指定位置中，返回新数组，数组长度不变。

**语法**

`array.copyWithin(target, start, end)`

**参数**

|参数|描述|
|-|-|
|target|必需。复制到指定目标索引位置。|
|start|可选。元素复制的起始位置。|
|end|可选。停止复制的索引位置 (默认为 array.length)，即不包含这一位。如果为负值，表示倒数。|

### 3.entries()
### 4.keys()
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var x = fruits.entries();
console.log(x);                       // Array Iterator {}
console.log(x.next().value);          // [0, "Banana"]
console.log(x.next().value);          // [1, "Orange"]
console.log(x.next().value);          // [2, "Apple"]
console.log(x.next().value);          // [3, "Mango"]
console.log(x.next().value);          // undefined
```

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var x = fruits.keys();
console.log(x);                       // Array Iterator {}
console.log(x.next().value);          // 0
console.log(x.next().value);          // 1
console.log(x.next().value);          // 2
console.log(x.next().value);          // 3
console.log(x.next().value);          // undefined
```

```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var x = fruits.entries();
console.log(x);                       // Array Iterator {}
console.log(x.next());                // {value: Array(2), done: false}
console.log(x.next());                // {value: Array(2), done: false}
console.log(x.next());                // {value: Array(2), done: false}
console.log(x.next());                // {value: Array(2), done: false}
console.log(x.next());                // {value: undefined, done: true}
```

`entries()` 方法返回一个数组的 **迭代对象** ，该对象包含数组的键值对 (key/value)。迭代对象中数组的索引值作为 key， 数组元素作为 value。

`keys()` 方法用于从数组创建一个包含数组键的可迭代对象。如果对象是数组返回 true，否则返回 false。

**语法**

`array.entries()`

### 5.every() 
### 6.some()
```js
a = [1, 2, 3, 4, 5];
a.every(function(x) {
    return x < 10;
});                            // => true:所有值<10
a.every(function(x) {
    return x % 2 === 0;
});                            // => false:不是所有的值都是偶数

a.some(function(x) {
    return x % 2 === 0; 
});                            // => true: a含有偶数值
a.some(isNaN);                 // => false: a不包含非数值元素
```

类比数学中的任意，存在。

&hearts; 注意： every() 不会对空数组进行检测。

&hearts; 注意： every() 不会改变原始数组。

**语法**

`array.every(function(currentValue,index,arr), thisValue)`

**参数**

|参数|描述|
|-|-|
|function(currentValue, index,arr)|必须。函数，数组中的每个元素都会执行这个函数
|thisValue|可选。对象作为该执行回调时使用，传递给函数，用作 "this" 的值。如果省略了 thisValue ，"this" 的值为 "undefined"|

函数参数:
|参数|描述|
|-|-|
|currentValue|必须。当前元素的值|
|index|可选。当前元素的索引值|
|arr|可选。当前元素属于的数组对象|

### 7.fill()
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits.fill("Runoob",1,3))  // ["Banana", "Runoob", "Runoob", "Mango"]
```

`fill()` 使用一个固定值来填充数组。

**语法**

`array.fill(value, start, end)`

**参数**

|参数|描述|
|-|-|
|value|必需。填充的值。|
|start|可选。开始填充位置。|
|end|可选。停止填充位置 (默认为 array.length)|

### 8.filter()
```js
var ages = [32, 33, 16, 40];
ages.filter(value => value > 18);  // [32, 33, 40]
```

`filer()` 检测数值元素，并返回符合条件所有元素的数组。

**语法**

`array.filter(function(currentValue,index,arr), thisValue)`

**参数**

|参数|描述|
|-|-|
|function(currentValue, index,arr)|必须。函数，数组中的每个元素都会执行这个函数
|thisValue|可选。对象作为该执行回调时使用，传递给函数，用作 "this" 的值。如果省略了 thisValue ，"this" 的值为 "undefined"|

函数参数:
|参数|描述|
|-|-|
|currentValue|必须。当前元素的值|
|index|可选。当前元素的索引值|
|arr|可选。当前元素属于的数组对象|

### 9.find()
### 10.findIndex()
```js
var ages = [3, 10, 18, 20];
ages.find(age => age >= 18);  // 18
ages.findIndex(age => age >= 18);  // 2
```

`find()` , `findIndex()` 方法返回通过测试（函数内判断）的数组的第一个元素的值。

`find()` , `findIndex()` 方法为数组中的每个元素都调用一次函数执行：

  - 当数组中的元素在测试条件时返回 true 时, find() 返回符合条件的元素，之后的值不会再调用执行函数。
  - `find()` 如果没有符合条件的元素返回 undefined 
  - `findIndex()` 如果没有符合条件的元素返回 -1

&hearts; 注意: `find()` , `findIndex()` 对于空数组，函数是不会执行的。

&hearts; 注意: `find()` , `findIndex()` 并没有改变数组的原始值。


**语法**

`array.find(function(currentValue, index, arr), thisValue)`
`array.findIndex(function(currentValue, index, arr), thisValue)`

**参数**

同上


### 11.forEach() 
### 12.map()

```js
var numbers = [4, 9, 16, 25];
numbers.forEach((item,index) =>  console.log( "index[" + index + "]: " + item );)
// index[0]: 4
// index[1]: 9
// index[2]: 16
// index[3]: 25
numbers.map(Math.sqrt);
// [2, 3, 4, 5]
```

forEach() 方法用于调用数组的每个元素，并将元素传递给回调函数。

&hearts; 注意: forEach() 对于空数组是不会执行回调函数的。

---

map() 方法返回一个新数组，数组中的元素为原始数组元素调用函数处理后的值。

map() 方法按照原始数组元素顺序依次处理元素。

&hearts; 注意： map() 不会对空数组进行检测。

&hearts; 注意： map() 不会改变原始数组。

**语法**

`array.forEach(function(currentValue, index, arr), thisValue)`
`array.map(function(currentValue,index,arr), thisValue)`

**参数**

同上

### 13.from()
```js
var myArr = Array.from("RUNOOB");
console.log(myArr);  // ["R", "U", "N", "O", "O", "B"]
```

`from()` 方法用于通过拥有 length 属性的对象或可迭代的对象来返回一个数组。

如果对象是数组返回 true，否则返回 false。

**语法**

`Array.from(object, mapFunction, thisValue)`

**参数**

|参数|描述|
|-|-|
|object|必需，要转换为数组的对象。|
|mapFunction|可选，数组中每个元素要调用的函数。|
|thisValue|可选，映射函数(mapFunction)中的 this 对象。|

### 14.includes()
```js
[1, 2, 3].includes(2);     // true
[1, 2, 3].includes(4);     // false
[1, 2, 3].includes(3, 3);  // false
[1, 2, 3].includes(3, -1); // true
[1, 2, NaN].includes(NaN); // true
```

`includes()` 方法用来判断一个数组是否包含一个指定的值，如果是返回 true，否则 false。

**语法**

`arr.includes(searchElement)`
`arr.includes(searchElement, fromIndex)`

**参数**

|参数|描述|
|-|-|
|searchElement|必须。需要查找的元素值。|
|fromIndex|可选。从该索引处开始查找 searchElement。如果为负值，则按升序从 array.length + fromIndex 的索引开始搜索。默认为 0。|

### 15.indexOf()
### 16.lastIndexOf()

```js
a = [0, 1, 2, 1, 0];
a.indexOf(1);                // => 1:a[1]是1
a.lastIndexOf(1);            // => 3:a[1]是1
a.indexOf(3);                // => -1: 没有值为3的元素
```

搜索整个数组中具有给定值的元素，返回找到的第一个元素的索引，indexOf() 正向搜索，lastIndexOf()反向搜索，找不到返回-1。

**语法**

`array.indexOf(item,start)`
`array.lastIndexOf(item,start)`

**参数**

|参数|描述|
|-|-|
|item|必须。查找的元素。|
|start|可选的整数参数。规定在数组中开始检索的位置。它的合法取值是 0 到 stringObject.length - 1。如省略该参数，则将从字符串的首字符开始检索。|

### 17.isArray()
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(Array.isArray(fruits));  // true
var num = 100000;
console.log(Array.isArray(num))      // false
```

isArray() 方法用于判断一个对象是否为数组。

如果对象是数组返回 true，否则返回 false。

**语法**

`Array.isArray(obj)`

**参数**

|参数|描述|
|-|-|
|obj|必需，要判断的对象。|

### 18.join()
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
var energy = fruits.join();
console.log(energy);  // Banana,Orange,Apple,Mango
var energy1 = fruits.join('%');
console.log(energy1);  // Banana%Orange%Apple%Mango
```

`join()` 方法用于把数组中的所有元素转换一个字符串，默认用逗号分割。元素也可以通过指定的分隔符进行分隔。

**语法**

`array.join(separator)`

**参数**

|参数|描述|
|-|-|
|separator|可选。指定要使用的分隔符。如果省略该参数，则使用逗号作为分隔符。|

### 19.push
### 20.pop()
```js
var stack = [];             // stack: []
stack.push(1,2);            // stack: [1,2] 返回2
stack.pop();                // stack: [1] 返回2
stack.push(3);              // stack: [1,3] 返回2
stack.pop();                // stack: [1] 返回3
stack.push([4,5]);          // stack: [1,[4,5]] 返回2
stack.pop();                // stack: [1] 返回[4,5]
stack.pop();                // stack: [] 返回1
```

`push()` 方法在数组的尾部添加一个或多个元素，并返回新的长度。 

`pop()` 删除数组的最后一个元素，减小数组长度并返回它的值。

### 21.unshift()
### 22.shift()
```js
var a = [];                 // a: []
a.unshift(1);               // a:[1]  返回：1
a.unshift(22);              // a:[22,1]  返回：2
a.shift();                  // a:[1] 返回：22
a.unshift(3,[4,5]);         // a:[3,[4,5],1] 返回：3
a.shift();                  // a:[[4,5],1] 返回：3
a.shift();                  // a:[1] 返回：[4,5]
a.shift();                  // a:[] 返回：1
```

`unshift()` 方法可向数组的开头添加一个或更多元素，并返回新的长度。

`shift()` 方法用于把数组的第一个元素从其中删除，并返回第一个元素的值。

### 23.reduce
### 24.reduceRight
```js
var a = [1, 2, 3, 4, 5];

// 数组求和
var sum = a.reduece(function(x, y) {
    return x + y
}, 0);

// 数组求积
var product = a.reduce(function(x, y) {
    return x * y
}, 1);

// 求最大值
var max = a.reduce(function(x, y) {
    return (x > y)?x:y;
});

var a = [2, 3, 4];
// 计算2^(3^4)。乘方操作的有限顺序是从右到左
var big = a.reduceRight(function(accumulator, value) {
    return Math.pow(value, accumulator);
});
```

**语法**

`array.reduce(function(total, currentValue, currentIndex, arr), initialValue)`
`array.reduceRight(function(total, currentValue, currentIndex, arr), initialValue)`

**参数**

|参数|描述|
|-|-|
|function(total,currentValue, index,arr)|必需。用于执行每个数组元素的函数。|
|initialValue|可选。传递给函数的初始值|

**函数参数:**

|参数|描述|
|-|-|
|total	必需。初始值, 或者计算结束后的返回值。|
|currentValue|必需。当前元素|
|currentIndex|可选。当前元素的索引|
|arr|可选。当前元素所属的数组对象。|

### 25.reverse()
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
fruits.reverse();
console.log(fruits);
// ["Mango", "Apple", "Orange", "Banana"]
```

reverse() 方法用于颠倒数组中元素的顺序。

**语法**

`array.reverse()`

**返回值**

|类型|描述|
|-|-|
|Array|颠倒顺序后的数组|

### 26.sort()
```js
var a = [33, 4, 1111, 222];
a.sort();                     // 字母表顺序：1111,222,33，4
a.sort(function(a,b) {        // 数值排序：4，33, 222，1111
    return a-b; 
});
a.sort(function(a,b) {        // 数值大小相反的顺序：1111, 222, 33, 4
    return b-a
}); 
```

```js
a = ['monkey', 'Bug', 'cat', 'Giraffe']
a.sort();                     // 区分大小写的排序: ["Bug", "Giraffe", "cat", "monkey"]
a.sort((x,y)=>{
  a=x.toLowerCase();
  b=y.toLowerCase();
  if(a<b) return -1;
  if(a>b) return 1;
  return 0;
});                           // 不区分大小写的排序：["Bug", "cat", "Giraffe", "monkey"]
```
**语法**

`array.sort(sortfunction)`

**参数**

|参数|描述|
|-|-|
|sortfunction|可选。规定排序顺序。必须是函数。|

### 27.toString()&toLocaleString()
```js
[1,2,3].toString();          //生成'1,2,3'
["a","b","c"].toString();    //生成'a,b,c'
[1,[2,'c']].toString();      //生成'1,2,c'
```

`toString()` 方法可把数组转换为字符串，并返回结果。

&hearts; 注意： 数组中的元素之间用逗号分隔。

与不使用任何参数的 join() 方法是一样的。

**语法**

`array.toString()`

### 28.valueOf()
```js
var fruits = ["Banana", "Orange", "Apple", "Mango"];
console.log(fruits);                 // ["Banana", "Orange", "Apple", "Mango"]
console.log(fruits.valueOf());       // ["Banana", "Orange", "Apple", "Mango"]
```

valueOf() 方法返回 Array 对象的原始值。

该原始值由 Array 对象派生的所有对象继承。

valueOf() 方法通常由 JavaScript 在后台自动调用，并不显式地出现在代码中。

&hearts; 注意： valueOf() 方法不会改变原数组。

### 29.slice()
```js
var a = [1, 2, 3, 4, 5];
a.slice(0,3);                       // 返回[1, 2, 3]  a 是 [1, 2, 3, 4, 5];
a.slice(3);                         // 返回[4, 5]     a 是 [1, 2, 3, 4, 5];
a.slice(1,-1);                      // 返回[2, 3, 4]  a 是 [1, 2, 3, 4, 5];
a.slice(-3, -2);                    // 返回[3]        a 是 [1, 2, 3, 4, 5];
```

slice() 方法可从已有的数组中返回选定的元素。

slice()方法可提取字符串的某个部分，并以新的字符串返回被提取的部分。

&hearts; 注意： slice() 方法不会改变原始数组。

**语法**

`array.slice(start, end)`

**参数**

|参数|描述|
|-|-|
|start|可选。规定从何处开始选取。如果是负数，那么它规定从数组尾部开始算起的位置。也就是说，-1 指最后一个元素，-2 指倒数第二个元素，以此类推。|
|end|可选。规定从何处结束选取。该参数是数组片断结束处的数组下标。如果没有指定该参数，那么切分的数组包含从 start 到数组结束的所有元素。如果这个参数是负数，那么它规定的是从数组尾部开始算起的元素。|

### 30.splice()
```js
var a = [1, 2, 3, 4, 5, 6, 7, 8];
a.splice(4);                  // 返回[5, 6, 7, 8]; a是[1, 2, 3, 4]
a.splice(1,2);                // 返回[2, 3]; a是[1, 4]
a.splice(1,1);                // 返回[4]; a是[1]
```
第一个参数指定了插入或删除的起始位置，第二个参数指定了应该从数组中删除的元素的个数。
```js
var a = [1, 2, 3, 4, 5];
a.splice(2, 0, 'a', 'b');     // 返回[]; a是[1, 2, 'a', 'b', 3, 4, ,5]
a.splice(2, 2, [1,2], 3);     // 返回['a', 'b']; a是[1, 2, [1, 2], 3, 3, 4, 5]
```
紧随前两个参数之后的任意个参数指定了需要插入到数组中的元素，从第一个参数指定的其实位置开始插入。

**语法**

`array.splice(index,howmany,item1,.....,itemX)`

**参数**

|参数|描述|
|-|-|
|index|必需。规定从何处添加/删除元素。该参数是开始插入和（或）删除的数组元素的下标，必须是数字。|
|howmany|可选。规定应该删除多少元素。必须是数字，但可以是 "0"。如果未规定此参数，则删除从 index 开始到原数组结尾的所有元素。|
|item1, ..., itemX|可选。要添加到数组的新元素。|