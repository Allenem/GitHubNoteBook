# Vue学习总结

## 目录

- [vue基础知识(1-13)](#basics)
  - vue 引入，实例化
  - vue 数据 & 方法
  - vue 绑定(:)
  - vue 事件(@)
  - vue 事件修饰符(.once.prevent.stop等)
  - vue 按键修饰符(@keyup.alt.enter)
  - vue 数据双向绑定(ref,v-model)
  - vue 计算属性computed
  - vue 动态绑定css样式
  - vue v-if & v-show
  - vue v-for
  - vue 实例化多个Vue对象
  - vue 初识组件的应用
- [运用脚手架及组件知识(14-21)](#vue-cli)
  - 脚手架初识
  - SRC文件
  - 组件嵌套
  - 组件CSS作用域
  - 属性传值Props(父组件向子组件传值)
  - 传值和传引用
  - 事件传值(子组件to父组件)
  - Vue生命周期(钩子函数)
- [vue路由知识点(22-32)](#router)
  - Vue 路由和HTTP
  - Vue 只用 Bootstrap4 中的样式
  - 路由跳转
  - 路由小细节(redirect和tag)
  - 路由name属性及跳转方法
  - 路由嵌套
  - 导航守卫(全局守卫)
  - 导航守卫(路由独享-组件内守卫)
  - 复用router-view
  - 路由控制滚动行为
  - 跨域
- [vue-cli3新特性(33-37)](#vuecli3)
  - 项目搭建及介绍
  - 新出的添加插件方法
  - 全局环境变量的使用
  - 独立运行.vue文件
  - 图形页面构建项目
- [vuex基础知识(38-43)](#vuex)
  - State
  - Getter
  - Mutation
  - Action
  - mapMutations & mapActions
  - Module

## basics
## 1.vue引入，实例化
```html
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```
```js
let vue-app = new Vue({
  ...
})
```

## 2.vue数据 & 方法
```js
// 数据
data(){
  data1:'xxx'
},
// 方法
methods: {
  methodName(){
    return this.data1;
  }
}
```
```html
<button @click='methodName'>点击</button>
<!-- 或者 -->
<div>{{ methodName() }}</div>
```
方法中用data中的属性，直接使用` this.*`，不用`this.data.*`

## 3.vue绑定(`v-bind:`, `:`, `v-html:`)
### （1）属性绑定(用 `v-bind:` 或 `:` )
```js
website: 'https://github.com/'
```
```html
<a v-bind:href="website">websit</a>
<!-- 或者简写 -->
<a :href="website">websit</a>
```

### （2）标签绑定(用`v-html:`)
```js
websiteTag: "<a href='https://github.com/'>websit</a>"
```
```html
<!-- 正确 -->
<p v-html="websiteTag">websit</a>
<!-- 错误 -->
{{ websiteTag }}
<!-- 显示如下 -->
<!-- <a href='https://github.com/'>websit</a> -->
```

## 4.vue事件(用 `v-on:` 或 `@`)
&hearts; 绑定事件里方法不传参可以不加括号仍然识别为方法，但在{{}}里一定要写括号才会识别为方法

eg: 传参单击双击事件

```js
methods: {
  add: function(val){
    this.age += val;
  },
  dec: function(val){
    this.age -= val;
  },
}
```

```html
<button v-on:click='add(1)'>加一岁</button>
<button @click='dec(1)'>减一岁</button>
<button v-on:dblclick='add(10)'>加十岁</button>
<button @dblclick='dec(10)'>减十岁</button>
```

## 5.vue事件修饰符(.once.prevent.stop等)
在事件处理程序中调用 `event.preventDefault()` 或 `event.stopPropagation()` 是非常常见的需求。尽管我们可以在方法中轻松实现这点，但更好的方式是：方法只有纯粹的数据逻辑，而不是去处理 DOM 事件细节。

为了解决这个问题，Vue.js 为 v-on 提供了事件修饰符。之前提过，修饰符是由点开头的指令后缀来表示的。

- .stop
- .prevent
- .capture
- .self
- .once
- .passive

```html
<!-- 阻止单击事件继续传播 -->
<a v-on:click.stop="doThis"></a>

<!-- 提交事件不再重载页面 -->
<form v-on:submit.prevent="onSubmit"></form>

<!-- 修饰符可以串联 -->
<a v-on:click.stop.prevent="doThat"></a>

<!-- 只有修饰符 -->
<form v-on:submit.prevent></form>

<!-- 添加事件监听器时使用事件捕获模式 -->
<!-- 即元素自身触发的事件先在此处理，然后才交由内部元素进行处理 -->
<div v-on:click.capture="doThis">...</div>

<!-- 只当在 event.target 是当前元素自身时触发处理函数 -->
<!-- 即事件不是从内部元素触发的 -->
<div v-on:click.self="doThat">...</div>
```
	
&hearts; 使用修饰符时，顺序很重要；相应的代码会以同样的顺序产生。因此，用 v-on:click.prevent.self 会阻止所有的点击，而 v-on:click.self.prevent 只会阻止对元素自身的点击。

## 6.vue按键修饰符(@keyup.alt.enter)
在监听键盘事件时，我们经常需要检查详细的按键。Vue 允许为 v-on 在监听键盘事件时添加按键修饰符：
```html
<!-- 只有在 `key` 是 `Enter` 时调用 `vm.submit()` -->
<input v-on:keyup.enter="submit">
```
你可以直接将 KeyboardEvent.key 暴露的任意有效按键名转换为 kebab-case 来作为修饰符。
```html
<input v-on:keyup.page-down="onPageDown">
```
在上述示例中，处理函数只会在 $event.key 等于 PageDown 时被调用。

&hearts; 按键码 keyCode 的事件用法已经被废弃了并可能不会被最新的浏览器支持。

使用 keyCode 特性也是允许的：
```html
<input v-on:keyup.13="submit">
```
为了在必要的情况下支持旧浏览器，Vue 提供了绝大多数常用的按键码的别名：
- .enter
- .tab
- .delete (捕获“删除”和“退格”键)
- .esc
- .space
- .up
- .down
- .left
- .right

## 7.vue数据双向绑定(ref,v-model)

### 方法一
```html
  <input ref='name' type="text" @keyup='logName'>
```
```js
  this.name = this.$refs.name.value;
```

### 方法二
```html
  <input v-model='age' type="text">
```

## 8.vue计算属性computed

`methods` 中的每个方法每次渲染dom都会执行 调用 `{{xxx()}}`

`computed` 中的每个方法只会在自己触发时执行 调用 `{{xxx}}`，案例中拷贝的值与虚拟dom不同，就执行。

## 9.vue动态绑定css样式

```html
<!-- active类名，isActive类值 -->
<div v-bind:class="{ active: isActive }"></div>
```

## 10.v-if & v-show
条件不成立时：v-if在dom中直接删除元素；v-show改变class为display:none

eg：
```html
  <button @click='err=!err'>err</button>
  <button @click='success=!success'>success</button>
  <p v-if='err'>err</p>
  <p v-else-if='success'>200</p>
  <p v-show='err'>err</p>
  <p v-show='success'>200</p>
```

## 11.v-for
&hearts; 记得绑定key值
```js
  data: {
    users:[
      {name:'hurry',age:20},
      {name:'luccy',age:25},
      {name:'zero',age:18},
    ]
  },
```
```html
  <ul v-for='(item,index) in users' :key='index'>
    <li>{{index+1}} - {{item.name}} - {{item.age}}</li>
  </ul>
  <!-- 会多出3个div -->
  <div v-for='(item,index) in users' :key='index'>
    <h2>{{item.name}}</h2>
    <p>{{index+1}} - {{item.age}}</p>
  </div>
  <!-- 不会多出3个template -->
  <template v-for='(item,index) in users' :key='index'>
    <h2>{{item.name}}</h2>
    <p>{{index+1}} - {{item.age}}</p>
  </template>
```

## 12.实例化多个Vue对象

### 多个vue对象实例化
```js
var one = new Vue({...})

var two = new Vue({...})
```

### 不同对象使用其他对象数据

**one.data**

eg:
```js
var one = new Vue({
  el: '#vue-app-one',
  data: {
    title: 'one 的内容'
  },
  methods: {
    
  },
  computed: {
    greet:function(){
      return 'hello app one';
    }
  },
});

var two = new Vue({
  el: '#vue-app-two',
  data: {
    title: 'two 的内容'
  },
  methods: {
    changeTitle:function(){
      one.title = 'title one changed by app two!!!';
    }
  },
  computed: {
    greet:function(){
      return 'hello app one';
    }
  },
});
```

## 13.vue初识组件的应用

js中：
```js
// greeting 是组件名，可在 #vue-app-one，#vue-app-two 中使用
Vue.component("greeting",{
  // 所有标签必须在一个大标签下
  template:`
  <div>
    <p> {{name}}：大家好，给大家介绍一下我的朋友@关晓彤</p>
    <button @click='changeName'>点我</button> 
  </div>
  `,
  // return一个对象则在组件内是私有的，不会暴露出去
  data:function(){
    return {
      name:'鹿晗'
    }
  },
  methods:{
    changeName:function(){
      this.name = this.name == '鹿晗'?'Hery':'鹿晗'
    }
  }
})

new Vue({
  el: '#vue-app-one'
});

new Vue({
  el: '#vue-app-two'
});
```

HTML中：
```html
<greeting></greeting>
```

## vue-cli
## 14.vue脚手架初识

### 部分特点
- 脚手架是通过webpack搭建的开发环境
- 使用es6语法
- 打包和压缩js为一个文件
- 项目在环境中编译，而不是浏览器
- 实现页面自动刷新
- ...

### vue-cli的使用
- 安装 nodejs ，一般选择安装LTS（长期稳定版）版本。[官网：https://nodejs.org/en/](https://nodejs.org/en/)
  ```bash
  # 在terminal、cmd、powershell 中
  # 输入 `node -v` 查看 node 版本号
  node -v
  ```
  ```bash
  # 输入 `npm -v` 查看 npm 版本号
  npm -v
  ```
- 安装 cnpm
  ```bash
  npm install -g cnpm --registry=https://registry.npm.taobao.org
  ```
- 安装 Vue CLI 3.x
  ```bash
  npm install -g @vue/cli
  # OR
  yarn global add @vue/cli
  ```
  ```bash
  # 输入 `vue --version` 查看 npm 版本号
  vue --version
  # OR
  vue -V
  ```
- 创建一个 Vue 项目
  ```bash
  vue create projectName

  cd projectName

  npm run serve
  ```
  ```bash
  # 创建项目相关帮助
  vue create --help
  ```
- 运行相关
  ```bash
  # Project setup
  npm install
  # Compiles and hot-reloads for development
  npm run serve
  # Compiles and minifies for production
  npm run build
  # Run your tests
  npm run test
  # Lints and fixes files
  npm run lint
  ```
- (PS)旧版本 Vue CLI 2.x
  ```bash
  npm install -g @vue/cli-init
  # `vue init` 的运行效果将会跟 `vue-cli@2.x` 相同
  vue init webpack my-project
  ```

## 15.介绍脚手架搭建的项目中SRC文件流程及根组件App

```bash
client
│  .gitignore
│  babel.config.js
│  package.json
│  README.md
│
├─public
│    favicon.ico
│    index.html
│
└─src
    │  App.vue
    │  main.js
    │  router.js
    │
    ├─assets
    │      bg.jpg
    │
    └─components
           Component1.vue
           Component2.vue
```

index.html -> main.js -> App.vue ()

```html
<!-- 模板 -->
<template></template>
<!-- 逻辑 -->
<script></script>
<!-- 样式 -->
<style></style>
```

## 16.组件嵌套

### 可以在main.js中注册全局组件
```js
import Users from './component/Users'

Vue.component('users',Users);
```

### 也可以在某些组件中调用
```html
<template>
  <div id="app">
    <Users></Users>
  </div>
</template>

<script>
import Users from './components/Users'
export default {
  components:{
    'Users':Users
  }
}
</script>
```

## 17.组件CSS作用域

```html
<style scoped>
/* `scoped`该组件作用域内有效 */
/* 否则子组件相同选项样式会覆盖根组件的 */
</style>
```

## 18.属性传值Props(父组件向子组件传值)

### 父组件：
在调用子组件的位置，绑定自己的属性，**第一个是子组件中的名称**，**第二个是父组件中的名称**。

eg:
```html
<Users :usersSon='users'></Users>
```

### 子组件：
子组件属性 `props:['usersSon'],` 接收传值。或者用标准写法

```js
props:{
  users:{
    type:Array;
    requied:true;
  },
  position:{
    type:Array;
    requied:true;
  },
},
```

eg:
```html
<template>
  <div class="users">
    <ul>
      <li v-for="(user,index) in usersSon" :key="index" @click="user.show = !user.show">
        <h2>{{user.name}}</h2>
        <h3 v-show="user.show">{{user.position}}</h3>
      </li>
    </ul>
  </div>
</template>

<script>
  export default {
    name:'users',
    props:['usersSon'],
  }
</script>
```

## 19.传值和传引用

>传值：string number boolean，一处变，全部变

>引用：array object，一处变，局部变

## 20.事件传值(子组件to父组件)

### 子组件
```html
<h1 @click="tofather">{{title1}} {{title}}</h1>
<script>
export default {
  methods: {
    tofather: function(){
      this.$emit('changed','son to father') //第1个参数是事件名，第2个参数是传递的值
    }
  },
}
</script>
```

### 父组件
```html
<Header @changed='update($event)' :title="title"></Header>
<!-- $event不能改 -->

<script>
export default {
  methods: {
    update:function(title){
      this.title = title;
    }
  },
}
</script>
```

## 21.Vue生命周期(钩子函数)

**作用**：可以找错误，可以解决需求

**生命周期图示（红色为生命周期函数）：**
![生命周期图示](https://cn.vuejs.org/images/lifecycle.png)

```js
// 8个钩子函数与 methods 并列。

// 创建对象之前(比如加载动画)
beforeCreate(){}

// 创建vue对象
new Vue()

// 组件创建成功，属性已经绑定，dom还未生成(比如获取数据，待会儿展示到dom，结束加载)
created(){}

// 检查 el 或者 new({...}).$mount('#app) ，都没有则生命周期结束

// 检查有没 template 或者 outerHTML ，都没有则生命周期结束

// 开始编译模板 template 里的内容，挂载前，虚拟dom中执行，看不到
beforeMount(){}

// el 中已经放入 template ，编译结束，此方法执行后，页面显示
mounted(){}

// 组件更新之前
beforeUpdate(){}

// 组件更新之后
updated(){}

// 组件销毁之前
beforeDestroy(){}

// 组件销毁之后
destroyed(){}

```

## router
## 22.Vue路由和HTTP

### (1) 安装路由模块及引入
```bash
npm install vue-router --save
```
router.js中
```js
import Vue from 'vue'
import Router from 'vue-router'
import Home from './components/Home.vue'
import HelloWorld from './components/HelloWorld.vue'

Vue.use(Router);

export default new Router({
  mode: 'history', // 没有#符号
  base: process.env.BASE_URL,
  routes: [
    {
      path: '/',
      name: 'home',
      component: Home
    },
    {
      path: '/helloworld',
      name: '',
      component: HelloWorld
    }
  ]
})
```
main.js中
```js
import router from './router';

new Vue({
  router,
  ...
});
```

App.vue
```html
    <ul>
      <li><a href="/">Home</a></li>
      <li><a href="/helloworld">Hello</a></li>
      <!-- 或者 -->
      <li><router-link to="/">Home</router-link></li>
      <li><router-link to="/helloworld">Hello</router-link></li>
    </ul>
    <router-view></router-view>
```

### (2) HTTP
安装依赖:

```bash
npm i vue-resource --save
```
使用:

main.js中
```js
import VueResource from 'vue-resource';
Vue.use(VueResource);
```
Home.vue中
```js
  created(){
    this.$http.get('http://jsonplaceholder.typicode.com/users')
    .then((data)=>{
      // console.log(data);
      this.users = data.body;
    })
  },
```

## 23.vue中只用 Bootstrap4 中的样式

index.html中引入
```html
<link rel="stylesheet" href="https://cdn.bootcss.com/bootstrap/4.0.0/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
```

## 24.路由跳转

router.js
```js
import Vue from 'vue'
import Router from 'vue-router'
import Home from './components/Home'
import About from './components/about/About'

Vue.use(Router)

export default new Router({
  mode: 'history',
  base: process.env.BASE_URL,
  routes: [
    {path:'/',component:Home},
    {path:'/about',component:About},
  ]
})
```
Header.vue
```html
<router-link to="/about"></router-link>
```
App.vue
```html
<router-view></router-view>
```

## 25.路由小细节(redirect和tag)

Header.vue
```html
<!-- 默认a标签 -->
<router-link to="/about"></router-link>

<!-- 修改为div标签 -->
<router-link tag='div' to="/about"></router-link>

<!-- 动态绑定属性路由 -->
<router-link tag='div' :to="router"></router-link>
<script>
  export default {
    data(){
      return{
        router:'/'
      }
    }
  }
</script>
```

router.js
```js
export default new Router({
  mode: 'history',
  base: process.env.BASE_URL,
  routes: [
    {path:'/',component:Home},
    {path:'/about',component:About},
    {path:'*',redirect:'/'}, //错误输入重定向
  ]
})
```

## 26.路由name属性及跳转方法

### name
```js
{path:'/',name:'homelink',component:Home},
```

```html
<!-- 注意这几个符号 : {} " '' " -->
<li><router-link :to="{name:'homelink'}" class="nav-link">主页</router-link></li>
```

### 跳转
```html
  <button @click="goOlder" class='btn btn-success'>goOlder</button>
  <button @click="goMenu" class='btn btn-success'>goMenu</button>
  <button @click="goAdmin" class='btn btn-success'>goAdmin</button>

<script>
export default {
  methods:{
    goOlder(){
      this.$router.go(-1); // 到前一个页面
    },
    goMenu(){
      // this.$router.replace('/menu');  // replace到指定路由页面
      this.$router.push('/menu');  // push到指定路由页面
    },
    goAdmin(){
      // this.$router.replace({name:'adminLink'});  // 到指定 name 页面
      this.$router.push({name:'adminLink'});  // 到指定 name 页面
    },
  }
}
</script>
```

## 27.路由嵌套

router.js
```js
    {path:'/about',name:'aboutLink',redirect:'/about/histoey',component:About,
    // 二级路由
    children:[
      {path:'/about/histoey',name:'historyLink',component:History},
      {path:'/about/contact',name:'contactLink',redirect:'/phone',component:Contact,children:[
        // 三级路由
        {path:'/phone',name:'phoneNum',component:Phone},
        {path:'/personname',name:'personName',component:Personname},
      ]},
      {path:'/about/orderingguide',name:'orderingGuideLink',component:OrderingGuide},
      {path:'/about/delivery',name:'deliveryLink',component:Delivery},
    ]},
```

about.vue
```html
<!-- 导航的内容 -->
<router-view></router-view>
```

## 28.导航守卫(全局守卫)

学习地址(https://router.vuejs.org/zh/guide/advanced/navigation-guards.html)

main.js中
```js
// 全局守卫
router.beforeEach((to,from,next) => {
  if(to.path == '/login' || to.path == '/register'){
    next()
  }else{
    alert("还没有登录，请先登录！");
    next('/login');
  }
})
```

## 29.导航守卫(路由独享-组件内守卫)

### 后置钩子(不常用)
```js
router.afterEach((to,from) => {
  alert("after each")
})
```

### 路由独享的守卫
```js
const router = new VueRouter({
  routes: [
    {
      path: '/foo',
      component: Foo,
      beforeEnter: (to, from, next) => {
        // ...
      }
    }
  ]
})
```
### 组件内的守卫
- beforeRouteEnter
- beforeRouteUpdate (2.2 新增)
- beforeRouteLeave

```js
const Foo = {
  template: `...`,
  beforeRouteEnter (to, from, next) {
    // 在渲染该组件的对应路由被 confirm 前调用
    // 不！能！获取组件实例 `this`
    // 因为当守卫执行前，组件实例还没被创建
  },
  beforeRouteUpdate (to, from, next) {
    // 在当前路由改变，但是该组件被复用时调用
    // 举例来说，对于一个带有动态参数的路径 /foo/:id，在 /foo/1 和 /foo/2 之间跳转的时候，
    // 由于会渲染同样的 Foo 组件，因此组件实例会被复用。而这个钩子就会在这个情况下被调用。
    // 可以访问组件实例 `this`
  },
  beforeRouteLeave (to, from, next) {
    // 导航离开该组件的对应路由时调用
    // 可以访问组件实例 `this`
  }
}
```
beforeRouteEnter 守卫 不能 访问 this，因为守卫在导航确认前被调用,因此即将登场的新组件还没被创建。

不过，你可以通过传一个回调给 next来访问组件实例。在导航被确认的时候执行回调，并且把组件实例作为回调方法的参数。

```js
beforeRouteEnter (to, from, next) {
  next(vm => {
    // 通过 `vm` 访问组件实例
  })
}
```
注意 beforeRouteEnter 是支持给 next 传递回调的唯一守卫。对于 beforeRouteUpdate 和 beforeRouteLeave 来说，this 已经可用了，所以不支持传递回调，因为没有必要了。

```js
beforeRouteUpdate (to, from, next) {
  // just use `this`
  this.name = to.params.name
  next()
}
```
这个离开守卫通常用来禁止用户在还未保存修改前突然离开。该导航可以通过 next(false) 来取消。

```js
beforeRouteLeave (to, from , next) {
  const answer = window.confirm('Do you really want to leave? you have unsaved changes!')
  if (answer) {
    next()
  } else {
    next(false)
  }
}
```
```js
beforeRouteLeave(to,from,next){
  if(confirm('确认离开吗？') == true){
    next()
  }else{
    next(false)
  }
}
```

## 30.复用router-view

router.js修改
```js
{path:'/',name:'homeLink',component:Home,},
```
为
```js
// 注意 components 的 s
{path:'/',name:'homeLink',components:{
  default:Home,
  'history':History,
  'orderingGuide':OrderingGuide,
  'delivery':Delivery
}},
```
App.vue添加
```html
<div class="container">
  <div class="row">
    <div class="col-sm-12 col-md-4">
      <router-view name="history"></router-view>
    </div>
    <div class="col-sm-12 col-md-4">
      <router-view name="orderingGuide"></router-view>
    </div>
    <div class="col-sm-12 col-md-4">
      <router-view name="delivery"></router-view>
    </div>
  </div>
</div>
```

## 31.路由控制滚动行为
router.js中
```js
const router = new VueRouter({
  routes: [...],
  scrollBehavior (to, from, savedPosition) {
    // return 期望滚动到哪个的位置
  }
})
```
eg:
```js

  scrollBehavior (to, from, savedPosition) {
    // return {x:0,y:100};  // 滚动到（0,100）
    // return {selector:'.btn'}; // 滚动到 第一个.btn
    // 浏览器返回上一页面时，回到上次浏览的位置
    if(savedPosition){
      return savedPosition
    }else{
      return {x:0,y:0}
    }
  }
```

## 32.跨域

### （0）预设

通过vue-cli3.x版本构建的项目使用proxy和以前的项目不同，而且3.x版本构建的时候可以选用typescript了。下面记录一下如何使用proxy跨域。
首先在根目录创建vue.config.js文件，这个配置文件在运行项目的时候自动加载。
```js
// vue.config.js
module.exports = {
  devServer: {
    proxy: {
      '/api': {
        target: 'http://xxxx/device/', //对应自己的接口
        changeOrigin: true,
        ws: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    }
  }
}
```
这个文件还可以配置其它信息，比如修改端口号，默认是8080等等。
最后在页面发送请求的时候：
```js
axios.get('/api/getDataPoint').then(res => {
  console.log(res)
})
```
示例如下：

### （1）预设
```js
proxyTable:{
  ' /apis': {
      //测试环境
      target:'http://www.thenewstep.cn/', //接口域名
      change0rigin:true, //是否跨域
      pathRewrite: {
        '^/apis':'' //需要rewrite重写的，
      }
  }
},
```

### （2）fetch
```js
created(){
  // fetch
  fetch("/apis/test/testToken. php", {
    method:"post",
    headers: {
      "Content-type" :"application/json",
      "token" : "f4c902c9ae5a2a9d8f84868ad064e706"
    },
    body: JSON.stringify({username: "henry" , password :"321321"})
  })
  . then( result =>{
    // console. log( result)
    return result. json()
  })
  . then(data => {
    console. log ( data)
  })
}
```

### (3)axios
main.js
```js
import axios from 'axios'

axios.defaults.headers.common[ 'token '] = "f4c902c9ae5a2a9d8f84868ad064e706"
axios.defaults.headers.post ["Content-type"] = "application/j son"

Vue.prototype.$axios = axios
```
App.vue
```js
this.$axios.post("/apis/test/testToken.php" , {username :"hello",password :"123456"})
  .then(data => {
    console. log(data)
  })
```

### (4) 示例二加载美团外卖数据json

将包含 `goods.json`,`ratings.json`,`seller.json` 三个文件的 `data` 文件夹放到根目录下

还是`vue.config.js`文件
```js
const goods = require(' ./data/goods.json');
const ratings = require(' ./data/ratings.json');
const seller = require(' ./data/seller.json');

module.exports = {
  //baseUrl: './', //根路径 //"baseUrl" option in vue.config.js is deprecated now, please use "publicPath" instead.
  publicPath: './', //根路径
  outputDir: 'dist2', //构建输出目录
  assetsDir: 'assets', //静态资源目录(js, css, img, fonts )
  lintOnSave: false, //是否开启eslint保存检测，有效值: true || false || ' error'

  devServer: {
    open: true, // 浏览器自动开启
    host: 'localhost', // 主机地址'127.0.0.0','0.0.0.0'也可以
    port: 8081, // 端口号
    https: false, // 是否启动https，启动会警告
    hot0nly: false, // 热更新，默认false
    proxy: {
      //配置跨域
      '/api': {
        target: 'http//localhost:5000/api/',
        ws: true,
        chang0rigin: true,
        pathRewrite: {
          '^/api': ''
        }
      }
    }
  },

  before(app) {
    // http: //loca lhost: 8081/api/goods
    app.get('/api/goods', (req, res) => {
      res. json(goods) ;
    });
    app.get( '/api/ratings', (req, res) => {
      res. json(ratings);
    });
    app.get( '/api/seller', (req, res) => {
      res. json(seller);
    });
  }

};
```

## vuecli3
## 33.Vue-Cli3.0-项目搭建及介绍

找到脚手架的github仓库：https://github.com/vuejs/vue-cli

打开docs文件夹，拉到最后，按照步骤安装

Install:
```bush
npm install -g @vue/cli
# OR
yarn global add @vue/cli
```
Create a project:
```bush
vue create my-project
# OR
vue ui
```
Run a project
```bush
cd my-project
npm run serve
```

## 34.Vue-Cli3.0-新出的添加插件方法

- 原来的插件安装方法
  ```bush
  npm install <plugin> --save
  ```
- 新方法
  ```bush
  vue add <plugin>
  ```
  会有一些文件替换的插件（比如`vuetify`）会有提示，建议用该方法

## 35.Vue-Cli3.0-全局环境变量的使用

### 全局环境
根路径下创建`.env`文件，设置全局环境变量，比如：
```
VUE_APP_XXX = XXX
```

在需要的组件内
```html
<script>
export default{
  data(){
    return{
      url: process.env.VUE_APP_XXX
    }
  }
}
</script>
```

`.env`数据变化要重新启动项目

### 开发环境
根路径下创建`.env.development`文件，设置开发环境变量，比如：
```
VUE_APP_XXX = XXX
```
`npm run serve`时用该文件的值。

### 生产环境
根路径下创建`.env.production`文件，设置开发环境变量，比如：
```
VUE_APP_XXX = XXX
```
`npm run build`时用该文件的值。

## 36.Vue-Cli3.0-独立运行.vue文件

```bush
npm install -g @vue/cli-service-global

vue serve XXX.vue
```

## 37.Vue-Cli3.0-图形页面构建项目

```bush
vue ui
```
打开GUI地址，进入图形页面，开始构建项目。

创建新项目：详情->预设->功能->配置

创建时 terminal 窗口会继续运行

创建好后gui界面会有：插件，依赖，配置，任务(serve,build,inspect) 4个菜单。

## vuex
## 38.State(Vuex-搭建Vuex中央状态管理 & Vuex-使用computed获取store数据)
Vuex
> Centralized State Management for Vue.js.

`src` 目录下新建 `store` 文件夹，下面新建 `index.js` 文件
```js
import Vue from 'vue'
import Vuex from 'vuex'

Vue.use(Vuex)

export const store = new Vuex.Store({
  state:{
    products:[
      {name:'马云',price:'200'},
      {name:'马化腾',price:'140'},
      {name:'马冬梅',price:'20'},
      {name:'马蓉',price:'10'},
    ]
  }
}) 
```

`main.js` 中引入
```js
import {store} from './store'
new Vue({
  store,
  ...
}
```

组建中使用，`computed` 属性获取 `store` 中数据
```html
<li v-for="product in products" :key='product'>
  <span class="name">{{product.name}}</span>
  <span class="price">${{product.price}}</span>
</li>

<script>
export default{
  computed: {
    products(){
      return this.$store.state.products
    }
  },
}
</script>
```

## 39.Getter
`index.js` 文件中，新增 `getters` 属性，里面放其他组件可以调用的方法
```js
export const store = new Vuex.Store({
  state:{
    products:[
      {name:'马云',price:'200'},
      {name:'马化腾',price:'140'},
      {name:'马冬梅',price:'20'},
      {name:'马蓉',price:'10'},
    ]
  },
  getters:{
    saleProducts:(state)=>{
      var saleProducts = state.products.map(product =>{
        return{
          name: "**" + product.name + "**" ,
          price: product.price / 2
        }
      });
      return saleProducts;
    }
  }
}) 
```
组件对 `store` 中方法的调用
```html
<li v-for="product in saleProducts" :key='product'>
  <span class="name">{{product.name}}</span>
  <span class="price">${{product.price}}</span>
</li>

<script>
export default{
  computed: {
    saleProducts(){
      return this.$store.getters.saleProducts;
    }
  },
}
</script>
```

## 40.Mutation
谷歌浏览器添加插件[Vue.js devtools](https://chrome.google.com/webstore/detail/vuejs-devtools/nhdogjmejiglipccpnnnanhbledajbpd)，**可以跟踪vuex状态**

>更改 Vuex 的 store 中的状态的唯一方法是提交 mutation。Vuex 中的 mutation 非常类似于事件：每个 mutation 都有一个字符串的 事件类型 (type) 和 一个 回调函数 (handler)。这个回调函数就是我们实际进行状态更改的地方，并且它会接受 state 作为第一个参数。

`store/index.js` 中添加 `mutations` 属性
```js
  mutations:{
    reducePriceV:state=>{
      state.products.forEach(product =>{
        product.price -= 1;
      })
    }
  }
```

组建中调用方法 `reducePriceV`
```html
<button @click="reducePrice">降价</button>
<script>
export default {
  methods: {
    reducePrice(){
      this.$store.commit('reducePriceM') // mutations中的方法
    }
  },
}
</script>
```

## 41.Action
Action 类似于 mutation，不同在于：

- Action 提交的是 mutation，而不是直接变更状态。
- Action 可以包含任意异步操作。(vuex调试器中方法和变化同时出来)

### 注册action
Action 函数接受一个与 store 实例具有相同方法和属性的 `context` 对象，因此你可以调用 `context.commit` 提交一个 mutation，或者通过 `context.state` 和 `context.getters` 来获取 state 和 getters。

### 组件触发action
Action 通过 `store.dispatch` 方法触发

### 接收第二个参数 payload

### eg:

`store/index.js` 中添加 `actions` 属性
```js
  actions:{
    reducePriceA:context=>{
      setTimeout(function(){
        context.commit('reducePriceM')
      },2000)
    }
  }
```
组建中调用方法 `reducePriceM`
```html
<button @click="reducePrice">降价</button>
<script>
export default {
  methods: {
    reducePrice(){
      this.$store.dispatch('reducePriceA') // actions中的方法
    }
  },
}
</script>
```

## 42.Vuex-mapMutations & mapActions
### 在组件中提交 Mutation
你可以在组件中使用 this.$store.commit('xxx') 提交 mutation，或者使用 mapMutations 辅助函数将组件中的 methods 映射为 store.commit 调用（需要在根节点注入 store）。
```js
import { mapMutations } from 'vuex'

export default {
  // ...
  methods: {
    ...mapMutations([
      'increment', // 将 `this.increment()` 映射为 `this.$store.commit('increment')`

      // `mapMutations` 也支持载荷：
      'incrementBy' // 将 `this.incrementBy(amount)` 映射为 `this.$store.commit('incrementBy', amount)`
    ]),
    ...mapMutations({
      add: 'increment' // 将 `this.add()` 映射为 `this.$store.commit('increment')`
    })
  }
}
```
### 在组件中分发 Action
你在组件中使用 this.$store.dispatch('xxx') 分发 action，或者使用 mapActions 辅助函数将组件的 methods 映射为 store.dispatch 调用（需要先在根节点注入 store）：
```js
import { mapActions } from 'vuex'

export default {
  // ...
  methods: {
    ...mapActions([
      'increment', // 将 `this.increment()` 映射为 `this.$store.dispatch('increment')`

      // `mapActions` 也支持载荷：
      'incrementBy' // 将 `this.incrementBy(amount)` 映射为 `this.$store.dispatch('incrementBy', amount)`
    ]),
    ...mapActions({
      add: 'increment' // 将 `this.add()` 映射为 `this.$store.dispatch('increment')`
    })
  }
}
```

## 43.Module
由于使用单一状态树，应用的所有状态会集中到一个比较大的对象。当应用变得非常复杂时，store 对象就有可能变得相当臃肿。

为了解决以上问题，Vuex 允许我们将 store 分割成模块（module）。每个模块拥有自己的 state、mutation、action、getter、甚至是嵌套子模块——从上至下进行同样方式的分割：

```js
const moduleA = {
  state: { ... },
  mutations: { ... },
  actions: { ... },
  getters: { ... }
}

const moduleB = {
  state: { ... },
  mutations: { ... },
  actions: { ... }
}

const store = new Vuex.Store({
  modules: {
    a: moduleA,
    b: moduleB
  }
})

store.state.a // -> moduleA 的状态
store.state.b // -> moduleB 的状态
```