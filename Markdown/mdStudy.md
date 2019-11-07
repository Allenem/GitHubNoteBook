# Markdown Study

![markdown](../img/md/markdown.png)

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

---

## 1.标题

（井号+空格）

### 示例

# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题

### 代码

```
# 一级标题
## 二级标题
### 三级标题
#### 四级标题
##### 五级标题
###### 六级标题
```

---

## 2.引用

（大于号+空格）

### 示例

>表示引用一段文字

### 代码

```md
>表示引用一段文字
```

---

## 3.序列
（星号或减号或加号+空格）

### 示例

* li1
  * li1li1
    * li1li1li1
- li2
  - li2li1
    - li2li1li1
+ li3
  + li3li1
    + li3li1li1
1. li1
2. li2
3. li3

### 代码

```md
* li1
  * li1li1
    * li1li1li1
- li2
  - li2li1
    - li2li1li1
+ li3
  + li3li1
    + li3li1li1
1. li1
2. li2
3. li3
```

---

## 4.倾斜，加粗，删除，分割线
（两端加一颗星，两端加两颗星，两端各加两~，---或***）

### 示例

*倾斜*

**加粗**

***加粗倾斜***

~~删除~~

---

***


### 代码

```md
*倾斜*

**加粗**

***加粗倾斜***

~~删除~~

---

***
```

---

## 5.表格

### 示例

|col1|col2|col3|col4|
|-|:-|:-:|-:|
|默认左对齐|左对齐|居中|右对齐|

### 代码

```md
|col1|col2|col3|col4|
|-|:-|:-:|-:|
|默认左对齐|左对齐|居中|右对齐|
```

---

## 6.链接和图片

### 示例

[本仓库地址](https://github.com/Allenem/GitHubNoteBook)

![某图片](../img/md/md.jpg)

### 代码

```md
[本仓库地址](https://github.com/Allenem/GitHubNoteBook)

![某图片](../img/md/md.jpg)
```

---

## 7.写代码（回勾号）
（行内代码用一对`；代码块用一对```，开始的三个符号后面标注语言）

### 示例

`行代码`

```js
let a = 'aaaaaaaaa';
console.log(`代码块${a}`);
```

### 代码

```md
`行代码`

```js
let a = 'aaaaaaaaa';
console.log(`代码块${a}`);
\```
```

上面代码块没有\，只是为了能够显示```

---

## 8.折叠

### 示例

<details>
<summary>View contents</summary>

- li1
- li2
- li3
- li4

</details>

### 代码

```md
<details>
<summary>View contents</summary>

- li1
- li2
- li3
- li4

</details>
```

---

## 9.一些HTML标签

### 示例

<kbd>Tab</kbd>

<!-- 注释内容，不可见 -->

<pre>aaa</pre>

<b>bold</b>

<header>    
  <h1>{{title}}</h1>
</header>
...

### 代码

```md
<kbd>Tab</kbd>

<!-- 注释内容，不可见 -->

<pre>aaa</pre>

<b>bold</b>

<header>    
  <h1>{{title}}</h1>
</header>
...
```

---

## 10.注意

`markdown` 一般换行要行末空三格，或者直接空一行