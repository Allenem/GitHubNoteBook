# JavaScript 运算符

* * *

JavaScript 运算符用于赋值，比较值，执行算术运算等。

* * *

## JavaScript 算术运算符

算术运算符用于执行两个变量或值的运算。

赋值 **y = 5**, 以下表格将向你说明算术运算符的使用：

| 运算符 | 描述 | 例子 | y 值 | x 值 | 在线实例 |
|-|-|-|-|-|-|
| + | 加法 | x = y + 2 | y = 5 | x = 7 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_add) |
| - | 减法 | x = y - 2 | y = 5 | x = 3 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_sub) |
| * | 乘法 | x = y * 2 | y = 5 | x = 10 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_mult) |
| / | 除法 | x = y / 2 | y = 5 | x = 2.5 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_div) |
| % | 余数 | x = y % 2 | y = 5 | x = 1 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_mod) |
| ++ | 自增 | x = ++y | y = 6 | x = 6 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_incr) |
|  |  | x = y++ | y = 6 | x = 5 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_incr2) |
| -- | 自减 | x = --y | y = 4 | x = 4 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_decr) |
|  |  |  x = y-- | y = 4 | x = 5 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_decr2) |

关于算术运算符，可以阅读 [JavaScript 运算符教程](https://www.runoob.com/js/js-operators.html)。

* * *

## JavaScript 赋值运算符

赋值运算符用于给 JavaScript 变量赋值。

给定 **x=10 **和** y=5**，下面的表格解释了赋值运算符：

| 运算符 | 例子 | 实例 | x 值 | 在线实例 |
|-|-|-|-|-|
| = | x = y | x = y | x = 5 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_equal) |
| += | x += y | x = x + y | x = 15 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_plusequal) |
| -= | x -= y | x = x - y | x = 5 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_minequal) |
| *= | x *= y | x = x * y | x = 50 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_multequal) |
| /= | x /= y | x = x / y | x = 2 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_divequal) |
| %= | x %= y | x = x % y | x = 0 | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_modequal) |

关于赋值运算符，可以阅读 [JavaScript 运算符教程](https://www.runoob.com/js/js-operators.html)。

* * *

## JavaScript 字符串运算符

+ 运算符， += 运算符可用于连接字符串。

给定 **text1 = "Good "**, **text2 = "Morning"**, **及 text3 = ""**, 下面的表格解释了字符串运算符的使用：

| 运算符 | 例子 | text1 | text2 | text3 | 在线实例 |
|-|-|-|-|-|-|
| + | text3 = text1 + text2 | "Good " | "Morning" |  "Good Morning" | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_string1) |
| += | text1 += text2 | "Good Morning" | "Morning" | "" | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_oper_string2) |

* * *

## 比较运算符

比较运算符用于逻辑语句的判断，从而确定给定的两个值或变量是否相等。

给定 **x=5**, 下表展示了比较运算符的使用：

| 运算符 | 描述 | 比较 | 结果 | 在线实例 |
|-|-|-|-|-|
| == | 等于 | x == 8 | false | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison1) |
|   |   | x == 5 | true | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison2) |
| === | 值及类型均相等（恒等于） | x === "5" | false | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison3) |
|   |   | x === 5 | true | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison4) |
| != | 不等于 | x != 8 | true | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison5) |
|  !== | 值与类型均不等（不恒等于） | x !== "5" | true | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison6) |
|   |   |  x !== 5 | false | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison7) |
| > | 大于 | x > 8 | false | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison8) |
| < | 小于 | x < 8 | true | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison9) |
| >= | 大于或等于 | x >= 8 | false | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison10) |
| <= | 小于或等于 | x <= 8 | *true* | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison11) |

关于比较运算符，可以阅读 [JavaScript 比较运算符教程](https://www.runoob.com/js/js-comparisons.html)。

* * *

## 条件运算符

条件运算符用于基于条件的赋值运算。

给定 **x=6 and y=3**, 下表演示了条件运算符的运算：

| 语法 | 例子 | 在线实例 |
|-|-|-|
| *变量 *= (*条件*) ?* 值1*:*值2* | voteable = (age < 18) ? "太年轻而不能":"年龄够"; | [实例 »](https://www.runoob.com/try/try.php?filename=tryjsref_comparison) |

* * *

## 逻辑运算符

逻辑运算符用来确定变量或值之间的逻辑关系。

给定 **x=6 and y=3**, 以下实例演示了逻辑运算符的使用：

| 运算符 | 描述 | 例子 |
|-|-|-|
| && | 和 | (x < 10 && y > 1) 为 true |
| \|\| | 或 | (x == 5 \|\| y == 5) 为 false |
| ! | 非 | !(x == y) 为 true |

* * *

## JavaScript 位运算符

位运算符工作于32位的数字上。任何数字操作都将转换为32位。结果会转换为 JavaScript 数字。

| 运算符 | 描述 | 例子 | 类似于 | 结果 | 十进制 |
|-|-|-|-|-|-|
| & | AND | x = 5 & 1 | 0101 & 0001 | 0001 |  1 |
| \| | OR | x = 5 \| 1 | 0101 \| 0001 | 0101 |  5 |
| ~ | 取反 | x = ~ 5 |  ~0101 | 1010 |  -6 |
| ^ | 异或 | x = 5 ^ 1 | 0101 ^ 0001 | 0100 |  4 |
| << | 左移 | x = 5 << 1 | 0101 << 1 | 1010 |  10 |
| >> | 右移 | x = 5 >> 1 | 0101 >> 1 | 0010 | 2 |
