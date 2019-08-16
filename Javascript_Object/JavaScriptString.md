# Javascript String
## CONTENT
### 语法
`var txt = new String("string");` 或者更简单方式：`var txt = "string";`
### String 对象属性
|属性|描述|
|-|-|
|constructor|对创建该对象的函数的引用|
|length|字符串的长度|
|prototype|允许您向对象添加属性和方法|

### String 对象方法
|方法|描述|
|-|-|
|[charAt()](#1charatcharcodeatfromcharcode)|返回在指定位置的字符。|
|[charCodeAt()](#1charatcharcodeatfromcharcode)|返回在指定的位置的字符的 Unicode 编码。|
|[fromCharCode()](#1charatcharcodeatfromcharcode)|将 Unicode 编码转为字符。|
|[concat()](#2concat)|连接两个或更多字符串，并返回新的字符串。|
|[includes()](#3includes)|查找字符串中是否包含指定的子字符串。|
|[indexOf()](#4indexoflastindexof)|返回某个指定的字符串值在字符串中首次出现的位置。|
|[lastIndexOf()](#4indexOf(&lastIndexOf)|从后向前搜索字符串，并从起始位置（0）开始计算返回字符串最后出现的位置。|
|[match()](#5match)|查找找到一个或多个正则表达式的匹配。|
|[repeat()](#6repeat)|复制字符串指定次数，并将它们连接在一起返回。|
|[replace()](#7replace)|在字符串中查找匹配的子串， 并替换与正则表达式匹配的子串。|
|[search()](#8search)|查找与正则表达式相匹配的值。|
|[slice()](#9slicesubstring)|提取字符串的片断，并在新的字符串中返回被提取的部分。|
|[substring()](#9slicesubstring)|提取字符串中两个指定的索引号之间的字符。|
|[substr()](#10substr)|从起始索引号提取字符串中指定数目的字符。|
|[split()](#11split)|把字符串分割为字符串数组。|
|[startsWith()](#12startwith)|查看字符串是否以指定的子字符串开头。|
|[toLowerCase()](#13tolowercasetouppercasetolocalelowercasetolocaleuppercase)|把字符串转换为小写。|
|[toUpperCase()](#13tolowercasetouppercasetolocalelowercasetolocaleuppercase)|把字符串转换为大写。|
|[toLocaleLowerCase()](#13tolowercasetouppercasetolocalelowercasetolocaleuppercase)|根据本地主机的语言环境把字符串转换为小写。|
|[toLocaleUpperCase()](#13tolowercasetouppercasetolocalelowercasetolocaleuppercase)|根据本地主机的语言环境把字符串转换为大写。|
|[trim()](#14trim)|去除字符串两边的空白|
|[valueOf()](#15valueoftostring)|返回某个字符串对象的原始值。|
|[toString()](#15valueoftostring)|返回一个字符串。|

## String 对象属性

```js
var txt = "Hello World!";
console.log(txt.constructor);         // ƒ String() { [native code] }
console.log((txt.length);             // 12

String.prototype.sayhi = function(){console.log('Hi!');}
txt.sayhi()                           // Hi!
```

```js
function employee(name,jobtitle,born){
    this.name=name;
    this.jobtitle=jobtitle;
    this.born=born;
}
var fred=new employee("Fred Flintstone","Caveman",1970);
employee.prototype.salary = null;
// fred employee {name: "Fred Flintstone", jobtitle: "Caveman", born: 1970}
fred.salary = 10000;
// fred employee {name: "Fred Flintstone", jobtitle: "Caveman", born: 1970, salary: 10000}
fred.height = 1.8;
// fred employee {name: "Fred Flintstone", jobtitle: "Caveman", born: 1970, salary: 10000, height: 1.8}
```

## String 对象方法

### 1.charAt()&charCodeAt()&fromCharCode()
```js
var str = "HELLO WORLD";
var n = str.charAt(2)   // =>L  
var n = str.charCodeAt(2)   // =>76  
var n = String.fromCharCode(65);  // =>A
```

`charAt()` 方法可返回指定位置的字符。

`charCodeAt()` 方法可返回指定位置的字符的 Unicode 编码。

`fromCharCode()` 可接受一个指定的 Unicode 值，然后返回一个字符串。

### 2.concat()
```js
var str1 = "Hello ";
var str2 = "world!";
var n = str1.concat(str2);  // n为Hello world!
```

`concat()` 方法用于连接两个或多个字符串。

### 3.includes()
```js
var str = "Hello world, welcome to the Runoob。";
var n = str.includes("world");  // =>true
var n = str.includes("WORLD");  // =>false
```

`includes()` 方法用于判断字符串是否包含指定的子字符串。

如果找到匹配的字符串则返回 true，否则返回 false。

&hearts; 注意： includes() 方法区分大小写。

### 4.indexOf(&lastIndexOf()
```js
var str = "Hello world, welcome to the Runoob。";
str.indexOf('o')               // 4
str.indexOf('w')               // 6
str.lastIndexOf('o')           // 32
str.lastIndexOf('o',25)        // 22
```

`indexOf()` 方法可返回某个指定的字符串值在字符串中首次出现的位置。

如果没有找到匹配的字符串则返回 -1。

&hearts; 注意： indexOf() 方法区分大小写。

`lastIndexOf()` 方法可返回一个指定的字符串值最后出现的位置，如果指定第二个参数 start，则在一个字符串中的指定位置从后向前搜索。

&hearts; 注意： 该方法将从后向前检索字符串，但返回是从起始位置 (0) 开始计算子字符串最后出现的位置。 看它是否含有字符串。

开始检索的位置在字符串的 start 处或字符串的结尾（没有指定 start 时）。

如果没有找到匹配字符串则返回 -1 。

&hearts; 注意：lastIndexOf() 方法是区分大小写的！

**语法**

`string.indexOf(searchvalue,start)`
`string.lastIndexOf(searchvalue,start)`

### 5.match()
```js
var str="The rain in SPAIN stays mainly in the plain"; 
var n=str.match(/ain/g);  // ain,ain,ain
```

match() 方法可在字符串内检索指定的值，或找到一个或多个正则表达式的匹配。

&hearts; 注意： match() 方法将检索字符串 String Object，以找到一个或多个与 regexp 匹配的文本。这个方法的行为在很大程度上有赖于 regexp 是否具有标志 g。如果 regexp 没有标志 g，那么 match() 方法就只能在 stringObject 中执行一次匹配。如果没有找到任何匹配的文本， match() 将返回 null。否则，它将返回一个数组，其中存放了与它找到的匹配文本有关的信息。

**语法**

`string.match(regexp)`

### 6.repeat()
```js
var str = "Runoob";
var n = str.repeat(2);  // n RunoobRunoob, str Runoob
```

`repeat()` 方法字符串复制指定次数。该方法不会改变原始字符串。

**语法**

`string.repeat(count)`

### 7.replace()
```js
var str="Visit Microsoft! Visit Microsoft!";
var n = str.replace("Microsoft","Runoob");             // n = Visit Runoob! Visit Microsoft!  str="Visit Microsoft! Visit Microsoft!"
var n = str.replace(/Microsoft/g,"Runoob");            // n = Visit Runoob! Visit Runoob!     str="Visit Microsoft! Visit Microsoft!"
```

`replace()` 方法用于在字符串中用一些字符替换另一些字符，或替换一个与正则表达式匹配的子串。

该方法不会改变原始字符串。

**语法**

`string.replace(searchvalue,newvalue)`

### 8.search()
```js
// 查找 "Runoob":
var str="Visit Runoob!"; 
var n=str.search("Runoob");  // 6
```

`search()` 方法用于检索字符串中指定的子字符串，或检索与正则表达式相匹配的子字符串。返回匹配的 String 对象起始位置。

如果没有找到任何匹配的子串，则返回 -1。

**语法**

`string.search(searchvalue)`

### 9.slice()&substring()
```js
var str = "Hello world!"; 
var n = str.slice(1,7);      // n = "ello w"  str = "Hello world!"
var m = str.substring(1,7)   // m = "ello w"  str = "Hello world!"
```

`slice(start, end)` 方法可提取字符串的某个部分，并以新的字符串返回被提取的部分。

使用 start（包含） 和 end（不包含） 参数来指定字符串提取的部分。

字符串中第一个字符位置为 0, 第二个字符位置为 1, 以此类推。

&hearts; 提示： 如果是负数，则该参数规定的是从字符串的尾部开始算起的位置。也就是说，-1 指字符串的最后一个字符，-2 指倒数第二个字符，以此类推。

**语法**

`string.slice(start,end)`

**参数值**

|参数|描述|
|-|-|
|start|必须。要抽取的片断的起始下标。第一个字符位置为 0|
|end|可选。 紧接着要截取的片段结尾的下标。若未指定此参数，则要提取的子串包括 start 到原字符串结尾的字符串。如果该参数是**负数，那么它规定的是从字符串的尾部开始算起的位置。**|

---

`substring()` 方法用于提取字符串中介于两个指定下标之间的字符。

`substring()` 方法返回的子串包括 开始 处的字符，但不包括 结束 处的字符。

**语法**

`string.substring(from, to)`

|参数|描述|
|-|-|
|from|必需。一个非负的整数，规定要提取的子串的第一个字符在 string Object 中的位置。|
|to|可选。一个非负的整数，比要提取的子串的最后一个字符在 string Object 中的位置多 1。如果省略该参数，那么返回的子串会一直到字符串的结尾。如果该参数是**负数，那么返回from到元字符串开头。**|

### 10.substr()
```js
var str="Hello world!";
var n=str.substr(2,3)                        // llo
```

`substr()` 方法可在字符串中抽取从 开始 下标开始的指定数目的字符。

&hearts; 提示： substr() 的参数指定的是子串的开始位置和长度，因此它可以替代 substring() 和 slice() 来使用。

在 IE 4 中，参数 start 的值无效。在这个 BUG 中，start 规定的是第 0 个字符的位置。在之后的版本中，此 BUG 已被修正。

ECMAscript 没有对该方法进行标准化，因此反对使用它。

&hearts; 注意： substr() 方法不会改变源字符串。

**语法**

`string.substr(start,length)`

### 11.split()
```js
var str = "How are you doing today?";
var n = str.split(" ");                 // How,are,you,doing,today?
var n = str.split(" "，3);              // How,are,you
```

**语法**

`string.split(separator,limit)`

**参数值**

|参数|描述|
|-|-|
|separator|可选。字符串或正则表达式，从该参数指定的地方分割 string Object。|
|limit|可选。该参数可指定返回的数组的最大长度。如果设置了该参数，返回的子串不会多于这个参数指定的数组。如果没有设置该参数，整个字符串都会被分割，不考虑它的长度。|

**返回值**

|类型|描述|
|-|-|
|Array|一个字符串数组。该数组是通过在 separator 指定的边界处将字符串 string Object 分割成子串创建的。返回的数组中的字串不包括 separator 自身。|

### 12.startWith()
```js
var str = "Hello world, welcome to the Runoob.";
var n = str.startsWith("Hello");             // true
var n = str.startsWith("Hellaaaa");          // false
var n = str.startsWith("world",6);           // true
```

`startsWith()` 方法用于检测字符串是否以指定的子字符串开始。

如果是以指定的子字符串开头返回 true，否则 false。

startsWith() 方法对大小写敏感。

**语法**

`string.startsWith(searchvalue, start)`

**参数值**

|参数|描述|
|-|-|
|searchvalue|必需，要查找的字符串。|
|start|可选，查找的开始位置，默认为 0。|


### 13.toLowerCase()&toUpperCase()&toLocaleLowerCase()&toLocaleUpperCase()

```js
var str="Runoob";
console.log(str.toLowerCase()+'\n');
console.log(str.toUpperCase()+'\n');
console.log(str.toLocaleLowerCase()+'\n');
console.log(str.toLocaleUpperCase()+'\n');
/*
runoob
RUNOOB
runoob
RUNOOB
*/
```

`toLowerCase()` 方法用于把字符串转换为小写。

`toUpperCase()` 方法用于把字符串转换为大写。

`toLocaleLowerCase()` 方法根据本地主机的语言环境把字符串转换为小写。

`toLocaleUpperCase()` 方法根据本地主机的语言环境把字符串转换为大写。

本地是根据浏览器的语言设置来判断的。通常，该方法与 toLowerCase(), toUpperCase() 方法返回的结果相同，只有几种语言（如土耳其语）具有地方特有的大小写映射。

&hearts; 注意: toLocaleLowerCase() 方法没有改变原始字符串。

**语法**

`string.toLowerCase()` ……

### 14.trim()
```js
var str = "       Runoob        ";
console.log(str.trim());  // Runoob
var str = "       Run  oob        ";
console.log(str.trim());  // Run  oob
```

`trim()` 方法用于删除字符串的头尾空格。

`trim()` 方法不会改变原始字符串。

**语法**

`string.trim()`

### 15.valueOf()&toString()

```js
var str="Hello world!";
str.valueOf();                  // "Hello world!"
str.toString();                 // "Hello world!"
```

`valueOf()` 方法可返回 String 对象的原始值。

&hearts; 注意： valueOf() 方法通常由 JavaScript 在后台自动进行调用，而不是显式地处于代码中。

`toString()` 方法返回一个表示 String 对象的值。

**语法**

`string.valueOf()`

`string.toString()`