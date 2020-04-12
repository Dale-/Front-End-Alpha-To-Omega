<h1 align="center">
<br>
  <img src="/Git/images/git.png" alt="Git" width="400">
  <br>
    <br>
  Git 版本控制
  <br>
</h1>

> 如果你正在学习Git版本控制，可点击右上角`Star`此项目, 我会持续更新资源和链接。

## 🔺目录
* [版本控制](#什么是版本控制)
* [什么是Git](#什么是Git)
* [图解命令](#图解命令)
* [常用命令](#常用命令)
* [优雅的提交记录](#优雅的提交记录)
* [图形化客户端](#图形化客户端)
* [代码托管平台](#代码托管平台)
* [学习资源](#学习资源)

## 🔺版本控制
* 版本控制是一种记录一个或若干文件内容变化，以便将来查阅特定版本修订情况的系统。一个比较易懂的说法，时光穿梭机。

* 通俗的话来说比如我们写了一篇文章，不免会在这个文章上修改、更新、或者删除。可能关于一篇文章，我们在桌面上会有很多个文件名，我们会用后缀的方式记录变化。如果我们能将每一次的改变记录成为一个版本，而且可以高效的回到某个版本、清晰的看到每一次的变化，这样就不在需要多个文件名出现在一个文件夹里面，我们可以对变化有更清晰的认知，这就是版本控制的意义。

* 比如我们可以用版本控制来推荐自己的写书进度、借助Git对Sketch进行文本管理、写文章/论文的版本更迭、对代码进行版本控制管理等。

## 🔺什么是Git
Git 是一种分布式的版本管理系统，用于敏捷高效地处理任何或小或大的项目。Git 不仅仅是个版本控制系统，它也是个内容管理系统(CMS)，工作管理系统等。

* 默认的行业标准
* 高质量的免费开源项目
* 速度快、体积小
* 隐式备份
* 安全


## 🔺图解命令

[图解原文](https://github.com/geeeeeeeeek/git-recipes/wiki/4.1-%E5%9B%BE%E8%A7%A3-Git-%E5%91%BD%E4%BB%A4)

### 基本用法

![enter image description here](http://marklodato.github.io/visual-git-guide/basic-usage.svg)

上面的四条命令在工作目录、stage 缓存(也叫做索引)和 commit 历史之间复制文件。

* `git add files` 把工作目录中的文件加入 stage 缓存
* `git commit` 把 stage 缓存生成一次 commit，并加入 commit 历史
* `git reset -- files` 撤销最后一次 `git add files`，你也可以用 `git reset` 撤销所有 stage 缓存文件
* `git checkout -- files` 把文件从 stage 缓存复制到工作目录，用来丢弃本地修改

你可以用 `git reset -p`、`git checkout -p` 或 `git add -p` 进入交互模式，也可以跳过 stage 缓存直接从  commit历史取出文件或者直接提交代码。

![enter image description here](http://marklodato.github.io/visual-git-guide/basic-usage-2.svg)

* `git commit -a ` 相当于运行 `git add` 把所有当前目录下的文件加入 stage 缓存再运行 `git commit`。
* `git commit files` 进行一次包含最后一次提交加上工作目录中文件快照的提交，并且文件被添加到 stage 缓存。
* `git checkout HEAD -- files` 回滚到复制最后一次提交。

### 约定

后文中以下面的形式使用图片：

![enter image description here](http://marklodato.github.io/visual-git-guide/conventions.svg)

绿色的5位字符表示提交的 ID，分别指向父节点。分支用橙色显示，分别指向特定的提交。当前分支由附在其上的 `_HEAD_` 标识。

这张图片里显示最后 5 次提交，`_ed489_` 是最新提交。 `_master_` 分支指向此次提交，另一个 `_maint_` 分支指向祖父提交节点。

### 命令详解

#### Diff

有许多种方法查看两次提交之间的变动，下面是其中一些例子。

![enter image description here](http://marklodato.github.io/visual-git-guide/diff.svg)

#### Commit

提交时，Git 用 stage 缓存中的文件创建一个新的提交，并把此时的节点设为父节点。然后把当前分支指向新的提交节点。下图中，当前分支是 `_master_`。

在运行命令之前，`_master_` 指向 `_ed489_`，提交后，`_master_` 指向新的节点`_f0cec_` 并以 `_ed489_` 作为父节点。

![enter image description here](http://marklodato.github.io/visual-git-guide/commit-master.svg)

即便当前分支是某次提交的祖父节点，Git 会同样操作。下图中，在 `_master_` 分支的祖父节点 `_maint_` 分支进行一次提交，生成了 `_1800b_`。

这样，`_maint_ `分支就不再是 `_master_` 分支的祖父节点。此时，[merge](#merge) 或者 [rebase](#rebase) 是必须的。

![enter image description here](http://marklodato.github.io/visual-git-guide/commit-maint.svg)

如果想更改一次提交，使用 `git commit --amend`。Git 会使用与当前提交相同的父节点进行一次新提交，旧的提交会被取消。

![enter image description here](http://marklodato.github.io/visual-git-guide/commit-amend.svg)

另一个例子是[分离HEAD提交](#detached)，在后面的章节中介绍。

#### Checkout

`git checkout` 命令用于从历史提交（或者 stage 缓存）中拷贝文件到工作目录，也可用于切换分支。

当给定某个文件名（或者打开 `-p` 选项，或者文件名和-p选项同时打开）时，Git 会从指定的提交中拷贝文件到 stage 缓存和工作目录。比如，`git checkout HEAD~ foo.c` 会将提交节点 `_HEAD~_`（即当前提交节点的父节点）中的 `foo.c` 复制到工作目录并且加到 stage 缓存中。如果命令中没有指定提交节点，则会从 stage 缓存中拷贝内容。注意当前分支不会发生变化。

![enter image description here](http://marklodato.github.io/visual-git-guide/checkout-files.svg)

当不指定文件名，而是给出一个（本地）分支时，那么 `_HEAD_` 标识会移动到那个分支（也就是说，我们「切换」到那个分支了），然后 stage 缓存和工作目录中的内容会和 `_HEAD_` 对应的提交节点一致。新提交节点（下图中的 `a47c3`）中的所有文件都会被复制（到 stage 缓存和工作目录中）；只存在于老的提交节点（`ed489`）中的文件会被删除；不属于上述两者的文件会被忽略，不受影响。

![enter image description here](http://marklodato.github.io/visual-git-guide/checkout-branch.svg)

如果既没有指定文件名，也没有指定分支名，而是一个标签、远程分支、SHA-1 值或者是像 `_master~3_` 类似的东西，就得到一个匿名分支，称作 `_detached HEAD_`（被分离的 `_HEAD_` 标识）。这样可以很方便地在历史版本之间互相切换。比如说你想要编译 1.6.6.1 版本的 Git，你可以运行 `git checkout v1.6.6.1`（这是一个标签，而非分支名），编译，安装，然后切换回另一个分支，比如说 `git checkout master`。然而，当提交操作涉及到「分离的 HEAD」时，其行为会略有不同，详情见在[下面](#detached)。

![enter image description here](http://marklodato.github.io/visual-git-guide/checkout-detached.svg)

#### HEAD 标识处于分离状态时的提交操作

当 `_HEAD_` 处于分离状态（不依附于任一分支）时，提交操作可以正常进行，但是不会更新任何已命名的分支。你可以认为这是在更新一个匿名分支。

![enter image description here](http://marklodato.github.io/visual-git-guide/commit-detached.svg)

一旦此后你切换到别的分支，比如说 `_master_`，那么这个提交节点（可能）再也不会被引用到，然后就会被丢弃掉了。注意这个命令之后就不会有东西引用 `_2eecb_`。

![enter image description here](http://marklodato.github.io/visual-git-guide/checkout-after-detached.svg)

但是，如果你想保存这个状态，可以用命令 `git checkout -b name` 来创建一个新的分支。

![enter image description here](http://marklodato.github.io/visual-git-guide/checkout-b-detached.svg)

#### Reset

`git reset` 命令把当前分支指向另一个位置，并且有选择的变动工作目录和索引。也用来在从历史commit历史中复制文件到索引，而不动工作目录。

如果不给选项，那么当前分支指向到那个提交。如果用 `--hard` 选项，那么工作目录也更新，如果用 `--soft` 选项，那么都不变。

![enter image description here](http://marklodato.github.io/visual-git-guide/reset-commit.svg)

如果没有给出提交点的版本号，那么默认用 `_HEAD_`。这样，分支指向不变，但是索引会回滚到最后一次提交，如果用 `--hard` 选项，工作目录也同样。

![enter image description here](http://marklodato.github.io/visual-git-guide/reset.svg)

如果给了文件名(或者 `-p` 选项), 那么工作效果和带文件名的[checkout](#checkout)差不多，除了索引被更新。

![enter image description here](http://marklodato.github.io/visual-git-guide/reset-files.svg)

#### Merge

`git merge` 命令把不同分支合并起来。合并前，索引必须和当前提交相同。如果另一个分支是当前提交的祖父节点，那么合并命令将什么也不做。

另一种情况是如果当前提交是另一个分支的祖父节点，就导致 `_fast-forward_` 合并。指向只是简单的移动，并生成一个新的提交。

![enter image description here](http://marklodato.github.io/visual-git-guide/merge-ff.svg)

否则就是一次真正的合并。默认把当前提交（`_ed489_` 如下所示）和另一个提交（`_33104_`）以及他们的共同祖父节点（`_b325c_`）进行一次[三方合并](http://en.wikipedia.org/wiki/Three-way_merge)。结果是先保存当前目录和索引，然后和父节点 `_33104_` 一起做一次新提交。

![enter image description here](http://marklodato.github.io/visual-git-guide/merge.svg)

#### Cherry Pick

`git cherry-pick` 命令「复制」一个提交节点并在当前分支做一次完全一样的新提交。

![enter image description here](http://marklodato.github.io/visual-git-guide/cherry-pick.svg)

#### Rebase

`git rebase` 是合并命令的另一种选择。合并把两个父分支合并进行一次提交，提交历史不是线性的。rebase 在当前分支上重演另一个分支的历史，提交历史是线性的。

本质上，这是线性化的自动的 [cherry-pick](#cherry-pick)。

![enter image description here](http://marklodato.github.io/visual-git-guide/rebase.svg)

上面的命令都在 `_topic_` 分支中进行，而不是 `_master_` 分支，在 `_master_` 分支上重演，并且把分支指向新的节点。注意旧提交没有被引用，将被回收。

要限制回滚范围，使用 `--onto` 选项。下面的命令在 `_master_` 分支上重演当前分支从 `_169a6_` 以来的最近几个提交，即 `_2c33a_`。

![enter image description here](http://marklodato.github.io/visual-git-guide/rebase-onto.svg)

同样有 `git rebase --interactive` 让你更方便的完成一些复杂操作，比如丢弃、重排、修改、合并提交。

## 🔺常用命令

[查看原文](https://github.com/521xueweihan/git-tips/blob/master/README.md)

#### 回到远程仓库的状态

抛弃本地所有的修改，回到远程仓库的状态。
```sh
git fetch --all && git reset --hard origin/master
```

#### 重设第一个 commit

也就是把所有的改动都重新放回工作区，并**清空所有的 commit**，这样就可以重新提交第一个 commit 了

```sh
git update-ref -d HEAD
```

#### 查看冲突文件列表

展示工作区的冲突文件列表
```sh
git diff --name-only --diff-filter=U
```
#### 展示工作区和暂存区的不同

输出**工作区**和**暂存区**的 different (不同)。

```sh
git diff
```

还可以展示本地仓库中任意两个 commit 之间的文件变动：
```sh
git diff <commit-id> <commit-id>
```

#### 展示暂存区和最近版本的不同

输出**暂存区**和本地最近的版本 (commit) 的 different (不同)。
```sh
git diff --cached
```

#### 展示暂存区、工作区和最近版本的不同

输出**工作区**、**暂存区** 和本地最近的版本 (commit) 的 different (不同)。

```sh
git diff HEAD
```

#### 快速切换到上一个分支

```sh
git checkout -
```

#### 删除已经合并到 master 的分支

```sh
git branch --merged master | grep -v '^\*\|  master' | xargs -n 1 git branch -d
```

#### 展示本地分支关联远程仓库的情况
```sh
git branch -vv
```

#### 关联远程分支

关联之后，`git branch -vv` 就可以展示关联的远程分支名了，同时推送到远程仓库直接：`git push`，不需要指定远程仓库了。
```sh
git branch -u origin/mybranch
```

或者在 push 时加上 `-u` 参数
```sh
git push origin/mybranch -u
```

#### 列出所有远程分支

-r 参数相当于：remote
```sh
git branch -r
```

#### 列出本地和远程分支

-a 参数相当于：all
```sh
git branch -a
```

#### 查看远程分支和本地分支的对应关系

```sh
git remote show origin
```

#### 远程删除了分支本地也想删除

```sh
git remote prune origin
```

#### 创建并切换到本地分支
```sh
git checkout -b <branch-name>
```

#### 从远程分支中创建并切换到本地分支

```sh
git checkout -b <branch-name> origin/<branch-name>
```

#### 删除本地分支

```sh
git branch -d <local-branchname>
```

#### 删除远程分支

```sh
git push origin --delete <remote-branchname>
```

或者

```sh
git push origin :<remote-branchname>
```

#### 重命名本地分支

```sh
git branch -m <new-branch-name>
```

#### 查看标签

```sh
git tag
```
展示当前分支的最近的 tag

```sh
git describe --tags --abbrev=0
```

#### 查看标签详细信息

```sh
git tag -ln
```

#### 本地创建标签

```sh
git tag <version-number>
```

默认 tag 是打在最近的一次 commit 上，如果需要指定 commit 打 tag：
```sh
$ git tag -a <version-number> -m "v1.0 发布(描述)" <commit-id>
```

#### 推送标签到远程仓库

首先要保证本地创建好了标签才可以推送标签到远程仓库：

```sh
git push origin <local-version-number>
```

一次性推送所有标签，同步到远程仓库：

```sh
git push origin --tags
```

#### 删除本地标签

```sh
git tag -d <tag-name>
```

#### 删除远程标签

```sh
git push origin --delete tag <tagname>
```

#### 切回到某个标签

一般上线之前都会打 tag，就是为了防止上线后出现问题，方便快速回退到上一版本。下面的命令是回到某一标签下的状态：
```sh
git checkout -b branch_name tag_name
```

#### 放弃工作区的修改
```sh
git checkout <file-name>
```

放弃所有修改：
```sh
git checkout .
```

#### 恢复删除的文件
```sh
git rev-list -n 1 HEAD -- <file_path> #得到 deleting_commit

git checkout <deleting_commit>^ -- <file_path> #回到删除文件 deleting_commit 之前的状态
```


#### 修改上一个 commit 的描述

如果暂存区有改动，同时也会将暂存区的改动提交到上一个 commit

```sh
git commit --amend
```

#### 查看某段代码是谁写的

```sh
git blame <file-name>
```

#### 修改作者名

```sh
git commit --amend --author='Author Name <email@address.com>'
```

#### 修改远程仓库的 url

```sh
git remote set-url origin <URL>
```

#### 增加远程仓库

```sh
git remote add origin <remote-url>
```

#### 列出所有远程仓库

```sh
git remote
```

#### 查看两个星期内的改动
```sh
git whatchanged --since='2 weeks ago'
```

#### 把 A 分支的某一个 commit，放到 B 分支上

这个过程需要 `cherry-pick` 命令，[参考](http://sg552.iteye.com/blog/1300713#bc2367928)

```sh
git checkout <branch-name> && git cherry-pick <commit-id>
```

#### 给 git 命令起别名

简化命令

```sh
git config --global alias.<handle> <command>

比如：git status 改成 git st，这样可以简化命令

git config --global alias.st status
```


## 🔺优雅的提交记录
#### commit结构
* type: 必填，描述主要修改内容的类型
* scope: 修改的范围
* subject: 描述主要修改的内容
```
<type>(<scope>): <subject>
```

#### 常用的修改类型
* feat: 新特性
* fix: 修改问题
* refactor: 代码重构
* docs: 文档修改
* style: 代码格式修改, 注意不是 css 修改
* test: 测试用例修改
* chore: 其他修改, 比如构建流程, 依赖管理.
* scope: commit 影响的范围, 比如: route, component, utils, build...
* subject: commit 的概述
* body: commit 具体修改内容, 可以分为多行
* footer: 一些备注, 通常是 BREAKING CHANGE 或修复的 bug 的链接.

## 🔺图形化客户端
* TOWER
* Sourcetree
* GitHub Desktop

## 🔺代码托管平台
* GitHub
GitHub 是第一个供“用Git进行版本控制系统的软件开发项目”使用的基于Web的代码托管服务，是目前全球最大的开源社交编程及代码托管网站。GitHub 于 2008 年 4 月 10 日正式上线，除了基本的服务以外，还提供了订阅、讨论组、文本渲染、在线文件编辑器、协作图谱（报表）、代码片段分享（Gist）等功能。

* Bitbucket
BitBucket 是 2008 年创建的源代码托管网站，采用 Mercurial 和 Git 作为分布式版本控制系统，同时提供免费账户和商业计划。2010 年被 Atlassian 收购，与 Atlassian 的其他服务(Git GUI SourceTree、HipChat、Cloud9)顺利集成，主要面向慈善企业和企业用户/其主要市场是大型企业。

* GitLab
GitLab 是一个利用 Ruby on Rails 开发的开源应用程序，实现一个自托管的 Git 项目仓库，可通过 Web 界面进行访问公开的或者私人项目。

* Coding
Coding 是一个面向开发者的云端开发平台，目前提供代码托管，运行空间，质量控制，项目管理等功能。此外，还提供社会化协作功能，包含了社交元素，方便开发者进行技术讨论和协作。2016 年 3 月 CODING 宣布收购代码托管平台 GitCafe。也许是目前国内体验最接近 github 的产品。


## 🔺学习资源
* [GIT简明指南](https://www.runoob.com/manual/git-guide/) 
* [Learn Git Branching](https://learngitbranching.js.org/)
*  [Git - Book](https://git-scm.com/book/zh/v2)


