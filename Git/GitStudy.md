# GitStudy

>Git是目前世界上最先进的分布式版本控制系统（没有之一）。

>学习参考文档：https://git-scm.com/docs

---

## 一、git的安装配置

下载地址：https://git-scm.com/downloads

按默认选项安装即可。

安装完成后，在开始菜单里找到 `Git` -> `Git Bash` ，蹦出一个类似命令行窗口的东西，就说明Git安装成功！

安装完成后，还需要最后一步设置 `用户名` 和 `邮箱` ，在命令行输入：

```git
git config --global user.name "Your Name"
git config --global user.email "email@example.com"
```
---

## 二、初始化git仓库

进入文件夹，右击进入 `git bash` ，输入

```git
git init
```

## 三、将修改的文件添加到仓库

添加所有修改
```git
git add .
```

添加 readme.txt
```git
git add readme.txt
```

添加 src/ 文件夹
```git
git add src/
```

## 四、把添加的文件提交到仓库

```git
git commit -m 'add sth.'
```
`-m` 后是对这次提交的说明

---

## 五、设置密钥

创建 `SSH KEY`。先看一下C盘用户目录下有没有.ssh目录，有的话看下里面有没有 `id_rsa` 和 `id_rsa.pub` 这两个文件，有就跳到 GitHub 设置，没有就通过下面命令创建

```git
ssh-keygen -t rsa -C "youremail@example.com"
```

然后一路回车。这时你就会在用户下的 `.ssh` 目录里找到 `id_rsa` 和 `id_rsa.pub` 这两个文件。

登录 `Github` ,找到右上角的图标，打开点进里面的 `Settings` ，再选中里面的 `SSH and GPG KEYS` ，点击右上角的 `New SSH key` ，然后 `Title` 里面随便填，再把刚才 `id_rsa.pub` 里面的内容复制到 `Title` 下面的 `Key` 内容框里面，最后点击 `Add SSH key` ，这样就完成了 `SSH Key` 的加密。

## 六、本地仓库和远程仓库关联

在 `Github` 上设置好 `SSH` 密钥后，新建一个远程仓库，通过以下命令将本地仓库和远程仓库进行关联；

```git
git remote add origin https://github.com/yourname/yourrepo.git
```

## 七、把本地仓库的项目推送到远程仓库

```git
git push -u origin master
```

由于新建的远程仓库是空的，所以要加上 `-u` 这个参数，等远程仓库里面有了内容之后，下次再从本地库上传内容的时候只需下面这样就可以了：

```bash
git push origin master
# OR
git push
```

至此，本地仓库代码已完全提交到远端仓库（GitHub仓库）中。

---

## 八、git 提交环节的三大部分

在 `git` 提交环节，存在三大部分：`working tree`, `index file`, `commit`（工作区，暂存区，远程仓库）

这三大部分中：

1. `working tree`：就是你所工作在的目录，每当你在代码中进行了修改，`working tree`的状态就改变了。
2. `index file`：是索引文件，它是连接`working tree`和`commit`的桥梁，每当我们使用git-add命令来登记后，`index file`的内容就改变了，此时`index file`就和`working tree`同步了。
3. `commit`：是最后的阶段，只有`commit`了，我们的代码才真正进入了git仓库。我们使用git-commit就是将`index file`里的内容提交到`commit`中。

总结一下：

1. `git diff`：是查看`working tree`与`index file`的差别的。
2. `git diff --cached`：是查看`index file`与`commit`的差别的。
3. `git diff HEAD`：是查看`working tree`和`commit`的差别的。（你一定没有忘记，HEAD代表的是最近的一次`commit`的信息）

eg:
本地README.md新增
```
...
## first change
```
git操作与显示如下：
1. add前：
```
$ git diff
diff --git a/README.md b/README.md
index 83c831f..b87bcfb 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
 # test
+
+## first change
```
```
$ git diff --cached

```
```
$ git diff HEAD
diff --git a/README.md b/README.md
index 83c831f..b87bcfb 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
 # test
+
+## first change
```
2. add后，commit前
```
$ git add .
```
```
$ git diff

```
```
$ git diff --cached
diff --git a/README.md b/README.md
index 83c831f..b87bcfb 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
 # test
+
+## first change
```
```
$ git diff HEAD
diff --git a/README.md b/README.md
index 83c831f..b87bcfb 100644
--- a/README.md
+++ b/README.md
@@ -1 +1,3 @@
 # test
+
+## first change
```
3. commit后
```
$ git commit -m 'first change'
[master 89c28ca] first change
 1 file changed, 2 insertions(+)
```
```
$ git diff

```
```
$ git diff --cached

```
```
$ git diff HEAD

```

## 九、部分指令

1、初始化本地仓库：git init

2、添加源仓库：git remote add origin yourgithub（切换到user-ssh地址）

3、把远程仓库的内容下载下来：git pull origin

4、检查绑定情况，查看远程仓库：git remote -v

5、查看当前文件的状态： git status

6、提交到暂存区： git add (如果单个文件就像index.html，如果多个文件就用“ . ”点的方式)

   暂存区用处：有修改但是没写完就不能提交到本地仓库，提交到本地仓库都叫一个版本，万一有bug提交后有人合并就会出问题。暂存区会被最新的代码覆盖之前的代码放到暂存区：

7、提交到本地仓库：git commit -m ' 提交信息的简介 '

8、提交内容到远程仓库： git push

9、撤销：git checkout -- index.html

10、版本号回退：
```
   查看日志，每次提交了什么： git log

   其中commit 后面的b7dc85是版本号，可以进行版本号回退

   回退一个完整的版本：--hard，回退到上一个完整的版本

   git reset --hard HEAD~1

   git reset --hard HEAD~2(回退两个版本)

   mixed回退到暂存区添加之前的状态，即add状态

   soft之后要么版本回退要么提交，退到commit状态

   回退到指定版本：git reflog

   git reset --hard b7dc854
```

11、其中origin可以替换，只是远程服务器的一个名字而已，
```
   git remote rename origin dev

   git remote

   返回dev

   获取github项目的地址
```

12、克隆仓库：git clone

13、远程仓库重命名：git remote rename oldName newName(这步可改可不改)

14、添加源仓库地址为远程仓库： git remote add

15、查看文件夹： dir

**差异比较：**

16、比较工作区与暂存区： git diff

17、比较暂存区与本地版本库中最近一次commit 的内容： git diff --cached

18、比较工作区与本地版本库中最近一次commit的内容 ：git diff HEAD

19、比较两个commit之间的差异： git diff

**基础工作流**

20、查看分支： git branch

21、创建新分支： git branch branchName ，新建完后要切换分支，然后add，commit，push，最后在github才有显示

22、创建并切换分支： git checkout -b branchName

23、删除本地分支： git branch -d branchName

24、删除远程分支： git push -d origin branchName

25、切换分支： git checkout branchName

26、删除某个文件： git rm -r --cached target 删除target文件夹后commit，push到master

  master是装着没有bug的代码，dev分支是跟master一样的代码，但是允许报错

27、合并分支：git merge

28、把本地master分支推送到远程的master分支上：
```
  git push origin master:master

  git push origin master:dev
```

---

## 十、[友链](https://git-scm.com/docs)

### Setup and Config

*   [git](https://git-scm.com/docs/git)
*   [config](https://git-scm.com/docs/git-config)
*   [help](https://git-scm.com/docs/git-help)

### Getting and Creating Projects

*   [init](https://git-scm.com/docs/git-init)
*   [clone](https://git-scm.com/docs/git-clone)

### Basic Snapshotting

*   [add](https://git-scm.com/docs/git-add)
*   [status](https://git-scm.com/docs/git-status)
*   [diff](https://git-scm.com/docs/git-diff)
*   [commit](https://git-scm.com/docs/git-commit)
*   [reset](https://git-scm.com/docs/git-reset)
*   [rm](https://git-scm.com/docs/git-rm)
*   [mv](https://git-scm.com/docs/git-mv)

### Branching and Merging

*   [branch](https://git-scm.com/docs/git-branch)
*   [checkout](https://git-scm.com/docs/git-checkout)
*   [merge](https://git-scm.com/docs/git-merge)
*   [mergetool](https://git-scm.com/docs/git-mergetool)
*   [log](https://git-scm.com/docs/git-log)
*   [stash](https://git-scm.com/docs/git-stash)
*   [tag](https://git-scm.com/docs/git-tag)
*   [worktree](https://git-scm.com/docs/git-worktree)

### Sharing and Updating Projects

*   [fetch](https://git-scm.com/docs/git-fetch)
*   [pull](https://git-scm.com/docs/git-pull)
*   [push](https://git-scm.com/docs/git-push)
*   [remote](https://git-scm.com/docs/git-remote)
*   [submodule](https://git-scm.com/docs/git-submodule)

### Inspection and Comparison

*   [show](https://git-scm.com/docs/git-show)
*   [log](https://git-scm.com/docs/git-log)
*   [diff](https://git-scm.com/docs/git-diff)
*   [shortlog](https://git-scm.com/docs/git-shortlog)
*   [describe](https://git-scm.com/docs/git-describe)

### Patching

*   [apply](https://git-scm.com/docs/git-apply)
*   [cherry-pick](https://git-scm.com/docs/git-cherry-pick)
*   [diff](https://git-scm.com/docs/git-diff)
*   [rebase](https://git-scm.com/docs/git-rebase)
*   [revert](https://git-scm.com/docs/git-revert)

### Debugging

*   [bisect](https://git-scm.com/docs/git-bisect)
*   [blame](https://git-scm.com/docs/git-blame)
*   [grep](https://git-scm.com/docs/git-grep)

### Guides

*   [gitattributes](https://git-scm.com/docs/gitattributes)
*   [Command-line interface conventions](https://git-scm.com/docs/gitcli)
*   [Everyday Git](https://git-scm.com/docs/giteveryday)
*   [Glossary](https://git-scm.com/docs/gitglossary)
*   [githooks](https://git-scm.com/docs/githooks)
*   [gitignore](https://git-scm.com/docs/gitignore)
*   [gitmodules](https://git-scm.com/docs/gitmodules)
*   [Revisions](https://git-scm.com/docs/gitrevisions)
*   [Submodules](https://git-scm.com/docs/gitsubmodules)
*   [Tutorial](https://git-scm.com/docs/gittutorial)
*   [Workflows](https://git-scm.com/docs/gitworkflows)

### Email

*   [am](https://git-scm.com/docs/git-am)
*   [apply](https://git-scm.com/docs/git-apply)
*   [format-patch](https://git-scm.com/docs/git-format-patch)
*   [send-email](https://git-scm.com/docs/git-send-email)
*   [request-pull](https://git-scm.com/docs/git-request-pull)

### External Systems

*   [svn](https://git-scm.com/docs/git-svn)
*   [fast-import](https://git-scm.com/docs/git-fast-import)

### Administration

*   [clean](https://git-scm.com/docs/git-clean)
*   [gc](https://git-scm.com/docs/git-gc)
*   [fsck](https://git-scm.com/docs/git-fsck)
*   [reflog](https://git-scm.com/docs/git-reflog)
*   [filter-branch](https://git-scm.com/docs/git-filter-branch)
*   [instaweb](https://git-scm.com/docs/git-instaweb)
*   [archive](https://git-scm.com/docs/git-archive)
*   [bundle](https://git-scm.com/docs/git-bundle)

### Server Admin

*   [daemon](https://git-scm.com/docs/git-daemon)
*   [update-server-info](https://git-scm.com/docs/git-update-server-info)

### Plumbing Commands

*   [cat-file](https://git-scm.com/docs/git-cat-file)
*   [check-ignore](https://git-scm.com/docs/git-check-ignore)
*   [checkout-index](https://git-scm.com/docs/git-checkout-index)
*   [commit-tree](https://git-scm.com/docs/git-commit-tree)
*   [count-objects](https://git-scm.com/docs/git-count-objects)
*   [diff-index](https://git-scm.com/docs/git-diff-index)
*   [for-each-ref](https://git-scm.com/docs/git-for-each-ref)
*   [hash-object](https://git-scm.com/docs/git-hash-object)
*   [ls-files](https://git-scm.com/docs/git-ls-files)
*   [ls-tree](https://git-scm.com/docs/git-ls-tree)
*   [merge-base](https://git-scm.com/docs/git-merge-base)
*   [read-tree](https://git-scm.com/docs/git-read-tree)
*   [rev-list](https://git-scm.com/docs/git-rev-list)
*   [rev-parse](https://git-scm.com/docs/git-rev-parse)
*   [show-ref](https://git-scm.com/docs/git-show-ref)
*   [symbolic-ref](https://git-scm.com/docs/git-symbolic-ref)
*   [update-index](https://git-scm.com/docs/git-update-index)
*   [update-ref](https://git-scm.com/docs/git-update-ref)
*   [verify-pack](https://git-scm.com/docs/git-verify-pack)
*   [write-tree](https://git-scm.com/docs/git-write-tree)

---

十一、在 `Github` 较精确搜索开源项目

- 1.在指定位置搜

在 `名字` 中搜索

`in:name xxx` 

在 `readme` 中搜索

`in:readme xxx` 

在描述中搜索

`in:description xxx` 

- 2.限制条件

限定 `star` 数

`stars:>1000`

限定 `fork` 数

`forks:>1000`

限定语言

`language:xxx`

限定最后提交时间

`pushed:>xxxx-xx-xx`

- 3.1和2组合搜索示例

`in:descripton 资金管理系统 stars:>=3 language:vue`

---

[BackToTop](#)