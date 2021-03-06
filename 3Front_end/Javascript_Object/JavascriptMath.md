# Javascript Math

## CONTENT

### [Math 对象属性](#Math属性)

| 属性 | 描述 |
|-|-|
| E | 返回算术常量 e，即自然对数的底数（约等于2.718）。 |
| LN2 | 返回 2 的自然对数（约等于0.693）。 |
| LN10 | 返回 10 的自然对数（约等于2.302）。 |
| LOG2E | 返回以 2 为底的 e 的对数（约等于 1.4426950408889634）。 |
| LOG10E | 返回以 10 为底的 e 的对数（约等于0.434）。 |
| PI | 返回圆周率（约等于3.14159）。 |
| SQRT1_2 | 返回 2 的平方根的倒数（约等于 0.707）。 |
| SQRT2 | 返回 2 的平方根（约等于 1.414）。 |

&hearts; 注意：以上属性，大小写，数值都不能打错，否则没那个属性。

### [Math 对象方法](#Math方法)

| 方法 | 描述 |
|-|-|
| abs(x) | 返回 x 的绝对值。 |
| acos(x) | 返回 x 的反余弦值。 |
| asin(x) | 返回 x 的反正弦值。 |
| atan(x) | 以介于 -PI/2 与 PI/2 弧度之间的数值来返回 x 的反正切值。 |
| atan2(y,x) | 返回从 x 轴到点 (x,y) 的角度（介于 -PI/2 与 PI/2 弧度之间）。 |
| ceil(x) | 对数进行上舍入。 |
| cos(x) | 返回数的余弦。 |
| exp(x) | 返回 E^x 。 |
| floor(x) | 对 x 进行下舍入。 |
| log(x) | 返回数的自然对数（底为e）。 |
| max(x,y,z,...,n) | 返回 x,y,z,...,n 中的最高值。 |
| min(x,y,z,...,n) | 返回 x,y,z,...,n中的最低值。 |
| pow(x,y) | 返回 x 的 y 次幂。 |
| random() | 返回 0 ~ 1 之间的随机数。 |
| round(x) | 四舍五入。 |
| sin(x) | 返回数的正弦。 |
| sqrt(x) | 返回数的平方根。 |
| tan(x) | 返回角的正切。 |


## Math属性
```js
console.log(
  Math.E,
  Math.LN2,
  Math.LN10,
  Math.LOG2E,
  Math.LOG10E,
  Math.PI,
  Math.SQRT1_2,
  Math.SQRT2,
  Math.E,
);
// 2.718281828459045 0.6931471805599453 2.302585092994046 1.4426950408889634 0.4342944819032518 3.141592653589793 0.7071067811865476 1.4142135623730951 2.718281828459045
```

## Math方法

略

```js
console.log(Math.random().toString().slice(2,8)); // 生成6位随机数
```
