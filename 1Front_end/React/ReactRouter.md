# ReactRouter

>学习地址：https://www.bilibili.com/video/av61672919
>
>demo04(动态传值重定向)地址：https://github.com/Allenem/ReactDraft/tree/master/jishupang/demo04
>
>demo05(路由嵌套)地址：https://github.com/Allenem/ReactDraft/tree/master/jishupang/demo05

## CONTENT

- [ReactRoute开安环境配置和安装](#ReactRoute开安环境配置和安装)
- [ReactRoute精确匹配和页面分离](#ReactRoute精确匹配和页面分离)
- [ReactRoute动态传值](#ReactRoute动态传值)
- [ReactRoute重定向-Redirect的使用](#ReactRoute重定向-Redirect的使用)
- [ReactRoute嵌套路由](#ReactRoute嵌套路由)
- [后台动态获取路由进行匹配](#后台动态获取路由进行匹配)

---

## ReactRoute开安环境配置和安装

>以下为demo04(动态传值重定向)地址：https://github.com/Allenem/ReactDraft/tree/master/jishupang/demo04

安装 `react-router-dom` ，实现基本路由跳转即可，首页/列表页 能够互相跳转。

```bash
create-react-app demo04
cd demo04
yarn add babel-loader
yarn add react-router-dom
yarn start
```

`index.js`

```js
import React from 'react';
import ReactDOM from 'react-dom';
import AppRouter from './AppRouter';

ReactDOM.render(<AppRouter />, document.getElementById('root'));
```

`AppRouter.js`

```js
import React from 'react';
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';

function Index(){
  return <h2>Allenem.com</h2>
}

function List(){
  return <h2>List-page</h2>
}

function AppRouter(){
  return (
    <Router>
      <ul>
        <li><Link to="/">首页</Link></li>
        <li><Link to="/list">列表</Link></li>
      </ul>
      {/* exact 精确匹配 */}
      <Route path="/" exact component={Index} />
      <Route path="/list" exact component={List} />
    </Router>
  )
}

export default AppRouter
```

---

## ReactRoute精确匹配和页面分离

新建 `src/pages/Index.js` `src/pages/List.js`

```js
import React, { Component } from 'react';

class Index extends Component {
  constructor(props) {
    super(props);
    this.state = {  }
  }
  render() { 
    return ( <h2>Allenem.com</h2> );
  }
}
 
export default Index;
```

```js
import React, { Component } from 'react';

class List extends Component {
  constructor(props) {
    super(props);
    this.state = {  }
  }
  render() { 
    return ( <h2>List-page</h2> );
  }
}
 
export default List;
```

修改 `AppRouter.js`

```js
import React from 'react';
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';
+ import Index from './pages/Index'
+ import List from './pages/List'

-
/*
function Index(){
  return <h2>Allenem.com</h2>
}

function List(){
  return <h2>List-page</h2>
}
*/

function AppRouter(){
  return (
    <Router>
      <ul>
        <li><Link to="/">首页</Link></li>
        <li><Link to="/list">列表</Link></li>
      </ul>
      <Route path="/" exact component={Index} />
      <Route path="/list" component={List} />
    </Router>
  )
}

export default AppRouter
```

---

## ReactRoute动态传值

### 业务逻辑：设置规则，传递值，接收值，显示内容

设置规则：在 `AppRouter.js` 中
```jsx
<Route path="/list/:id" component={List} />
```

传递值：在 `AppRouter.js` 中
```jsx
<li><Link to="/list/123">列表</Link></li>
```

接收值：在 `src/pages/List.js` 的生命周期函数中
```js
  render() { 
    return ( <h2>List-page->{this.state.id}</h2> );
  }
  componentDidMount(){
    // console.log(this.props)
    let tempId = this.props.match.params.id
    this.setState({id:tempId})
  }
```
this.props.match有三个关键信息：
```
params: {id: "123"}
path: "/list/:id"
url: "/list/123"
```

### 进阶

在 `src/pages/Index.js` 创建链接条目

```js
import React, { Component } from 'react';
import { Link } from 'react-router-dom';

class Index extends Component {
  constructor(props) {
    super(props);
    this.state = { 
      list: [
        {cid:123,title:'博文1'},
        {cid:456,title:'博文2'},
        {cid:789,title:'博文3'}
      ]
     }
  }
  render() { 
    return ( 
      <div>
        <h2>Allenem.com</h2> 
        <ul>
          {
            this.state.list.map((item,index) => {
              return(
                <li key={index}>
                  <Link to={'/list/'+item.cid}>{item.title}</Link>
                </li>
              )
            })
          }
        </ul>
      </div>
    );
  }
}
 
export default Index;
```

首页显示如下，前面有点的皆可跳转：

```
. 首页
. 列表
Allenem.com
. 博文1
. 博文2
. 博文3
```

---

## ReactRoute重定向-Redirect的使用

两种跳转方式：标签跳转，编程跳转

1. 标签跳转

新建 `src/pages/Home.js`
```js
import React, { Component } from 'react';

class Home extends Component {
  constructor(props) {
    super(props);
    this.state = {  }
  }
  render() { 
    return ( 
      <h2>我是Home组件-Redirect</h2>
    );
  }
}
 
export default Home;
```

修改 `src/pages/Index.js`
```js
import { Link , Redirect } from 'react-router-dom';
...
  render() { 
    return ( 
      <div>
      <Redirect to='/home/' />
...
```

修改 `AppRouter.js`
```js
+ import Home from './pages/Home'
+ <Route path="/home/" component={Home} />
```

2. 编程式重定向

修改 `src/pages/Index.js`
```js
import React, { Component } from 'react';
- import { Link , Redirect } from 'react-router-dom';
+ import { Link } from 'react-router-dom';

class Index extends Component {
  constructor(props) {
    super(props);
    this.state = { 
      list: [
        {cid:123,title:'博文1'},
        {cid:456,title:'博文2'},
        {cid:789,title:'博文3'}
      ]
     }
+     this.props.history.push("/home/")
  }
  render() { 
    return ( 
      <div>
-      {/*<Redirect to='/home/' />*/}
        <h2>Allenem.com</h2> 
        <ul>
          {
            this.state.list.map((item,index) => {
              return(
                <li key={index}>
                  <Link to={'/list/'+item.cid}>{item.title}</Link>
                </li>
              )
            })
          }
        </ul>
      </div>
    );
  }
}
 
export default Index;
```

---

## ReactRoute嵌套路由

>以下为demo05(路由嵌套)地址：https://github.com/Allenem/ReactDraft/tree/master/jishupang/demo05

### 安装

```bash
create-react-app demo05
cd demo05
yarn add babel-loader
yarn add react-router-dom
yarn start
```

### 文件目录

```
│  .gitignore
│  package.json
│  README.md
│  yarn.lock
│
├─public
│      favicon.ico
│      index.html
│      logo192.png
│      logo512.png
│      manifest.json
│      robots.txt
│
└─src
    │  AppRouter.js
    │  index.css
    │  index.js
    │
    └─pages
        │  Index.js
        │  Video.js
        │  Workplace.js
        │
        ├─video
        │      Flutter.js
        │      Reactpage.js
        │      Vue.js
        │
        └─workplace
                English.js
                Math.js
                Politics.js
```

`index.css` 样式
```css
body{
  padding: 0px;
  margin: 0px;
}

.mainDiv{
  display: flex;
  width: 100%;
}
.leftNav{
  width: 16%;
  background-color: #c0c0c0;
  color:#333;
  font-size:24px;
  height: 1000px;
  padding: 20px;
}
.rightMain{
  width: 84%;
  height:1000px;
  background-color: #fff;
  font-size:20px;
  
}

.topNav{
  height:50px ;
  background-color: #cfdefd;
}
.topNav ul{
 display: flex; 
 margin: 0px;
 padding: 0px;
}
.topNav li{
 padding: 10px;
 text-align: center;
 list-style: none;
}
.videoContent{
   padding:20px;
}
```

`index.js` 入口
```js
import React from 'react';
import ReactDOM from 'react-dom';
import AppRouter from './AppRouter';

ReactDOM.render(<AppRouter />, document.getElementById('root'));
```

`AppRouter.js` 存放一级导航
```js
import React from 'react';
import { BrowserRouter as Router, Route, Link } from 'react-router-dom';
import './index.css'
import Index from './pages/Index';
import Video from './pages/Video';
import Workplace from './pages/Workplace';

function AppRouter(){
  return(
    <Router>
      <div className="mainDiv">
        <div className="leftNav">
          <h3>一级导航</h3>
          <ul>
            <li><Link to="/">博客首页</Link></li>
            <li><Link to="/video">视频教程</Link></li>
            <li><Link to="/workplace">职场技能</Link></li>
          </ul>
        </div>
        <div className="rightMain">
          <Route path="/" exact component={Index} />
          <Route path="/video/"  component={Video} />
          <Route path="/workplace/"  component={Workplace} />
        </div>
      </div>
    </Router>
  )
}

export default AppRouter
```

`src/pages/Index.js` 首页
```js
import React from 'react';

function Index(){
  return(
    <h2>我是博客首页</h2>
  )
}

export default Index
```

`src/pages/Video.js` 视频页，存放二级导航
```js
import React from 'react';
import {  Route, Link } from 'react-router-dom';
import Flutter from './video/Flutter';
import Reactpage from './video/Reactpage';
import Vue from './video/Vue';

function Video(){
  return(
    <div>
      <div className="topNav">
        <ul>
          <li><Link to="/video/flutter">Flutter教程</Link></li>
          <li><Link to="/video/reactpage">React教程</Link></li>
          <li><Link to="/video/vue">Vue教程</Link></li>
        </ul>
      </div>
      <div className="videoContent">
        <div><h3>视频教程</h3></div>
        <Route path="/video/flutter/" component={Flutter} />
        <Route path="/video/reactpage/" component={Reactpage} />
        <Route path="/video/vue/" component={Vue} />
      </div>
    </div>
  )
}

export default Video
```

`src/pages/video/flutter.js` 二级路由页
```js
import React from 'react';

function Flutter(){
  return(
    <h2>我是Flutter</h2>
  )
}

export default Flutter
```

主体框架就这样，其他部分大同小异

---

## 后台动态获取路由进行匹配

`AppRouter.js` 中将获取的数据 `map` 循环渲染

```js
...

function AppRouter(){
+  let routeConfig = [
+    {path:'/',title:'博客首页', exact:true, component:Index},
+    {path:'/video',title:'视频教程', exact:false, component:Video},
+    {path:'/workplace',title:'职场技能', exact:false, component:Workplace}
+  ]

  return(
    <Router>
      <div className="mainDiv">
        <div className="leftNav">
          <h3>一级导航</h3>
          <ul>
-          {/*
-            <li><Link to="/">博客首页</Link></li>
-            <li><Link to="/video">视频教程</Link></li>
-            <li><Link to="/workplace">职场技能</Link></li>
-          */}
+          {
+            routeConfig.map((item,index) => {
+              return(
+                <li key={index}><Link to={item.path}>{item.title}</Link></li>
+              )
+            })
+          }
          </ul>
        </div>
        <div className="rightMain">
-        {/*
-          <Route path="/" exact component={Index} />
-          <Route path="/video/"  component={Video} />
-          <Route path="/workplace/"  component={Workplace} />
-          */}
+          {
+            routeConfig.map((item,index) => {
+              return(
+                <Route key={index} path={item.path} exact={item.exact}  component={item.component}/>
+              )
+            })
+          }
        </div>
      </div>
    </Router>
  )
}
...
```
最终效果如下图

![router.png](../img/React/router.png)


---

\_(:з」∠)_

完结(END)

[TOP](#)