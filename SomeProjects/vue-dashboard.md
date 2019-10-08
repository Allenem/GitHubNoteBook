# vue-dashboard

> A Vue.js project: shoppingWeb   
> 项目地址：https://github.com/Allenem/vue-dashboard

![build](https://travis-ci.org/Allenem/vue-dashboard.svg?branch=master)
![language](https://img.shields.io/badge/language-Vue-brightgreen.svg)
![Version](https://img.shields.io/badge/Vue-2.9.6-brightgreen.svg)

## Demo Address

https://allenem.github.io/vue-dashboard/dist/index.html

### tips
* 1.模拟订单 **无需登录**

* 2.产品列表、订单列表、优惠券部分 **需要登录**   
  + 可以使用默认账号密码
  + 也可以clone项目到本地，自己注册添加修改商品信息，注意修改 config/dev.env.js 和 config/prod.env.js 中的 ```CUSTOMPATH``` 为自己的API。
  + 参考注册账号，申请API网址：https://vue-course-api.herokuapp.com/ (老师给的接口，非常感谢)   

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build

# build for production and view the bundle analyzer report
npm run build --report
```

For a detailed explanation on how things work, check out the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).

## Used
* Vue-cli
* Vue-axios
* Bootstrap4
* 参考注册申请API网址：https://vue-course-api.herokuapp.com/ (老师给的接口，非常感谢)
* filter
* vee-validate

## Data  
```json
[
  {
    "category": "測試分類",
    "id": "-LREz8_3Df7aMDcFI8mU",
    "image": "https://images.unsplash.com/photo-1516550135131-fe3dcb0bedc7?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=621e8231a4e714c2e85f5acbbcc6a730&auto=format&fit=crop&w=1352&q=80",
    "origin_price": 1000,
    "price": 500,
    "title": "測試的產品",
    "unit": "單位",
    "num": 1
  },
  {
    "category": "測試分類",
    "id": "-LREyEWgcMSrCSQ-elg3",
    "image": "https://images.unsplash.com/photo-1516550135131-fe3dcb0bedc7?ixlib=rb-0.3.5&ixid=eyJhcHBfaWQiOjEyMDd9&s=621e8231a4e714c2e85f5acbbcc6a730&auto=format&fit=crop&w=1352&q=80",
    "origin_price": 1000,
    "price": 500,
    "title": "測試的產品",
    "unit": "單位",
    "num": 2
  }
]
```

## Thanks
[【前端教程】——Vue 出一個電商網站（下）](https://www.bilibili.com/video/av35541119)

## Done
- [x] 登录页
- [x] 产品列表页布局
- [x] 产品列表增、删、改
- [x] 模拟订单页布局
- [x] 模拟订单详情
- [x] 模拟订单加入购物车
- [x] 模拟订单购物车显示和删除
- [x] 模拟订单用户信息填写及验证
- [x] 付款页布局
- [x] 付款页付款成功与否的验证显示
- [x] 页面和按钮懒加载效果
- [x] 手机自适应

## Todo List
- [ ] 订单列表页
- [ ] 优惠券页
- [ ] 使用优惠券
- [ ] 搜索功能

## Effect Images

* 1login2productspageone3productspageone4lazyloading
![1login2productspageone3productspageone4lazyloading](https://github.com/Allenem/vue-dashboard/raw/master/effectPictures/1login2productspageone3productspageone4lazyloading.png)   

* costermer_order
![costermer_order](https://github.com/Allenem/vue-dashboard/raw/master/effectPictures/costermer_order.png)   

* newOrEditOrDelProduct
![newOrEditOrDelProduct](https://github.com/Allenem/vue-dashboard/raw/master/effectPictures/newOrEditOrDelProduct.png)   

* payPageAndOthers
![payPageAndOthers](https://github.com/Allenem/vue-dashboard/raw/master/effectPictures/paypageAndOthers.png)   

## Others

本来想用router的mode为history，因为默认的hash模式有#太丑但是发现用history模式好像要有后端配置，放弃了。[官网](https://router.vuejs.org/zh/guide/essentials/history-mode.html)有如下说明：   

>``` vue-router ```默认``` hash ```模式 —— 使用 URL 的 hash 来模拟一个完整的 URL，于是当 URL 改变时，页面不会重新加载。
>
>如果不想要很丑的 hash，我们可以用路由的 history 模式，这种模式充分利用 history.pushState API 来完成 URL 跳转而无须重新加载页面。
>```js
>const router = new VueRouter({
>  mode: 'history',
>  routes: [...]
>})
>```
>当你使用 history 模式时，URL 就像正常的 url，例如 http://yoursite.com/user/id 也好看！
>不过这种模式要玩好，还需要后台配置支持。因为我们的应用是个单页客户端应用，如果后台没有正确的配置，当用户在浏览器直接访问 http://oursite.com/user/id 就会返回 404，这就不好看了。
>   
>所以呢，你要在服务端增加一个覆盖所有情况的候选资源：如果 URL 匹配不到任何静态资源，则应该返回同一个 index.html 页面，这个页面就是你 app 依赖的页面。