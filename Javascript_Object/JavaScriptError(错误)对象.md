# JavaScript Error(错误) 对象
## Error 对象
Error 对象在错误发生时提供了错误的提示信息。

JavaScript 更多错误的内容可以参考：[JavaScript 错误 - throw、try 和 catch](https://www.runoob.com/js/js-errors.html)
```js
try {
    adddlert("Welcome guest!");
}
catch(err) {
    document.getElementById("demo").innerHTML = 
    err.name + "<br>" + err.message;
}
/*
以下实例中 try 语句块包含了未定义的函数 "adddlert" ，执行它会产生错误，catch 语句块会输出该错误的信息。

ReferenceError
adddlert is not defined
*/
```
* * *

## Error 对象属性

| 属性 | 描述 |
|-|-|
| [name](#name) | 设置或返回一个错误名 |
| [message](#message) | 设置或返回一个错误信息(字符串) |

### name
`name` 属性用于设置或返回错误名。

`name` 属性可以返回以下 6 个不同的值。

| 错误名 | 描述 | 实例 |
|-|-|-|
| EvalError | eval() 函数产生的错误。 **注意:** 新版的 JavaScript 使用 **SyntaxError** 替代 EvalError。 |   |
| RangeError | 数值超出规定的范围 | [尝试一下](https://www.runoob.com/try/try.php?filename=tryjsref_error_range) |
| ReferenceError | 非法引用 | [尝试一下](https://www.runoob.com/try/try.php?filename=tryjsref_error_reference) |
| SyntaxError | 语法错误 | [尝试一下](https://www.runoob.com/try/try.php?filename=tryjsref_error_syntax) |
| TypeError | 类型错误 | [尝试一下](https://www.runoob.com/try/try.php?filename=tryjsref_error_type) |
| URIError | encodeURI() 函数产生的错误 | [尝试一下](https://www.runoob.com/try/try.php?filename=tryjsref_error_uri) |

**语法**

`errorObj.name`

### message

`message` 属性用于设置或返回错误信息

**语法**

`errorObj.message`