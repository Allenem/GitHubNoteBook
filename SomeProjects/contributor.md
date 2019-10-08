# all-contributors-cli 测试

[![All Contributors](https://img.shields.io/badge/all_contributors-3-orange.svg?style=flat-square)](#contributors-)

官方网址：https://allcontributors.org

English | 中文
-|-
[README.md](https://github.com/Allenem/all-contributors-cli-test/blob/master/README.md)|[README-zh-CN.md](https://github.com/Allenem/all-contributors-cli-test/blob/master/README-zh-CN.md)

* * *

## 贡献者 ✨

<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- prettier-ignore-start -->
<!-- markdownlint-disable -->
<table>
  <tr>
    <td align="center"><a target="_blank" href="https://github.com/Allenem"><img src="https://avatars1.githubusercontent.com/u/33366355?v=4" width="100px;" alt="蒲尧"/><br /><sub><b>蒲尧</b></sub></a><br /><a target="_blank" href="https://github.com/Allenem/all-contributors-cli-test/commits?author=Allenem" title="Code">💻</a> <a target="_blank" href="https://github.com/Allenem/all-contributors-cli-test/commits?author=Allenem" title="Documentation">📖</a> <a target="_blank" href="#translation-Allenem" title="Translation">🌍</a> <a target="_blank" href="#review-Allenem" title="Reviewed Pull Requests">👀</a></td>
    <td align="center"><a target="_blank" href="https://github.com/ionicbond-lzj"><img src="https://avatars0.githubusercontent.com/u/45113875?v=4" width="100px;" alt="ionicbond-lzj"/><br /><sub><b>ionicbond-lzj</b></sub></a><br /><a target="_blank" href="https://github.com/Allenem/all-contributors-cli-test/commits?author=ionicbond-lzj" title="Tests">⚠️</a></td>
    <td align="center"><a target="_blank" href="https://github.com/Juliayao"><img src="https://avatars3.githubusercontent.com/u/55355288?v=4" width="100px;" alt="Juliayao"/><br /><sub><b>Juliayao</b></sub></a><br /><a target="_blank" href="#userTesting-Juliayao" title="User Testing">📓</a></td>
  </tr>
</table>

<!-- markdownlint-enable -->
<!-- prettier-ignore-end -->
<!-- ALL-CONTRIBUTORS-LIST:END -->

* * *

## 一、从 NPM 安装

 ```bash
yarn add --dev all-contributors-cli 
# 或者
npm i -D all-contributors-cli
```

## 二、初始化项目

```bash
yarn all-contributors init
# 或者
npm run all-contributors init
# 或者直接执行bin
./node_modules/.bin/all-contributors init
```

## 三、添加贡献者

```bash
# 添加做出了 <contribution> 类型贡献的贡献者 <username>, 
all-contributors add <username> <contribution>

# 例如：
# all-contributors add jfmengels code,doc

# 生成表格
yarn all-contributors generate
```

## 四、更新贡献者文档

考虑更新 `.all-contributorsrc` 或者 重复上面相同的步骤添加贡献者。

## 五、在 `package.json` 中选择性添加快捷指令

你可以在 `package.json` 的 `scripts` 区域选择性添加快捷指令。

例如:
```json
{
  "scripts": {
    "contributors:add": "all-contributors add",
    "contributors:generate": "all-contributors generate"
  }
}
```
运行如下指令
```bash
yarn contributors:add jfmengels doc
```

## 六、注意事项

### 注1：generate 前注意事项

使用 `generate` 从 `.all-contributorsrc` 文件读取贡献者列表 `contributors` 并对指定的文件 `files` 更新贡献者表格。

请注意在这些文件中，下面的标签必须能够被 `generate` 指令找到，以生成或者更新贡献者表格：

```
<!-- ALL-CONTRIBUTORS-LIST:START - Do not remove or modify this section -->
<!-- ALL-CONTRIBUTORS-LIST:END -->
```
&hearts; 我发现上面的代码如果在文中第一次出现，在运行 `yarn all-contributors generate` 时，上面的代码可能会被自动注入贡献者 , 请将第一个和最后一个标签之间的内容移动到合适的地方[Contributors](#contributors-)。

### 注2：Emoji 关键词 ✨ (和贡献种类)

| Emoji图标/关键词 | 含义 | 说明 |
| --- | --- | --- |
| 💬 | | |
| `question` | 回答问题 | 在Issues, Stack Overflow, Gitter, Slack等回答问题 |
| 🐛 | | |
| `bug` | Bug反馈 | 指向用户在此项目汇报的issues |
| 📝 | | |
| `blog` | 博文 | 指向博文 |
| 💼 | | |
| `business` | 业务发展 | 执行业务端的人员 |
| 💻 | | |
| `code` | 代码 | 指向用户在此项目的提交 |
| 🖋 | | |
| `content` | 内容 | 例如：网站备份和博文都是分开的 |
| 📖 | | |
| `doc` | 文档 | 指向用户在此项目、Wiki或者其他文档来源的提交 |
| 🎨 | | |
| `design` | 设计 | 指向标志、肖像、视觉设计等 |
| 💡 | | |
| `example` | 范例 | 指向范例 |
| 📋 | | |
| `eventOrganizing` | 活动组织者 | 指向活动页面 |
| 💵 | | |
| `financial` | 经济支持 | 提供经济支持、指向相关页面的人员或者组织 |
| 🔍 | | |
| `fundingFinding` | 资金/拨款发现者 | 帮助寻找经济支持的人员 |
| 🤔 | | |
| `ideas` | 创意 & 策划 |  |
| 🚇 | | |
| `infra` | 基础设施 | 托管，构建工具等， 如果适用的话，指向仓库中的源文件(像`travis.yml`) |
| 🚧 | | |
| `maintenance` | 维护 | 帮助维护仓库的人员，指向用户在此项目的提交 |
| 📦 | | |
| `platform` | 打包 | 移植以支持新平台 |
| 🔌 | | |
| `plugin` | 插件/实用程序库 | 指向仓库主页 |
| 📆 | | |
| `projectManagement` | 项目管理 |  |
| 👀 | | |
| `review` | 检查pull request |  |
| 🛡️ | | |
| `security` | 安全 | 识别 和/或 减少安全威胁，GDPR，隐私等 |
| 🔧 | | |
| `tool` | 工具 | 指向仓库主页 |
| 🌍 | | |
| `translation` | 翻译 | 链接到翻译的内容 |
| ⚠️ | | |
| `test` | 测试 | 指向用户在此项目的提交 |
| ✅ | | |
| `tutorial` | 教程 | 指向教程 |
| 📢 | | |
| `talk` | 交流 | 指向幻灯片/录音/仓库等 |
| 📓 | | |
| `userTesting` | 用户测试 | 指向用户测试记录 |
| 📹 | | |
| `video` | 视频 | 指向视频 | 

### 注3：CLI配置

可以通过更新 `.all-contributorsrc` JSON文件来配置 all-contributors 。 用来生成贡献者列表的数据将会存储在此文件中，同时可以随意配置 `all-contributors-cli` 来生成列表。

这些是可以指定的关键词：

| 选项 | 描述 | 范例/默认 |
| --- | --- | --- |
| `projectName` | 必要，项目名称 | 范例：`all-contributors-cli` |
| `projectOwner` | 必要，项目的持有用户名称 | 范例：`jfmengels` |
| `repoType` | 仓库类型， 必须是`github`或者`gitlab` | 默认：`github` |
| `repoHost` | 指向仓库的主机名， 如果你用自己托管的仓库请更改 | 默认：`https://github.com`如果`仓库类型`是`github`，或者`https://gitlab.com`如果`仓库类型`是`gitlab`。 |
| `files` | 要更新文件的数组 | 默认：`['README.md']` |
| `imageSize` | 用户头像尺寸 (以像素为单位) | 默认：`100` |
| `commit` | 当添加贡献者时，自动提交徽章 | `true` 或者`false` |
| `commentConvention` | Commit convention ([`angular`](https://github.com/angular/angular/blob/master/CONTRIBUTING.md#-commit-message-guidelines), [`atom`](https://github.com/atom/atom/blob/master/CONTRIBUTING.md#git-commit-messages), [`ember`](https://guides.emberjs.com/v1.10.0/contributing/#toc_commits), [`eslint`](https://eslint.org/docs/1.0.0/developer-guide/contributing#step-2-make-your-changes), [`jshint`](https://jshint.com/contribute/) or [`gitmoji`](https://gitmoji.carloscuesta.me/)). | 默认: `none` |
| `contributorsPerLine` | 贡献者表的最大列数 | 默认：`7` |
| `badgeTemplate` | 定义你自己的lodash模版来生成徽章 |  |
| `contributorTemplate` | 定义你自己的lodash模版来生成贡献者 |  |
| `types` | 对于贡献者类型，具体说明自定义符号或者链接模版 可以覆盖记录的类型 |  |
| `contributors` | `all-contributors add`可以用来更新此项目的贡献者列表 | | |

* * *

## LICENSE

[MIT](https://github.com/Allenem/all-contributors-cli-test/blob/master/LICENSE)