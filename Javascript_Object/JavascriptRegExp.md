# Javascript RegExp
(Regular Expression)

**语法**
```js
var patt=new RegExp(pattern,modifiers);
// or
var patt=/pattern/modifiers;
```
pattern(模式) 描述了表达式的模式

modifiers(修饰符) 用于指定全局匹配、区分大小写的匹配和多行匹配

&hearts; 注意：当使用构造函数创造正则对象时，需要常规的字符转义规则（在前面加反斜杠 \）。比如，以下是等价的：
```js
var re = new RegExp("\\w+");
var re = /\w+/;
```
## CONTENT
### 修饰符

修饰符用于执行区分大小写和全局匹配:

| 修饰符 | 描述 |
|-|-|
| [i](https://www.runoob.com/js/jsref-regexp-i.html) | 执行对大小写不敏感的匹配。 |
| [g](https://www.runoob.com/js/jsref-regexp-g.html) | 执行全局匹配（查找所有匹配而非在找到第一个匹配后停止）。 |
| m | 执行多行匹配。 |

### 方括号

方括号用于查找某个范围内的字符：

| 表达式 | 描述 |
|-|-|
| [[abc]](https://www.runoob.com/jsref/jsref-regexp-charset.html) | 查找方括号之间的任何字符。 |
| [[^abc]](https://www.runoob.com/jsref/jsref-regexp-charset-not.html) | 查找任何不在方括号之间的字符。 |
| [0-9] | 查找任何从 0 至 9 的数字。 |
| [a-z] | 查找任何从小写 a 到小写 z 的字符。 |
| [A-Z] | 查找任何从大写 A 到大写 Z 的字符。 |
| [A-z] | 查找任何从大写 A 到小写 z 的字符。 |
| [adgk] | 查找给定集合内的任何字符。 |
| [^adgk] | 查找给定集合外的任何字符。 |
| (red|blue|green) | 查找任何指定的选项。 |

### 元字符

元字符（Metacharacter）是拥有特殊含义的字符：

| 元字符 | 描述 |
|-|-|
| [.](https://www.runoob.com/jsref/jsref-regexp-dot.html) | 查找单个字符，除了换行和行结束符。 |
| [\w](https://www.runoob.com/jsref/jsref-regexp-wordchar.html) | 查找单词字符。 |
| [\W](https://www.runoob.com/jsref/jsref-regexp-wordchar-non.html) | 查找非单词字符。 |
| [\d](https://www.runoob.com/jsref/jsref-regexp-digit.html) | 查找数字。 |
| [\D](https://www.runoob.com/jsref/jsref-regexp-digit-non.html) | 查找非数字字符。 |
| [\s](https://www.runoob.com/jsref/jsref-regexp-whitespace.html) | 查找空白字符。 |
| [\S](https://www.runoob.com/jsref/jsref-regexp-whitespace-non.html) | 查找非空白字符。 |
| [\b](https://www.runoob.com/jsref/jsref-regexp-begin.html) | 匹配单词边界。 |
| [\B](https://www.runoob.com/jsref/jsref-regexp-begin-not.html) | 匹配非单词边界。 |
| \0 | 查找 NULL 字符。 |
| [\n](https://www.runoob.com/jsref/jsref-regexp-newline.html) | 查找换行符。 |
| \f | 查找换页符。 |
| \r | 查找回车符。 |
| \t | 查找制表符。 |
| \v | 查找垂直制表符。 |
| [\xxx](https://www.runoob.com/jsref/jsref-regexp-octal.html) | 查找以八进制数 xxx 规定的字符。 |
| [\xdd](https://www.runoob.com/jsref/jsref-regexp-hex.html) | 查找以十六进制数 dd 规定的字符。 |
| [\uxxxx](https://www.runoob.com/jsref/jsref-regexp-unicode-hex.html) | 查找以十六进制数 xxxx 规定的 Unicode 字符。 |

### 量词

| 量词 | 描述 |
|-|-|
| [n+](https://www.runoob.com/jsref/jsref-regexp-onemore.html) | 匹配任何包含至少一个 n 的字符串。例如，/a+/ 匹配 "candy" 中的 "a"，"caaaaaaandy" 中所有的 "a"。|
| [n*](https://www.runoob.com/jsref/jsref-regexp-zeromore.html) | 匹配任何包含零个或多个 n 的字符串。例如，/bo*/ 匹配 "A ghost booooed" 中的 "boooo"，"A bird warbled" 中的 "b"，但是不匹配 "A goat grunted"。 |
| [n?](https://www.runoob.com/jsref/jsref-regexp-zeroone.html) | 匹配任何包含零个或一个 n 的字符串。例如，/e?le?/ 匹配 "angel" 中的 "el"，"angle" 中的 "le"。 |
| [n{X}](https://www.runoob.com/jsref/jsref-regexp-nx.html) | 匹配包含 X 个 n 的序列的字符串。例如，/a{2}/ 不匹配 "candy," 中的 "a"，但是匹配 "caandy," 中的两个 "a"，且匹配 "caaandy." 中的前两个 "a"。 |
| [n{X,}](https://www.runoob.com/jsref/jsref-regexp-nxcomma.html) | X 是一个正整数。前面的模式 n 连续出现至少 X 次时匹配。例如，/a{2,}/ 不匹配 "candy" 中的 "a"，但是匹配 "caandy" 和 "caaaaaaandy." 中所有的 "a"。 |
| [n{X,Y}](https://www.runoob.com/jsref/jsref-regexp-nxy.html) | X 和 Y 为正整数。前面的模式 n 连续出现至少 X 次，至多 Y 次时匹配。例如，/a{1,3}/ 不匹配 "cndy"，匹配 "candy," 中的 "a"，"caandy," 中的两个 "a"，匹配 "caaaaaaandy" 中的前面三个 "a"。注意，当匹配 "caaaaaaandy" 时，即使原始字符串拥有更多的 "a"，匹配项也是 "aaa"。 |
| [n$](https://www.runoob.com/jsref/jsref-regexp-ndollar.html) | 匹配任何结尾为 n 的字符串。 |
| [^n](https://www.runoob.com/jsref/jsref-regexp-ncaret.html) | 匹配任何开头为 n 的字符串。 |
| [?=n](https://www.runoob.com/jsref/jsref-regexp-nfollow.html) | 匹配任何其后紧接指定字符串 n 的字符串。 |
| [?!n](https://www.runoob.com/jsref/jsref-regexp-nfollow-not.html) | 匹配任何其后没有紧接指定字符串 n 的字符串。 |

### RegExp 对象方法

| 方法 | 描述 |
|-|-|
| [compile](https://www.runoob.com/jsref/jsref-regexp-compile.html) | 在 1.5 版本中已废弃。 编译正则表达式。 |
| [exec](https://www.runoob.com/jsref/jsref-exec-regexp.html) | 检索字符串中指定的值。返回找到的值，并确定其位置。 |
| [test](https://www.runoob.com/jsref/jsref-test-regexp.html) | 检索字符串中指定的值。返回 true 或 false。 |
| [toString](https://www.runoob.com/jsref/jsref-regexp-tostring.html) | 返回正则表达式的字符串。 |

### 支持正则表达式的 String 对象的方法

| 方法 | 描述 | FF | IE |
|-|-|-|-|
| [search](https://www.runoob.com/js/jsref-search.html) | 检索与正则表达式相匹配的值。 | 1 | 4 |
| [match](https://www.runoob.com/js/jsref-match.html) | 找到一个或多个正则表达式的匹配。 | 1 | 4 |
| [replace](https://www.runoob.com/js/jsref-replace.html) | 替换与正则表达式匹配的子串。 | 1 | 4 |
| [split](https://www.runoob.com/js/jsref-split.html) | 把字符串分割为字符串数组。 | 1 | 4 |

* * *

### RegExp 对象属性

| 属性 | 描述 |
|-|-|
| [constructor](https://www.runoob.com/jsref/jsref-regexp-constructor.html) | 返回一个函数，该函数是一个创建 RegExp 对象的原型。 |
| [global](https://www.runoob.com/jsref/jsref-regexp-global.html) | 判断是否设置了 "g" 修饰符 |
| [ignoreCase](https://www.runoob.com/jsref/jsref-regexp-ignorecase.html) | 判断是否设置了 "i" 修饰符 |
| [lastIndex](https://www.runoob.com/jsref/jsref-lastindex-regexp.html) | 用于规定下次匹配的起始位置 |
| [multiline](https://www.runoob.com/jsref/jsref-multiline-regexp.html) | 判断是否设置了 "m" 修饰符 |
| [source](https://www.runoob.com/jsref/jsref-source-regexp.html) | 返回正则表达式的匹配模式 |

## 一些例子

```js
var str="Visit Runoob. Hello World!";
var patt1=/\127/g;
str.match(patt1);
```
结果如下：Visit Runoob. Hello ***W*** orld!

\xxx 元字符用于查找以八进制数 xxx 规定的字符。

如果未找到匹配，则返回 null 。

```js
var str="Visit Runoob. Hello World!";
var patt1=/\x57/g;
str.match(patt1);
```
结果如下：Visit Runoob. Hello ***W*** orld!

\xdd 元字符查找以十六进制数 dd 规定的字符。

如果未找到匹配，则返回 null。

```js
var str="Visit W3Schools. Hello World!";
var patt1=/\u0057/g;
str.match(patt1);
```

下面 被标记 的文本显示了表达式获得匹配的位置：

Visit ***W*** 3Schools. Hello ***W*** orld!

```js
// 对至少一个 "o" 进行全局搜索：
var str="Hellooo World! Hello Runoob!"; 
var patt1=/o+/g;
str.match(patt1);
```

下面被标记的文本显示了表达式获得匹配的位置：

Hell ***ooo*** W ***o*** rld! Hell ***o*** Run ***oo*** b!