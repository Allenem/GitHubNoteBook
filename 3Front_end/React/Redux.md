# Redux

>学习地址：https://www.bilibili.com/video/av56213747
>
>demo地址(use thunk or saga)：https://github.com/Allenem/ReactDraft/tree/master/jishupang/demo02
>
>demo地址(use React-Redux)：https://github.com/Allenem/ReactDraft/tree/master/jishupang/demo03

## CONTENT

- [Redux简介](#Redux简介)
- [使用create-react-app生成demo02，引入ant-design](#使用create-react-app生成demo02引入ant-design)
- [安装使用redux](#安装使用redux)
- [Chrome 添加拓展程序 Redux DevTools](#Chrome添加拓展程序ReduxDevTools)
- [通过Input初体验Redux的流程](#通过Input初体验Redux的流程)
- [运用Redux基本完成Todolist](#运用Redux基本完成Todolist)
- redux小技巧
  - [redux小技巧1](#redux小技巧1)
  - [redux小技巧2](#redux小技巧2)
- [redux填三个小坑](#redux填三个小坑)
- [组件UI和业务逻辑的拆分](#组件UI和业务逻辑的拆分)
- [无状态组件](#无状态组件)
- [Axios异步请求获取数据并和Redux结合](#Axios异步请求获取数据并和Redux结合)
- Redux-thunk
  - [Redux-thunk中间件的安装和配置](#Redux-thunk中间件的安装和配置)
  - [Redux-thunk中间件的使用](#Redux-thunk中间件的使用)
- Redux-saga
  - [Redux-saga的安装和配置](#Redux-saga的安装和配置)
  - [Redux-saga的使用(获取list)](#Redux-saga的使用获取list)
- React-Redux
  - [React-Redux插件介绍和安装](#React-Redux插件介绍和安装)
  - [React-Redux的Provider和Connect](#React-Redux的Provider和Connect)
  - [React-Redux修改Store中state的值](#React-Redux修改Store中state的值)
  - [React-Redux增加和删除list的值](#React-Redux增加和删除list的值)
  - [代码优化](#代码优化)

---

## Redux简介

![redux001.jpg](../img/React/redux001.jpg)
![redux_flow.png](../img/React/redux_flow.png)
![redux_flow_me.png](../img/React/redux_flow_me.png)
![redux_flow_book.png](../img/React/redux_flow_book.png)

---

## 使用create-react-app生成demo02，引入ant-design

以下代码在 [demo02](https://github.com/Allenem/ReactDraft/tree/master/jishupang/demo02)

### 安装

```bash
create-react-app demo02
cd demo02
yarn add antd
yarn start
```

浏览器打开 localhost:3000
![Reactnewinterface.png](../img/React/Reactnewinterface.png)

### 引入

```js
import React, { Component } from 'react';
import 'antd/dist/antd.css';
import { Input , Button , List } from 'antd';

const data = [
  '早上8点背单词',
  '早上9点学政治',
  '早上10点写数学'
]

class Todolist extends Component {

  render() { 
    return ( 
      <div style={{margin:'10px'}}>
        <div>
          <Input 
            placeholder='Write Something'
            style={{ width:'250px',marginRight:'10px' }}
          />
          <Button type='primary'>增加</Button>
        </div>
        <div style={{margin:'10px',width:'300px'}}>
          <List
            bordered
            dataSource={data}
            renderItem={item=>(<List.Item>{item}</List.Item>)}
          />
        </div>
      </div>
     );
  }

}
 
export default Todolist;
```

结果有报错
```
Module not found: Can't resolve node_modules\babel-loader\lib\index.js in ...
```

重新安装 `babel-loader` 即可
```bash
yarn add babel-loader
# OR
npm install babel-loader -S
```

---

## 安装使用redux

```bash
yarn add redux
```

数据抽离，新建下面2个文件

1. `src/store/index.js`

```js
import { createStore } from 'redux'
import reducer from './reducer'

const store = createStore(reducer)

export default store
```

2. `src/store/reducer.js` 

```js
const defaultState = {
  inputValue:'Write something',
  list: [
    '早上8点背单词',
    '早上9点学政治',
    '早上10点写数学'
  ]
}

export default (state = defaultState,action) => {
  return state
}
```

改变原来的 `Todolist.js`

```js
import store from './store';

  constructor(props){
    super(props)
    // console.log(store.getState())
    this.state = store.getState()
  }

  render(){
    return(
      <Input 
        placeholder={this.state.inputValue}
        style={{ width:'250px',marginRight:'10px' }}
      />

      <List
        bordered
        dataSource={this.state.list}
        renderItem={item=>(<List.Item>{item}</List.Item>)}
      />
      
    )
  }
  
```

---

## Chrome添加拓展程序ReduxDevTools

科嗯学嗯上嗯网之后在这里添加`Redux DevTools`：

https://chrome.google.com/webstore/detail/redux-devtools/lmhkpmbekcpmknklioeibfkpmmfibljd?hl=zh-CN

配置详见：

https://github.com/zalmoxisus/redux-devtools-extension#usage

简单设置：

在 `src/store/index.js` 中添加一句话

```js
const store = createStore(
  reducer, /* preloadedState, */
+ window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
);
```

---

## 通过Input初体验Redux的流程

`Todolist.js`
```js
...

class Todolist extends Component {

  constructor(props){
    ...
    // 一定要订阅，否则input的value绑定会报错
    this.storeChange = this.storeChange.bind(this)
    store.subscribe(this.storeChange)
  }

  render() { 
    return ( 
      ...
          <Input 
            placeholder={this.state.inputValue}
            value={this.state.inputValue}
            style={{ width:'250px',marginRight:'10px' }}
            onChange={this.changeInputValue}
          />
      ...
     );
  }

  // react component -> action …> store -> reducer
  changeInputValue(e){
    const action = {
      type: 'changeInput',
      value: e.target.value
    }
    store.dispatch(action)
  }

  // reducer -> store -> react component
  storeChange(){
    this.setState(store.getState())
  }

}
 
...
```

`src/store/index.js`啥都不变

`src/store/reducer.js`
```js
const defaultState = {
  inputValue:...,
  list: [
    ...
  ]
}

export default (state = defaultState,action) => {
  console.log(state,action)
  // Reducer里只能接受state，不能改变state
  if(action.type==='changeInput'){
    // 深拷贝
    let newState = JSON.parse(JSON.stringify(state))
    newState.inputValue = action.value
    return newState
  }
  return state
}
```

---

## 运用Redux基本完成Todolist

`Todolist.js`

```js
import React, { Component } from 'react';
import 'antd/dist/antd.css';
import { Input , Button , List } from 'antd';
import store from './store';

class Todolist extends Component {

  constructor(props){
    super(props)
    // console.log(store.getState())
    this.state = store.getState()
    this.changeInputValue = this.changeInputValue.bind(this)
    this.clickBtn = this.clickBtn.bind(this)

    this.storeChange = this.storeChange.bind(this)
    store.subscribe(this.storeChange)
  }

  render() { 
    return ( 
      <div style={{margin:'10px'}}>
        <div>
          <Input 
            placeholder={this.state.inputValue}
            value={this.state.inputValue}
            style={{ width:'250px',marginRight:'10px' }}
            onChange={this.changeInputValue}
          />
          <Button 
            type='primary'
            onClick={this.clickBtn}
          >
            增加
          </Button>
        </div>
        <div style={{margin:'10px',width:'300px'}}>
          <List
            bordered
            dataSource={this.state.list}
            renderItem={(item,index)=>(<List.Item onClick={this.deleteItem.bind(this,index)}>{item}</List.Item>)}
          />
        </div>
      </div>
     );
  }

  storeChange(){
    this.setState(store.getState())
  }

  changeInputValue(e){
    const action = {
      type: 'changeInput',
      value: e.target.value
    }
    store.dispatch(action)
  }

  clickBtn(){
    const action = {type:'addItem'}
    store.dispatch(action)
  }

  deleteItem(index){
    // console.log(index)
    const action = {
      type: 'deleteItem',
      index
    }
    store.dispatch(action)
  }

}
 
export default Todolist;
```

`src/store/index.js`

```js
import { createStore } from 'redux'
import reducer from './reducer'

const store = createStore(
  reducer,
  window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
)

export default store
```

`src/store/reducer.js`

```js
const defaultState = {
  inputValue:'Write something',
  list: [
    '早上8点背单词',
    '早上9点学政治',
    '早上10点写数学'
  ]
}

export default (state = defaultState,action) => {
  // console.log(state,action)

  // Reducer里只能接受state，不能改变state
  if(action.type==='changeInput'){
    // 深拷贝
    let newState = JSON.parse(JSON.stringify(state))
    newState.inputValue = action.value
    return newState
  }

  if(action.type==='addItem'){
    let newState = JSON.parse(JSON.stringify(state))
    newState.list.push(newState.inputValue)
    newState.inputValue = ''
    return newState
  }

  if(action.type==='deleteItem'){
    let newState = JSON.parse(JSON.stringify(state))
    newState.list.splice(action.index,1)
    return newState
  }

  return state
}
```

---

## redux小技巧1

工作中，会单独创建一个文件 `src/store/actionTypes.js` 定义 `type` 常量，在 `Todolist.js` 和 `reducer.js` 中引入

`src/store/actionTypes.js`
```js
export const CHANGE_INPUT = 'changeInput'
export const ADD_ITEM = 'addItem'
export const DELETE_ITEM = 'deleteItem'
```

`Todolist.js`
```js
import { CHANGE_INPUT , ADD_ITEM , DELETE_ITEM } from './store/actionTypes';

  changeInputValue(e){
    const action = {
      type: CHANGE_INPUT,
      value: e.target.value
    }
    store.dispatch(action)
  }

  clickBtn(){
    const action = {
      type: ADD_ITEM
    }
    store.dispatch(action)
  }

  deleteItem(index){
    // console.log(index)
    const action = {
      type: DELETE_ITEM,
      index
    }
    store.dispatch(action)
  }
```

`reducer.js`
```js
import { CHANGE_INPUT , ADD_ITEM , DELETE_ITEM } from './actionTypes';

  if(action.type===CHANGE_INPUT){
  ...
  }

  if(action.type===ADD_ITEM){
  ...
  }

  if(action.type===DELETE_ITEM){
  ...
  }
```

---

## redux小技巧2

工作中，会单独创建一个文件 `src/store/actionCreators.js` 分发许多 `action` ，在 `Todolist.js` 中引入

`src/store/actionCreators.js`
```js
import { CHANGE_INPUT , ADD_ITEM , DELETE_ITEM } from './actionTypes';

export const changeInputAction = (value) => ({
  type: CHANGE_INPUT,
  value
})

export const addItemAction = () => ({
  type: ADD_ITEM
})

export const deleteItemAction = (index) => ({
  type: DELETE_ITEM,
  index
})
```

`Todolist.js`
```js
- import { CHANGE_INPUT , ADD_ITEM , DELETE_ITEM } from './store/actionTypes';
+ import { changeInputAction , addItemAction , deleteItemAction } from './store/actionCreators';

// 修改
  changeInputValue(e){
    const action = changeInputAction(e.target.value)
    store.dispatch(action)
  }

  clickBtn(){
    const action = addItemAction()
    store.dispatch(action)
  }

  deleteItem(index){
    const action = deleteItemAction(index)
    store.dispatch(action)
  }

```

---

## redux填三个小坑

- `store` 必须是唯一的，多个 `store` 是坚决不允许，只能有一个 `store` 空间
- 只有 `store` 能改变自己的内容， `Reducer` 不能改变
- `Reducer` 必须是纯函数

1. 只有一个 `store` 是来自于 `src/store/index.js` 
2. `src/store/reducer.js` 是拷贝，修改 `newState` 传给 `src/store/index.js`,
`src/store/index.js` 自己修改 `store` 的
3. `src/store/reducer.js` 返回的值由传入的两个参数 `state` `action` 决定，不能进行 `ajax` 请求

---

## 组件UI和业务逻辑的拆分

创建 UI 组件 `src/TodolistUI.js`
```js
import React, { Component } from 'react'
import 'antd/dist/antd.css';
import { Input , Button , List } from 'antd';

class TodolistUI extends Component {
  render() { 
    return ( 
      <div style={{margin:'10px'}}>
        <div>
          <Input 
            placeholder={this.props.inputValue}
            value={this.props.inputValue}
            style={{ width:'250px',marginRight:'10px' }}
            onChange={this.props.changeInputValue}
          />
          <Button 
            type='primary'
            onClick={this.props.clickBtn}
          >
            增加
          </Button>
        </div>
        <div style={{margin:'10px',width:'300px'}}>
          <List
            bordered
            dataSource={this.props.list}
            renderItem={(item,index)=>(<List.Item onClick={()=>this.props.deleteItem(index)}>{item}</List.Item>)}
          />
        </div>
      </div>
    );
  }
}
 
export default TodolistUI;
```

修改根组件 `src/Todolist.js`
```js
- import 'antd/dist/antd.css';
- import { Input , Button , List } from 'antd';
+ import TodolistUI from './TodolistUI';

  render() { 
    return ( 
      {/* 原来的全部剪切粘贴到UI组件，这里替换为<TodolistUI />，并传值传函数，注意this的绑定 */}
      <TodolistUI
        inputValue = {this.state.inputValue}
        list = {this.state.list}
        changeInputValue = {this.changeInputValue}
        clickBtn = {this.clickBtn}
        deleteItem = {this.deleteItem}
      />
    );
  }
```

---

## 无状态组件

无状态组件： 就是一个标准的方法，没有 `class` ，没有业务逻辑，只有 `UI` ，返回 `jsx` 。

`TodolistUINoState.js` 删除引入的 `Component` ，删除 `this.` ， 函数传入 `(props)` 。

`TodolistUINoState.js`
```js
import React from 'react'
import 'antd/dist/antd.css';
import { Input , Button , List } from 'antd';

const TodolistUI = (props) => {
  return ( 
    <div style={{margin:'10px'}}>
      <div>
        <Input 
          placeholder={props.inputValue}
          value={props.inputValue}
          style={{ width:'250px',marginRight:'10px' }}
          onChange={props.changeInputValue}
        />
        <Button 
          type='primary'
          onClick={props.clickBtn}
        >
          增加
        </Button>
      </div>
      <div style={{margin:'10px',width:'300px'}}>
        <List
          bordered
          dataSource={props.list}
          renderItem={(item,index)=>(<List.Item onClick={()=>props.deleteItem(index)}>{item}</List.Item>)}
        />
      </div>
    </div>
  );
}
 
export default TodolistUI;
```


修改根组件 `src/Todolist.js`
```js
- import TodolistUI from './TodolistUI';
+ import TodolistUINoState from './TodolistUINoState';

  render() { 
    return ( 
-     <TodolistUI
+     <TodolistUINoState
        ...
      />
    );
  }
```

---

## Axios异步请求获取数据并和Redux结合

1. 安装 `axios`
```bash
yarn add axios
```

2. 修改 `Todolist.js` ，新添生命周期函数获取数据，派发 `action`

```js
- import { changeInputAction , addItemAction , deleteItemAction } from './store/actionCreators';
+ import { changeInputAction , addItemAction , deleteItemAction , getListAction} from './store/actionCreators';

...

  componentDidMount(){
    axios.get('https://www.easy-mock.com/mock/5d9a2a338c63954ea11dd4df/react-demo01/list')
    .then((res)=>{
      // console.log(res)
      const data = res.data.data
      const action = getListAction(data)
      store.dispatch(action)
    })
    .catch((err)=>console.log(err))
  }
```

3. `src/store/actionTypes.js` 新添 `export const GET_LIST = 'getList'`

4. `src/store/actionCreator.js` 新添 `action'`

```js
- import { CHANGE_INPUT , ADD_ITEM , DELETE_ITEM } from './actionTypes';
+ import { CHANGE_INPUT , ADD_ITEM , DELETE_ITEM , GET_LIST } from './actionTypes';

+ export const getListAction = (data) => ({
+   type: GET_LIST,
+   data
+ })
```

5. `src/store/reducer.js` 新添 业务逻辑

```js
- import { CHANGE_INPUT , ADD_ITEM , DELETE_ITEM } from './actionTypes';
+ import { CHANGE_INPUT , ADD_ITEM , DELETE_ITEM , GET_LIST } from './actionTypes';

-  list: [
-    '早上8点背单词',
-    '早上9点学政治',
-    '早上10点写数学'
-  ]
+  list: []

+   if(action.type === GET_LIST){
+    let newState = JSON.parse(JSON.stringify(state))
+    newState.list = action.data
+    return newState
+  }
```

---

## Redux-thunk中间件的安装和配置

![redux_action.png](../img/React/redux_action.png)

1. 安装
```bash
yarn add redux-thunk
```

2. 配置

在 `src/store/index.js` 引入

使用 `redux` 的增强函数 `compose` ，能够同时使用 `REDUX_DEVTOOLS` 和 `Redux-thunk`

```js
import { createStore , applyMiddleware , compose} from 'redux'
import reducer from './reducer'

// thunkSTART
import thunk from 'redux-thunk'
// 周期函数 enhancer 执行两个函数 ， 相当于下面那两行注释， 但注释那样不对， createStore(parameter1,parameter2)最多接收2参数
const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__?window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__({}):compose
const enhancer = composeEnhancers(applyMiddleware(thunk))

const store = createStore(
  reducer,enhancer
  // applyMiddleware(thunk),
  // window.__REDUX_DEVTOOLS_EXTENSION__ && window.__REDUX_DEVTOOLS_EXTENSION__()
)
// thunkEND

export default store
```

---

## Redux-thunk中间件的使用

将异步请求从生命周期函数移动到中间件

`Todolist.js`
```js
- import { changeInputAction , addItemAction , deleteItemAction , getListAction} from './store/actionCreators';
+ import { changeInputAction , addItemAction , deleteItemAction , getTodoListUseThunk} from './store/actionCreators';
- import axios from 'axios';
  /*
  componentDidMount(){
    axios.get('https://www.easy-mock.com/mock/5d9a2a338c63954ea11dd4df/react-demo01/list')
    .then((res)=>{
      // console.log(res)
      const data = res.data.data
      const action = getListAction(data)
      store.dispatch(action)
    })
    .catch((err)=>console.log(err))
  }
  注释部分变为下面的样子
  */
  
  componentDidMount(){
    const action = getTodoListUseThunk()
    store.dispatch(action)
  }

```

`actionCreators.js`

```js
// 新增action
+ import axios from 'axios';

export const getTodoListUseThunk = () => {
  return (dispatch) => {
    axios.get('https://www.easy-mock.com/mock/5d9a2a338c63954ea11dd4df/react-demo01/list')
    .then((res)=>{
      // console.log(res)
      const data = res.data.data
      const action = getListAction(data)
      dispatch(action)
    })
    .catch((err)=>console.log(err))
  }
}
```
---

## Redux-saga的安装和配置

安装
```bash
yarn add redux-saga
```

配置

在 `src/store/index.js`
```js
import { createStore , applyMiddleware , compose} from 'redux'
import reducer from './reducer'
// sagaSTART
import createSagaMiddleware from 'redux-saga'
import mySagas from './sagas'
const sagaMiddleware = createSagaMiddleware()
const composeEnhancers = window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__?window.__REDUX_DEVTOOLS_EXTENSION_COMPOSE__({}):compose
const enhancer = composeEnhancers(applyMiddleware(sagaMiddleware))
const store = createStore(reducer,enhancer)
sagaMiddleware.run(mySagas)
// sagaEND
export default store
```

在 `src/store/sagas.js`
```js
function* mySagas(){}
export default mySagas
```
---

## Redux-saga的使用(获取list)

`Todolist.js`
```js
- import { changeInputAction , addItemAction , deleteItemAction , getTodoListUseThunk } from './store/actionCreators';
+ import { changeInputAction , addItemAction , deleteItemAction , getTodoListUseSaga} from './store/actionCreators';
  /*
  // use thunk
  componentDidMount(){
    const action = getTodoListUseThunk()
    store.dispatch(action)
  }*/

  // use saga
  componentDidMount(){
    const action = getTodoListUseSaga()
    store.dispatch(action)
  }
```

`src/store/actionCreator.js`
```js
import { CHANGE_INPUT , ADD_ITEM , DELETE_ITEM , GET_LIST , GET_MY_LIST} from './actionTypes';

// use saga
export const getTodoListUseSaga = () => ({
  type: GET_MY_LIST
})
```

`src/store/actionTypes.js`
```js
+ export const GET_MY_LIST = 'getMyList'
```

`src/store/sagas.js`
```js
import { takeEvery , put } from 'redux-saga/effects';
import { GET_MY_LIST } from './actionTypes';
import { getListAction } from './actionCreators';
import axios from 'axios';

// generator
function* mySagas(){
  yield takeEvery(GET_MY_LIST, getList)
}

function* getList(){
  // console.log('aaa')
  // axios.get('https://www.easy-mock.com/mock/5d9a2a338c63954ea11dd4df/react-demo01/list')
  // .then((res)=>{
  //   // console.log(res)
  //   const data = res.data.data
  //   const action = getListAction(data)
  //   put(action)
  // })
  // .catch((err)=>console.log(err))

  const res = yield axios.get('https://www.easy-mock.com/mock/5d9a2a338c63954ea11dd4df/react-demo01/list')
  const action = getListAction(res.data.data)
  yield put(action) 
}

export default mySagas
```

---

## React-Redux插件介绍和安装

以下代码在 [demo03](https://github.com/Allenem/ReactDraft/tree/master/jishupang/demo03)

现生成新项目，安装 `react-redux` `redux`
```bash
create-react-app demo03
cd demo03
yarn add react-redux
yarn add redux
yarn start
```

---

## React-Redux的Provider和Connect

1. 提供器 `Provider` ， 包裹所有组件

`src/index.js`

```js
// 添加和修改如下
import { Provider } from 'react-redux';
import store from './store';

const App = (
  <Provider store={store}>
    <Todolist />
  </Provider>
)
- ReactDOM.render(<Todolist />, document.getElementById('root'));
+ ReactDOM.render(App, document.getElementById('root'));
```

2. 连接器 `connect` ，组建中连接， `store` 中的 `state` 映射成 `props`

`Todolis.js`

```js
+ import { connect } from 'react-redux';
- import store from './store';

- this.state = store.getState()
- value = {this.state.inputValue}
+ value = {this.props.inputValue}

+
// 映射器，状态映射成属性
const stateToPrpos = (state) => {
  return{
    inputValue: state.inputValue
  }
}

- export default Todolist
+ export default connect(stateToPrpos,null)(Todolist);
// 第一个是 state->props 映射，第二个是 dispatch->props 映射，暂时设为null，后面会补上
```

---

## React-Redux修改Store中state的值

`Todolist.js`

```js
- <input 
    value={this.props.inputValue} 
    onChange={this.inputChange.bind(this)}
  />
+ <input 
    value={this.props.inputValue} 
    onChange={this.props.inputChange}
  />

+
// dispatch->props 映射
const dispatchToPrpos = (dispatch) => {
  return{
    inputChange(e){
      let action = {
        type: 'change_input',
        value: e.target.value
      }
      dispatch(action)
    }
  }
}

- export default connect(stateToPrpos,nul)(Todolist);
+ export default connect(stateToPrpos,dispatchToPrpos)(Todolist);
```

`src/store/reducer.js`

```js
export default (state = defaultState,action) => {

  if(action.type === 'change_input'){
    let newState = JSON.parse(JSON.stringify(state))
    newState.inputValue = action.value
    return newState
  }

  return state
}
```

---

## React-Redux增加和删除list的值

`Todolist.js`

```js
...
class Todolist extends Component {

  render() { 
    return ( 
      <div>
        <div>
          <input value={this.props.inputValue} onChange={this.props.inputChange}/>
          <button onClick={this.props.clickBtn}>提交</button>
        </div>
        <ul>
          {
            this.props.list.map((item,index)=>{
              return(
                <li key={index+item} onClick={()=>this.props.delItem(index)}>{item}</li>
              )
            })
          }
        </ul>
      </div>
    );
  }
}
...
const dispatchToPrpos = (dispatch) => {
  return{
    inputChange(e){
      let action = {
        type: 'change_input',
        value: e.target.value
      }
      dispatch(action)
    },
    clickBtn(){
      let action = {
        type: 'add_item'
      }
      dispatch(action)
    },
    delItem(index){
      let action = {
        type: 'del_item',
        index
      }
      dispatch(action)
    }
  }
}
...
```

`src/store/reducer.js`

```js
const defaultState = {
  inputValue: 'aaa',
  list: [
    'bbb',
    'ccc',
    'ddd'
  ]
}

export default (state = defaultState,action) => {

  if(action.type === 'change_input'){
    let newState = JSON.parse(JSON.stringify(state))
    newState.inputValue = action.value
    return newState
  }

  if(action.type === 'add_item'){
    let newState = JSON.parse(JSON.stringify(state))
    newState.list.push(newState.inputValue)
    newState.inputValue = ''
    return newState
  }

  if(action.type === 'del_item'){
    let newState = JSON.parse(JSON.stringify(state))
    newState.list.splice(action.index,1)
    return newState
  }

  return state
}
```

---

## 代码优化

1. 解构赋值

`Todolist.js`中

```js
+ let { inputValue,list,inputChange,clickBtn,delItem } = this.props;
- this.props.inputValue
+ inputValue
...
```

2. 拆分出无状态组件

`Todolist.js`变为
```js
- // import React, { Component } from 'react';
+ import React from 'react';
import { connect } from 'react-redux';

- // 删除class
/*class Todolist extends Component {

  render() { 
    let { inputValue,list,inputChange,clickBtn,delItem } = this.props;
    return ( 
      <div>
        <div>
          <input value={inputValue} onChange={inputChange}/>
          <button onClick={clickBtn}>提交</button>
        </div>
        <ul>
          {
            list.map((item,index)=>{
              return(
                <li key={index+item} onClick={()=>delItem(index)}>{item}</li>
              )
            })
          }
        </ul>
      </div>
    );
  }
}
*/
+ // 变为函数
const Todolist = (props) => {
  let { inputValue,list,inputChange,clickBtn,delItem } = props;
  return ( 
    <div>
      <div>
        <input value={inputValue} onChange={inputChange}/>
        <button onClick={clickBtn}>提交</button>
      </div>
      <ul>
        {
          list.map((item,index)=>{
            return(
              <li key={index+item} onClick={()=>delItem(index)}>{item}</li>
            )
          })
        }
      </ul>
    </div>
  );
}

// state 映射器
const stateToPrpos = (state) => {
  return{
    // 数据
  }
}
// dispatch 映射器
const dispatchToPrpos = (dispatch) => {
  return{
    // 函数
  }
}

export default connect(stateToPrpos,dispatchToPrpos)(Todolist);
```

---

\_(:з」∠)_

完结(END)

[TOP](#)