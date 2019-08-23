# React16

## CONTENT

- [运用脚手架初始化React项目](#运用脚手架初始化React项目)
- [安装时报错及解决（可略过）](#安装时报错及解决)
- [脚手架生成的项目目录介绍](#脚手架生成的项目目录介绍)

***

## 运用脚手架初始化React项目

```bash
# install node
node -v
npm -v
npm install -g cnpm --registry=https://registry.npm.taobao.org

# install react scaffold
npm install -g create-react-app 
create-react-app -V

# new an app
create-react-app <appname>

# go to <appname> folder
cd <appname>

# start project
npm start
```

***

## 安装时报错及解决

**以下这一部分可以选择性忽略。**

报错了，那我就升级node吧，试试安装网上说的 安装 n 模块升级
```
error eslint@6.2.1: The engine "node" is incompatible with this module. Expected version "^8.10.0 || ^10.13.0 || >=11.10.1". Got "11.2.0"
error Found incompatible module.
```
```bash
# install n module
npm i -g n 
```
又报错
```
npm ERR! code EBADPLATFORM
npm ERR! notsup Unsupported platform for n@6.0.1: wanted {"os":"!win32","arch":"any"} (current: {"os":"win32","arch":"x64"})
```
那就说明 n 模块不支持windows系统，虽然下面可以强制安装n模块，然并卵。
```bash
# PS:global package direction:C:\Users\<username>\AppData\Roaming\npm
npm i -g n --force
```

```bash
# update to specific version
n version 
# such as
n 10.0.0

# update to the latest version
n latest

# update to the LTS version
n stable
```

然并卵，那我就下载安装包来安装吧 ┭┮﹏┭┮，OK，安装成功，运行`create-react-app <appname>`成功生成React新项目。

这部分可能是由于我安装了yarn，脚手架优先用yarn生成项目，yarn又对node版本有要求所致。

**以上这一部分可以选择性忽略。**

***

## 脚手架生成的项目目录介绍

```
│  .gitignore
│  package.json
│  README.md
│  yarn.lock
│
├─node_modules/
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
        App.css
        App.js
        App.test.js
        index.css
        index.js
        logo.svg
        serviceWorker.js
```

|文件 / 文件夹|子文件|简介|
|-|-|-|
|`.gitignore` ||git忽略文件|
|`package.json` ||包管理文件|
|`README.md` ||项目介绍|
|`yarn.lock` ||安装时的版本管理文件|
|`node_modules/` ||依赖包|
|`public` ||公共资源文件夹|
| |`index.html`    |网页入口|
| |`favicon.ico`   |网页小logo|
| |`logo192.png`   |网页中logo|
| |`logo512.png`   |网页大logo|
| |`manifest.json` |logo配置文件|
| |`robots.txt`    |Web site owners use the /robots.txt file to give instructions about their site to web robots; this is called *The Robots Exclusion Protocol*.|
|`src` ||源码文件夹|
| |`index.js` |入口文件|
| |`index.css` |入口文件样式|
| |`App.js` |根组件|
| |`App.css` |根组件样式|
| |`App.test.js` |根组件测试文件|
| |`logo.svg` |旋转的logo|
| |`serviceWorker.js` |提供PWA|

***

## 