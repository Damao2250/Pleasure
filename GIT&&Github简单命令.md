```js
// 初始化 -> 添加到缓存区 -> 提交版本描述 -> 连接到远程地址 -> 推送到远程仓库
git init  
git add .
git commit -m ''
git remote add origin + git地址
git push 



// 查看git的版本信息
git --version

// 配置用户信息
git config --global user.email "xxx@163.com"
git config --global user.name "xxx"

// 获取当前登录的用户&&登录用户的邮箱
git config --global user.name   
git config --global user.email  



// 初始化仓库
git init

// 全部添加到缓存区
git add .

// 添加版本信息
git commit -m "对当前提交的描述信息" 



// 查看版本
git log --oneline
git log

// 比较差异
// 比较的是暂存区和工作区的差异
git diff 

// 比较的是暂存区和历史区的差异
git diff --cached

// 显示目录的状体 有没有添加或者修改文件
git status



// 未使用 git add 撤销代码
git checkout .



// 不需要服务器端提交的内容可以写到忽略文件 .gitignore 里
.gitignore忽略内容如下：
/*
  .git
  .idea
*/



// 查看HEAD历史
git reflog

// 回滚最近的一个版本 
git reset --hard HEAD/commit_id


// 撤销merge
git reset --hard HEAD
// or (快速)
git merge --abort




// 分支管理
// 查看当前分支
git branch

// 查看全部分支
git branch  -a

// 查看远程分支
git branch -r

// 创建dev分支
git branch dev

// 切换分支
git checkout dev

// 创建分支并切换分支
git checkout -b dev

// 删除分支
git branch -d dev

// 在分支上提交新的版本
git commit -a -m 'dev1'

// 合并分支
git merge dev

//分支的合并后显示log
git log --oneline --graph --decorate

// 拉取远程所有分支
git fetch --all

//可以看到所有远程分支
git branch -r 

// ，假设有一个分支叫origin/mybranch，git checkout mybranch即可，会在本地新建一个同名分支，并与该远程分支关联
//（git checkout origin/mybranch 会进入detached head状态，不会在本地新建分支，不要这样写）
git checkout mybranch

// 删除某一个分支,前提是在该分支和产生该分支的主分支已经合并了(merge)
git branch -d 分支名

// 删除某一个分支,无论是否合并都强制删除
git branch -D 分支名  

// 删除远程分支
git push origin --delete [branchName]

// 同步远程已删除分支
git branch -a   // 查看本地和远程分支情况
git remote show origin // 查看本地分支和追踪情况   可以看见远程已经删除的分支
git remote prune origin  // 同步删除的分支

// 提交本地分支到远程仓库
git push origin 分支名

// 远程分支分支拉取到本地
git pull origin 分支名称

// 将master分支合并到dev分支
// 切换到dev分支, 将所有的修改进行add 以及commit 然后  git merge master  将master 的分支合并过来
// merge 遇见冲突后会直接停止，等待手动解决冲突并重新提交 commit 后，才能再次 merge
// merge 是一个合并操作，会将两个分支的修改合并在一起，默认操作的情况下会提交合并中修改的内容
git checkout dev
git merge master  // 现有的分支并不会被更改,它会比对双方不同的文件缓存下来，生成一个commit,去push
//or
git rebase matser // 修改提交历史，比对双方的commit，然后找出不同的去缓存，然后在去push，修改你的commit历史



// 与GitHub有关的：
// 先有本地库，后有远程库，将本地库push到远程库:
// 1.关联本地仓库和GitHub库
git remote add origin 网站上的仓库地址
// 2.第一次将本地仓库推送到GitHub上：
git push –u origin master

// 先有远程库，后有本地库，从远程库clone到本地库:
// 1.从远程库克隆到本地
git clone 网站上的仓库地址
// 网站地址可以选择HTTPS协议（https://github.com...）、SSH协议（git@github.com...）。
// 如果是自己的仓库可直接 add commit push

// 2. 如果克隆之后无法推送到远程库 先本地与当前远程remote切断联系
git remote remove origin
// 再
git remote add origin 网站上的仓库地址
// （.git 目录中的 Confit 文件有远程仓库的关联配置）



// SSH Key
// 如果选择SSH协议，必须将Ubuntu的公钥添加到GitHub上。

// 生成SSH Key：
ssh-keygen –t rsa –C "你的邮箱@xx.com"
// 生成Key时弹出选项，回车选择默认即可。
// Key保存位置：/root/.ssh (即C盘用户下面的，你的电脑名称的那个文件夹，里面的.ssh文件夹)
// 登陆GitHub，创建new SSH key，其内容为/root/.ssh/id_rsa.pub中文本
// 已经有了本地库和远程库，二者实现同步

// 本地库的改动提交到远程库（上传）
git push origin master

// 更新本地库至远程库的最新改动（拉取）
git pull

// 查看远程库的名称
git remote

// 查看远程仓库的详细信息
git remote -v

// 克隆一个GitHub仓库
git clone github仓库地址



// git 官网命令
git init
git add README.md
git commit -m "first commit"
git remote add origin git@github.com:Damao2250/invoiceAdmin.git
git push -u origin master




// 新建本地分支后将本地分支推送到远程库, 使用git pull 或者 git push 的时候报错如下

// gitThere is no tracking information for the current branch.
// Please specify which branch you want to merge with.
// See git-pull(1) for details
//     git pull <remote> <branch>
// If you wish to set tracking information for this branch you can do so with:
//     git branch --set-upstream-to=origin/<branch> merged0.9.6

// 是因为本地分支和远程分支没有建立联系  (使用git branch -vv  可以查看本地分支和远程分支的关联关系) 

 
//  根据命令行提示只需要执行以下命令即可
// git branch --set-upstream-to=origin/远程分支的名字 本地分支的名字   



// git fetch和git pull的区别
git pull：相当于是从远程获取最新版本并merge到本地    其实相当于git fetch 和 git merge

git fetch：相当于是从远程获取最新版本到本地，不会自动merge （相对安全）
常用操作：
git fetch origin master:tmp
git diff tmp
git merge tmp
从远程获取最新的版本到本地的test分支上
之后再进行比较合并




// Git 全局设置
git config --global user.name "周茂"
git config --global user.email "15678565370@163.com"

// 创建一个新仓库
git clone https://git.csiitl.com/frontend.csiitl.com/invoice-vue.git
cd invoice-vue
touch README.md
git add README.md
git commit -m "add README"
git push -u origin master

// 推送现有文件夹
cd existing_folder
git init
git remote add origin https://git.csiitl.com/frontend.csiitl.com/invoice-vue.git
git add .
git commit -m "Initial commit"
git push -u origin master

// 推送现有的 Git 仓库
cd existing_repo
git remote rename origin old-origin
git remote add origin https://git.csiitl.com/frontend.csiitl.com/invoice-vue.git
git push -u origin --all
git push -u origin --tags


// 本地添加到暂存区 （git push 不会提交stash）
git stash

// 查看现有的暂存
git stash list

// 恢复/弹出之前的暂存的stash
git stash pop

// 删除stash 把修改的内容都删了
git stash drop





// git push/pull 两个远程仓库
/**
 * 1.关联
 * git remote add <refs> <addr>
 */
git remote add 自定义远程名 git@git.test.com/test.git
// 查看关联的仓库
git remote -v

// 2. 代码 push
/**
 * 逐一push
 * git push <refs> <branch> (push 默认 origin)
 */
git push 自定义远程名 master
// or
git push origin master  // 推送代码到 origin 的 master 分支，可省略为：git push

// 全部push
// 在.git/congig下的[remote "origin"] 下添加新的远程仓库url， push时全部会push
[remote "origin"]
    url="git@git.test.com/test.git"

// 3. 代码pull
// git pull <refs> <branch>
git pull 自定义远程名 master
//or
git pull origin master // 拉取 origin 的 master 分支的代码，可省略为：git pull


// git修改commit（commit后未push，只能是最新一次提交的commit）
git commit --amend


```






# Git常用命令参考手册 ![](https://img.shields.io/github/license/xjh22222228/git-manual)  [git-repo](https://github.com/xjh22222228/git-manual)


基本涵盖了在开发中用到的git命令，能满足日常需求。

<center>
<img src="https://xiejiahe.gitee.io/public/tomato-work/project-9.png" />
</center>


---
# 目录
- [配置](#配置)
- [初始化本地仓库](#初始化本地仓库)
- [文件状态](#文件状态)
- [日志](#日志)
- [克隆](#克隆)
- [查看分支](#查看分支)
- [切换分支](#切换分支)
- [创建分支](#创建分支)
- [删除分支](#删除分支)
- [重命名分支](#重命名分支)
- [代码合并](#代码合并)
- [暂存](#暂存)
- [删除](#删除)
- [提交](#提交)
- [推送](#推送)
- [提交](#提交)
- [拉取最新内容](#拉取最新内容)
- [查看文件的改动](#查看文件的改动)
- [回滚版本](#回滚版本)
- [撤销](#撤销)
- [标签](#标签)
- [Git Flow](#GitFlow)
- [子模块](#子模块)
- [其他](#其他)

## 配置
```bash
# 查看配置列表
git config -l

# 查看已设置的用户名
git config --global --get user.name

# 设置用户名
git config --global user.name "xiejiahe"

# 查看已设置的邮箱
git config --global --get user.email

# 设置邮箱
git config --global user.email "example@example.com"
```

## 初始化本地仓库
```bash
# 会在当前目录生成.git
git init
```

## 文件状态
```bash
git status
```

## 日志
```bash
# 查看完整历史提交记录
git log

# 查看前N次提交记录 commit message
git log -2

# 查看前N次提交记录，包括diff
git log -p -2

# 搜索关键词
git log -S 你好

# 列出提交者贡献数量
git shortlog -sn
```


## 克隆
```bash
# https 协议
git clone https://github.com/xjh22222228/git-manual.git

# SSH协议
git clone xjh22222228@github.com/xjh22222228/git-manual.git

# 克隆某个分支， -b 后面分支名字
git clone -b v2.8.0 https://github.com/xjh22222228/git-manual.git

# 递归克隆，如果项目包含子模块就非常有用
git clone --recursive xjh22222228@github.com/xjh22222228/git-manual.git

# 克隆深度为1, 不会把历史的记录也克隆，这样可以节省克隆时间
git clone --depth=1 https://github.com/xjh22222228/git-manual.git
```



----


## 查看分支
```bash
# 查看所有分支
git branch --all

# 查看本地分支
git branch

# 查看远端分支
git branch -r
```

## 切换分支
```bash
# 2种方法，切换到master分支
git checkout master
git switch master

# 切换上一个分支
git checkout -
```

## 创建分支
```bash
# 创建develop分支
git branch develop

# 创建develop分支并切换
git checkout -b develop

# 切换远端分支
git checkout -t origin/dev
```


## 删除分支
```bash
# 删除本地分支
git branch -d <branchName>

# 删除远程分支
git branch -d -r origin/<branchName>
git push origin :<branchName>
```

## 重命名分支
```bash
# 重命名当前分支
git branch -m <branchName>
```


----


## 代码合并
```bash
# 两步法, 将 feature/v1.0.0 分支代码合并到 develop
git checkout develop
git merge feature/v1.0.0

# 或者一步法
git merge feature/v1.0.0 develop
```



## 暂存
```bash
# 暂存所有
git add -A

# 暂存某个文件
git add ./README.md

# 添加当前目录所有改动文件
git add .

# 暂存一系列文件
git add 1.txt 2.txt ...
```

## 删除
git add 的反向操作
```bash
# 删除1.txt 文件
git rm 1.txt
```

## 提交
```bash
# -m 提交的信息
git commit -m "changes log"

# 提交显示diff变化
git commit -v
```

## 推送
```bash
# 推送内容到主分支
git push -u origin master

# 本地分支推送到远程， 本地分支:远程分支
git push origin <branchName>:<branchName>

# 简写，默认推送当前分支
git push

# 强制推送, -f 是 --force 缩写
git push -f
```

----


## 拉取最新内容
```bash
# 推荐使用这个，因为不会做自动合并
git fetch origin master

# 相当于git fetch 然后 git merge
git pull

# 后面的意思是： 远程分支名:本地分支名
git pull origin master:master

# 如果是要与本地当前分支合并，则冒号后面的<本地分支名>可以不写
git pull origin master
```




----

## 查看文件的改动
```bash
# 查看所有文件改动
git diff

# 查看具体文件的改动
git diff README.md

# 查看某个版本的改动, 后面那一窜是commitId， git log后就能看到
git diff d68a1ef2407283516e8e4cb675b434505e39dc54

# 查看某个文件的历史修改记录
git log README.md
git show d68a1ef2407283516e8e4cb675b434505e39dc54 README.md
```


----

## 回滚版本
```bash
# 回滚上一个版本
git reset --hard HEAD^

# 回滚上两个版本
git reset --hard HEAD^^

# 回退到指定版本，git log 就能看到commit id了
git reset --hard 'commit id'

# 回滚版本是不保存在 git log，如果想查看使用
git reflog
```

----

## 撤销
```bash
# 撤销当前目录下所有文件的改动
git checkout -- .

# 撤销指定文件修改
git checkout -- README.md

# 暂存区回到工作区, 指定 ./README.md 文件从暂存区回到工作区
git reset HEAD ./README.md

# 撤销commit, 回到工作区, 一般commit id 是前一个
git reset <commit_id>

# 撤销commit, 并且把修改同时撤销
git reset --hard <commit_id>
```



## 标签
```bash
# 列出标签
git tag

# 按照特定模式查找标签, `*` 模板搜索
git tag -l "v1.0.0*"

# 创建带有附注标签
git tag -a v1.1.0 -m "标签描述"

# 创建轻量标签, 不需要带任何参数
git tag v1.1.0

# 后期打标签, 假设之前忘记打标签了，可以通过git log查看commit id
git log
git tag -a v1.1.0 <commit_id>

# 推送到远程，默认只是本地创建
git push origin v1.1.0

# 一次性推送所有标签到远程
git push origin --tags

# 删除标签, 你需要再次运行 git push origin v1.1.0 才能删除远程标签
git tag -d v1.1.0

# 删除远程标签
git push origin --delete v1.1.0

# 检查标签
git checkout v1.1.0
```


## Git Flow
Git Flow 不是内置命令，需要单独安装

**初始化** 每个仓库都必须初始化一次
```bash
# 通常直接回车以完成默认设置
git flow init
```

**功能**
```bash
# 开启新的功能
git flow feature start v1.1.0

# 推送到远程, 在团队协作中这一步少不了
git flow feature publish v1.1.0

# 完成功能, 会将当前分支合并到 develop 然后删除分支，回到 develop
git flow feature finish v1.1.0
```

**打补丁**
hotfix是针对 `master` 进行打补丁的
```bash
# 开启新的 hotfix
git flow hotfix start v1.1.0_hotifx

# 推送到远程
git flow hotfix publish v1.1.0_hotifx

# 完成新的hotfix, 将当前分支合并到 master 和 develop，然后删除分支，回到 develop
git flow hotfix finish v1.1.0_hotifx
```

**发布**
```bash
# 开启新的 release
git flow release start v1.1.0

# 推送到远程
git flow release publish v1.1.0

# 完成, 将当前分支合并到 master 和 develop，删除当前分支然后回到 develop
git flow release finish v1.1.0
```



## 子模块 Submodule
具体使用还可以看这里 [git submodule子模块使用教程](https://www.xiejiahe.com/blog/detail/5dbceefc0bb52b1c88c30853)
```bash
# 添加子模块
git submodule add https://github.com/xjh22222228/git-manual.git

# 更新，有2种方法
# 一步到位
git submodule update --remote
# 或者进入到子模块项目再拉取
git pull

# 修复子模块分支指向 detached head
git submodule foreach -q --recursive 'git checkout $(git config -f $toplevel/.gitmodules submodule.$name.branch || echo master)'

# 删除子模块 common 为子模块名称，一般删除需要三部
git submodule deinit <common>
#清除子模块缓存
git rm --cached common
# 提交代码并推送
git commit -am "Remove a submodule" && git push
```




## 其他
```bash
# 查看远程仓库地址
git remote -v

# 记住提交账号密码
git config --global credential.helper store

# 清除git已保存的用户名和密码
# windows
git credential-manager uninstall
# mac linux
git config --global credential.helper store

# 清除本地git缓存
git rm -r --cached .
```




## License
MIT













# 一个比较全的git文档




# Git飞行规则(Flight Rules)

🌍


#### 前言

- 英文原版[README](https://github.com/k88hudson/git-flight-rules/blob/master/README.md)


#### 什么是"飞行规则"?

一个 [宇航员指南](http://www.jsc.nasa.gov/news/columbia/fr_generic.pdf) (现在, 程序员们都在使用GIT) 是关于出现问题过后应该怎么操作。

>  *飞行规则(Flight Rules)* 是记录在手册上的来之不易的一系列知识，记录了某个事情发生的原因，以及怎样一步一步的进行处理。本质上, 它们是特定场景的非常详细的标准处理流程。 [...]

> 自20世纪60年代初以来，NASA一直在捕捉(capturing)我们的失误，灾难和解决方案, 当时水星时代(Mercury-era)的地面小组首先开始将“经验教训”收集到一个纲要(compendium)中，该纲现在已经有上千个问题情景，从发动机故障到破损的舱口把手到计算机故障，以及它们对应的解决方案。

&mdash; Chris Hadfield, *一个宇航员的生活指南(An Astronaut's Guide to Life)*。

#### 这篇文章的约定

为了清楚的表述，这篇文档里的所有例子使用了自定义的bash 提示，以便指示当前分支和是否有暂存的变化(changes)。分支名用小括号括起来，分支名后面跟的`*`表示暂存的变化(changes)。

[![Join the chat at https://gitter.im/k88hudson/git-flight-rules](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/k88hudson/git-flight-rules?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)
<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

  - [编辑提交(editting commits)](#%E7%BC%96%E8%BE%91%E6%8F%90%E4%BA%A4editting-commits)
    - [我刚才提交了什么?](#%E6%88%91%E5%88%9A%E6%89%8D%E6%8F%90%E4%BA%A4%E4%BA%86%E4%BB%80%E4%B9%88)
    - [我的提交信息(commit message)写错了](#%E6%88%91%E7%9A%84%E6%8F%90%E4%BA%A4%E4%BF%A1%E6%81%AFcommit-message%E5%86%99%E9%94%99%E4%BA%86)
    - [我提交(commit)里的用户名和邮箱不对](#%E6%88%91%E6%8F%90%E4%BA%A4commit%E9%87%8C%E7%9A%84%E7%94%A8%E6%88%B7%E5%90%8D%E5%92%8C%E9%82%AE%E7%AE%B1%E4%B8%8D%E5%AF%B9)
    - [我想从一个提交(commit)里移除一个文件](#%E6%88%91%E6%83%B3%E4%BB%8E%E4%B8%80%E4%B8%AA%E6%8F%90%E4%BA%A4commit%E9%87%8C%E7%A7%BB%E9%99%A4%E4%B8%80%E4%B8%AA%E6%96%87%E4%BB%B6)
    - [我想删除我的的最后一次提交(commit)](#%E6%88%91%E6%83%B3%E5%88%A0%E9%99%A4%E6%88%91%E7%9A%84%E7%9A%84%E6%9C%80%E5%90%8E%E4%B8%80%E6%AC%A1%E6%8F%90%E4%BA%A4commit)
    - [删除任意提交(commit)](#%E5%88%A0%E9%99%A4%E4%BB%BB%E6%84%8F%E6%8F%90%E4%BA%A4commit)
    - [我尝试推一个修正后的提交(amended commit)到远程，但是报错：](#%E6%88%91%E5%B0%9D%E8%AF%95%E6%8E%A8%E4%B8%80%E4%B8%AA%E4%BF%AE%E6%AD%A3%E5%90%8E%E7%9A%84%E6%8F%90%E4%BA%A4amended-commit%E5%88%B0%E8%BF%9C%E7%A8%8B%E4%BD%86%E6%98%AF%E6%8A%A5%E9%94%99)
    - [我意外的做了一次硬重置(hard reset)，我想找回我的内容](#%E6%88%91%E6%84%8F%E5%A4%96%E7%9A%84%E5%81%9A%E4%BA%86%E4%B8%80%E6%AC%A1%E7%A1%AC%E9%87%8D%E7%BD%AEhard-reset%E6%88%91%E6%83%B3%E6%89%BE%E5%9B%9E%E6%88%91%E7%9A%84%E5%86%85%E5%AE%B9)
  - [暂存(Staging)](#%E6%9A%82%E5%AD%98staging)
    - [我需要把暂存的内容添加到上一次的提交(commit)](#%E6%88%91%E9%9C%80%E8%A6%81%E6%8A%8A%E6%9A%82%E5%AD%98%E7%9A%84%E5%86%85%E5%AE%B9%E6%B7%BB%E5%8A%A0%E5%88%B0%E4%B8%8A%E4%B8%80%E6%AC%A1%E7%9A%84%E6%8F%90%E4%BA%A4commit)
    - [我想要暂存一个新文件的一部分，而不是这个文件的全部](#%E6%88%91%E6%83%B3%E8%A6%81%E6%9A%82%E5%AD%98%E4%B8%80%E4%B8%AA%E6%96%B0%E6%96%87%E4%BB%B6%E7%9A%84%E4%B8%80%E9%83%A8%E5%88%86%E8%80%8C%E4%B8%8D%E6%98%AF%E8%BF%99%E4%B8%AA%E6%96%87%E4%BB%B6%E7%9A%84%E5%85%A8%E9%83%A8)
    - [我想把在一个文件里的变化(changes)加到两个提交(commit)里](#%E6%88%91%E6%83%B3%E6%8A%8A%E5%9C%A8%E4%B8%80%E4%B8%AA%E6%96%87%E4%BB%B6%E9%87%8C%E7%9A%84%E5%8F%98%E5%8C%96changes%E5%8A%A0%E5%88%B0%E4%B8%A4%E4%B8%AA%E6%8F%90%E4%BA%A4commit%E9%87%8C)
    - [我想把暂存的内容变成未暂存，把未暂存的内容暂存起来](#%E6%88%91%E6%83%B3%E6%8A%8A%E6%9A%82%E5%AD%98%E7%9A%84%E5%86%85%E5%AE%B9%E5%8F%98%E6%88%90%E6%9C%AA%E6%9A%82%E5%AD%98%E6%8A%8A%E6%9C%AA%E6%9A%82%E5%AD%98%E7%9A%84%E5%86%85%E5%AE%B9%E6%9A%82%E5%AD%98%E8%B5%B7%E6%9D%A5)
  - [未暂存(Unstaged)的内容](#%E6%9C%AA%E6%9A%82%E5%AD%98unstaged%E7%9A%84%E5%86%85%E5%AE%B9)
    - [我想把未暂存的内容移动到一个新分支](#%E6%88%91%E6%83%B3%E6%8A%8A%E6%9C%AA%E6%9A%82%E5%AD%98%E7%9A%84%E5%86%85%E5%AE%B9%E7%A7%BB%E5%8A%A8%E5%88%B0%E4%B8%80%E4%B8%AA%E6%96%B0%E5%88%86%E6%94%AF)
    - [我想把未暂存的内容移动到另一个已存在的分支](#%E6%88%91%E6%83%B3%E6%8A%8A%E6%9C%AA%E6%9A%82%E5%AD%98%E7%9A%84%E5%86%85%E5%AE%B9%E7%A7%BB%E5%8A%A8%E5%88%B0%E5%8F%A6%E4%B8%80%E4%B8%AA%E5%B7%B2%E5%AD%98%E5%9C%A8%E7%9A%84%E5%88%86%E6%94%AF)
    - [我想丢弃本地未提交的变化(uncommitted changes)](#%E6%88%91%E6%83%B3%E4%B8%A2%E5%BC%83%E6%9C%AC%E5%9C%B0%E6%9C%AA%E6%8F%90%E4%BA%A4%E7%9A%84%E5%8F%98%E5%8C%96uncommitted-changes)
    - [我想丢弃某些未暂存的内容](#%E6%88%91%E6%83%B3%E4%B8%A2%E5%BC%83%E6%9F%90%E4%BA%9B%E6%9C%AA%E6%9A%82%E5%AD%98%E7%9A%84%E5%86%85%E5%AE%B9)
  - [分支(Branches)](#%E5%88%86%E6%94%AFbranches)
    - [我从错误的分支拉取了内容，或把内容拉取到了错误的分支](#%E6%88%91%E4%BB%8E%E9%94%99%E8%AF%AF%E7%9A%84%E5%88%86%E6%94%AF%E6%8B%89%E5%8F%96%E4%BA%86%E5%86%85%E5%AE%B9%E6%88%96%E6%8A%8A%E5%86%85%E5%AE%B9%E6%8B%89%E5%8F%96%E5%88%B0%E4%BA%86%E9%94%99%E8%AF%AF%E7%9A%84%E5%88%86%E6%94%AF)
    - [我想扔掉本地的提交(commit)，以便我的分支与远程的保持一致](#%E6%88%91%E6%83%B3%E6%89%94%E6%8E%89%E6%9C%AC%E5%9C%B0%E7%9A%84%E6%8F%90%E4%BA%A4commit%E4%BB%A5%E4%BE%BF%E6%88%91%E7%9A%84%E5%88%86%E6%94%AF%E4%B8%8E%E8%BF%9C%E7%A8%8B%E7%9A%84%E4%BF%9D%E6%8C%81%E4%B8%80%E8%87%B4)
    - [我需要提交到一个新分支，但错误的提交到了master](#%E6%88%91%E9%9C%80%E8%A6%81%E6%8F%90%E4%BA%A4%E5%88%B0%E4%B8%80%E4%B8%AA%E6%96%B0%E5%88%86%E6%94%AF%E4%BD%86%E9%94%99%E8%AF%AF%E7%9A%84%E6%8F%90%E4%BA%A4%E5%88%B0%E4%BA%86master)
    - [我想保留来自另外一个ref-ish的整个文件](#%E6%88%91%E6%83%B3%E4%BF%9D%E7%95%99%E6%9D%A5%E8%87%AA%E5%8F%A6%E5%A4%96%E4%B8%80%E4%B8%AAref-ish%E7%9A%84%E6%95%B4%E4%B8%AA%E6%96%87%E4%BB%B6)
    - [我把几个提交(commit)提交到了同一个分支，而这些提交应该分布在不同的分支里](#%E6%88%91%E6%8A%8A%E5%87%A0%E4%B8%AA%E6%8F%90%E4%BA%A4commit%E6%8F%90%E4%BA%A4%E5%88%B0%E4%BA%86%E5%90%8C%E4%B8%80%E4%B8%AA%E5%88%86%E6%94%AF%E8%80%8C%E8%BF%99%E4%BA%9B%E6%8F%90%E4%BA%A4%E5%BA%94%E8%AF%A5%E5%88%86%E5%B8%83%E5%9C%A8%E4%B8%8D%E5%90%8C%E7%9A%84%E5%88%86%E6%94%AF%E9%87%8C)
    - [我想删除上游(upstream)分支被删除了的本地分支](#%E6%88%91%E6%83%B3%E5%88%A0%E9%99%A4%E4%B8%8A%E6%B8%B8upstream%E5%88%86%E6%94%AF%E8%A2%AB%E5%88%A0%E9%99%A4%E4%BA%86%E7%9A%84%E6%9C%AC%E5%9C%B0%E5%88%86%E6%94%AF)
    - [我不小心删除了我的分支](#%E6%88%91%E4%B8%8D%E5%B0%8F%E5%BF%83%E5%88%A0%E9%99%A4%E4%BA%86%E6%88%91%E7%9A%84%E5%88%86%E6%94%AF)
    - [我想删除一个分支](#%E6%88%91%E6%83%B3%E5%88%A0%E9%99%A4%E4%B8%80%E4%B8%AA%E5%88%86%E6%94%AF)
    - [我想从别人正在工作的远程分支签出(checkout)一个分支](#%E6%88%91%E6%83%B3%E4%BB%8E%E5%88%AB%E4%BA%BA%E6%AD%A3%E5%9C%A8%E5%B7%A5%E4%BD%9C%E7%9A%84%E8%BF%9C%E7%A8%8B%E5%88%86%E6%94%AF%E7%AD%BE%E5%87%BAcheckout%E4%B8%80%E4%B8%AA%E5%88%86%E6%94%AF)
  - [Rebasing 和合并(Merging)](#rebasing-%E5%92%8C%E5%90%88%E5%B9%B6merging)
    - [我想撤销rebase/merge](#%E6%88%91%E6%83%B3%E6%92%A4%E9%94%80rebasemerge)
    - [我已经rebase过, 但是我不想强推(force push)](#%E6%88%91%E5%B7%B2%E7%BB%8Frebase%E8%BF%87-%E4%BD%86%E6%98%AF%E6%88%91%E4%B8%8D%E6%83%B3%E5%BC%BA%E6%8E%A8force-push)
    - [我需要组合(combine)几个提交(commit)](#%E6%88%91%E9%9C%80%E8%A6%81%E7%BB%84%E5%90%88combine%E5%87%A0%E4%B8%AA%E6%8F%90%E4%BA%A4commit)
      - [安全合并(merging)策略](#%E5%AE%89%E5%85%A8%E5%90%88%E5%B9%B6merging%E7%AD%96%E7%95%A5)
      - [我需要将一个分支合并成一个提交(commit)](#%E6%88%91%E9%9C%80%E8%A6%81%E5%B0%86%E4%B8%80%E4%B8%AA%E5%88%86%E6%94%AF%E5%90%88%E5%B9%B6%E6%88%90%E4%B8%80%E4%B8%AA%E6%8F%90%E4%BA%A4commit)
      - [我只想组合(combine)未推的提交(unpushed commit)](#%E6%88%91%E5%8F%AA%E6%83%B3%E7%BB%84%E5%90%88combine%E6%9C%AA%E6%8E%A8%E7%9A%84%E6%8F%90%E4%BA%A4unpushed-commit)
    - [检查是否分支上的所有提交(commit)都合并(merge)过了](#%E6%A3%80%E6%9F%A5%E6%98%AF%E5%90%A6%E5%88%86%E6%94%AF%E4%B8%8A%E7%9A%84%E6%89%80%E6%9C%89%E6%8F%90%E4%BA%A4commit%E9%83%BD%E5%90%88%E5%B9%B6merge%E8%BF%87%E4%BA%86)
    - [交互式rebase(interactive rebase)可能出现的问题](#%E4%BA%A4%E4%BA%92%E5%BC%8Frebaseinteractive-rebase%E5%8F%AF%E8%83%BD%E5%87%BA%E7%8E%B0%E7%9A%84%E9%97%AE%E9%A2%98)
      - [这个rebase 编辑屏幕出现'noop'](#%E8%BF%99%E4%B8%AArebase-%E7%BC%96%E8%BE%91%E5%B1%8F%E5%B9%95%E5%87%BA%E7%8E%B0noop)
      - [有冲突的情况](#%E6%9C%89%E5%86%B2%E7%AA%81%E7%9A%84%E6%83%85%E5%86%B5)
  - [杂项(Miscellaneous Objects)](#%E6%9D%82%E9%A1%B9miscellaneous-objects)
    - [克隆所有子模块](#%E5%85%8B%E9%9A%86%E6%89%80%E6%9C%89%E5%AD%90%E6%A8%A1%E5%9D%97)
    - [删除标签(tag)](#%E5%88%A0%E9%99%A4%E6%A0%87%E7%AD%BEtag)
    - [恢复已删除标签(tag)](#%E6%81%A2%E5%A4%8D%E5%B7%B2%E5%88%A0%E9%99%A4%E6%A0%87%E7%AD%BEtag)
    - [已删除补丁(patch)](#%E5%B7%B2%E5%88%A0%E9%99%A4%E8%A1%A5%E4%B8%81patch)
  - [跟踪文件(Tracking Files)](#%E8%B7%9F%E8%B8%AA%E6%96%87%E4%BB%B6tracking-files)
    - [我只想改变一个文件名字的大小写，而不修改内容](#%E6%88%91%E5%8F%AA%E6%83%B3%E6%94%B9%E5%8F%98%E4%B8%80%E4%B8%AA%E6%96%87%E4%BB%B6%E5%90%8D%E5%AD%97%E7%9A%84%E5%A4%A7%E5%B0%8F%E5%86%99%E8%80%8C%E4%B8%8D%E4%BF%AE%E6%94%B9%E5%86%85%E5%AE%B9)
    - [我想从Git删除一个文件，但保留该文件](#%E6%88%91%E6%83%B3%E4%BB%8Egit%E5%88%A0%E9%99%A4%E4%B8%80%E4%B8%AA%E6%96%87%E4%BB%B6%E4%BD%86%E4%BF%9D%E7%95%99%E8%AF%A5%E6%96%87%E4%BB%B6)
  - [配置(Configuration)](#%E9%85%8D%E7%BD%AEconfiguration)
    - [我想给一些Git命令添加别名(alias)](#%E6%88%91%E6%83%B3%E7%BB%99%E4%B8%80%E4%BA%9Bgit%E5%91%BD%E4%BB%A4%E6%B7%BB%E5%8A%A0%E5%88%AB%E5%90%8Dalias)
    - [我想缓存一个仓库(repository)的用户名和密码](#%E6%88%91%E6%83%B3%E7%BC%93%E5%AD%98%E4%B8%80%E4%B8%AA%E4%BB%93%E5%BA%93repository%E7%9A%84%E7%94%A8%E6%88%B7%E5%90%8D%E5%92%8C%E5%AF%86%E7%A0%81)
  - [我不知道我做错了些什么](#%E6%88%91%E4%B8%8D%E7%9F%A5%E9%81%93%E6%88%91%E5%81%9A%E9%94%99%E4%BA%86%E4%BA%9B%E4%BB%80%E4%B9%88)
- [其它资源(Other Resources)](#%E5%85%B6%E5%AE%83%E8%B5%84%E6%BA%90other-resources)
  - [书(Books)](#%E4%B9%A6books)
  - [教程(Tutorials)](#%E6%95%99%E7%A8%8Btutorials)
  - [脚本和工具(Scripts and Tools)](#%E8%84%9A%E6%9C%AC%E5%92%8C%E5%B7%A5%E5%85%B7scripts-and-tools)
  - [GUI客户端(GUI Clients)](#gui%E5%AE%A2%E6%88%B7%E7%AB%AFgui-clients)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 编辑提交(editting commits)

<a name="diff-last"></a>
### 我刚才提交了什么?

如果你用 `git commit -a` 提交了一次变化(changes)，而你又不确定到底这次提交了哪些内容。 你就可以用下面的命令显示当前`HEAD`上的最近一次的提交(commit):

```sh
(master)$ git show
```

或者

```sh
$ git log -n1 -p
```

<a name="#i-wrote-the-wrong-thing-in-a-commit-message"></a>
### 我的提交信息(commit message)写错了

如果你的提交信息(commit message)写错了且这次提交(commit)还没有推(push), 你可以通过下面的方法来修改提交信息(commit message):

```sh
$ git commit --amend
```
这会打开你的默认编辑器, 在这里你可以编辑信息. 另一方面, 你也可以用一条命令一次完成:

```sh
$ git commit --amend -m 'xxxxxxx'
```

如果你已经推(push)了这次提交(commit), 你可以修改这次提交(commit)然后强推(force push), 但是不推荐这么做。

<a name="commit-wrong-author"></a>
### 我提交(commit)里的用户名和邮箱不对

如果这只是单个提交(commit)，修改它：

```sh
$ git commit --amend --author "New Authorname <authoremail@mydomain.com>"
```

如果你需要修改所有历史, 参考 'git filter-branch'的指南页.

<a href="#i-want-to-remove-a-file-from-a-commit"></a>
### 我想从一个提交(commit)里移除一个文件

通过下面的方法，从一个提交(commit)里移除一个文件:

```sh
$ git checkout HEAD^ myfile
$ git add -A
$ git commit --amend
```

这将非常有用，当你有一个开放的补丁(open patch)，你往上面提交了一个不必要的文件，你需要强推(force push)去更新这个远程补丁。

<a name="delete-pushed-commit"></a>
### 我想删除我的的最后一次提交(commit)

如果你需要删除推了的提交(pushed commits)，你可以使用下面的方法。可是，这会不可逆的改变你的历史，也会搞乱那些已经从该仓库拉取(pulled)了的人的历史。简而言之，如果你不是很确定，千万不要这么做。

```sh
$ git reset HEAD^ --hard
$ git push -f [remote] [branch]
```

如果你还没有推到远程, 把Git重置(reset)到你最后一次提交前的状态就可以了(同时保存暂存的变化):

```
(my-branch*)$ git reset --soft HEAD@{1}

```

这只能在没有推送之前有用. 如果你已经推了, 唯一安全能做的是 `git revert SHAofBadCommit`， 那会创建一个新的提交(commit)用于撤消前一个提交的所有变化(changes)； 或者, 如果你推的这个分支是rebase-safe的 (例如： 其它开发者不会从这个分支拉), 只需要使用 `git push -f`； 更多, 请参考 [the above section](#deleteremove-last-pushed-commit)。

<a name="delete-any-commit"></a>
### 删除任意提交(commit)

同样的警告：不到万不得已的时候不要这么做.

```sh
$ git rebase --onto SHA1_OF_BAD_COMMIT^ SHA1_OF_BAD_COMMIT
$ git push -f [remote] [branch]
```

或者做一个 [交互式rebase](#interactive-rebase) 删除那些你想要删除的提交(commit)里所对应的行。

<a name="#force-push"></a>
### 我尝试推一个修正后的提交(amended commit)到远程，但是报错：

```sh
To https://github.com/yourusername/repo.git
! [rejected]        mybranch -> mybranch (non-fast-forward)
error: failed to push some refs to 'https://github.com/tanay1337/webmaker.org.git'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details.
```

注意, rebasing(见下面)和修正(amending)会用一个**新的提交(commit)代替旧的**, 所以如果之前你已经往远程仓库上推过一次修正前的提交(commit)，那你现在就必须强推(force push) (`-f`)。 注意 &ndash; *总是* 确保你指明一个分支!

```sh
(my-branch)$ git push origin mybranch -f
```

一般来说, **要避免强推**. 最好是创建和推(push)一个新的提交(commit)，而不是强推一个修正后的提交。后者会使那些与该分支或该分支的子分支工作的开发者，在源历史中产生冲突。

<a href="undo-git-reset-hard"></a>
### 我意外的做了一次硬重置(hard reset)，我想找回我的内容

如果你意外的做了 `git reset --hard`, 你通常能找回你的提交(commit), 因为Git对每件事都会有日志，且都会保存几天。

```sh
(master)$ git reflog
```

你将会看到一个你过去提交(commit)的列表, 和一个重置的提交。 选择你想要回到的提交(commit)的SHA，再重置一次:

```sh
(master)$ git reset --hard SHA1234
```

这样就完成了。

## 暂存(Staging)

<a href="#i-need-to-add-staged-changes-to-the-previous-commit"></a>
### 我需要把暂存的内容添加到上一次的提交(commit)

```sh
(my-branch*)$ git commit --amend

```

<a name="commit-partial-new-file"></a>
### 我想要暂存一个新文件的一部分，而不是这个文件的全部

一般来说, 如果你想暂存一个文件的一部分, 你可这样做:

```sh
$ git add --patch filename.x
```

`-p` 简写。这会打开交互模式， 你将能够用 `s` 选项来分隔提交(commit)； 然而, 如果这个文件是新的, 会没有这个选择， 添加一个新文件时, 这样做:

```sh
$ git add -N filename.x
```

然后, 你需要用 `e` 选项来手动选择需要添加的行，执行 `git diff --cached` 将会显示哪些行暂存了哪些行只是保存在本地了。

<a href="stage-in-two-commits"></a>
### 我想把在一个文件里的变化(changes)加到两个提交(commit)里

`git add` 会把整个文件加入到一个提交. `git add -p` 允许交互式的选择你想要提交的部分.

<a href="unstaging-edits-and-staging-the-unstaged"></a>
### 我想把暂存的内容变成未暂存，把未暂存的内容暂存起来

这个有点困难， 我能想到的最好的方法是先stash未暂存的内容， 然后重置(reset)，再pop第一步stashed的内容, 最后再add它们。

```sh
$ git stash -k
$ git reset --hard
$ git stash pop
$ git add -A
```

## 未暂存(Unstaged)的内容

<a href="move-unstaged-edits-to-new-branch"></a>
### 我想把未暂存的内容移动到一个新分支

```sh
$ git checkout -b my-branch
```

<a href="move-unstaged-edits-to-old-branch"></a>
### 我想把未暂存的内容移动到另一个已存在的分支

```sh
$ git stash
$ git checkout my-branch
$ git stash pop
```

<a href="i-want-to-discard-my-local-uncommitted-changes"></a>
### 我想丢弃本地未提交的变化(uncommitted changes)

如果你只是想重置源(origin)和你本地(local)之间的一些提交(commit)，你可以：

```sh
# one commit
(my-branch)$ git reset --hard HEAD^
# two commits
(my-branch)$ git reset --hard HEAD^^
# four commits
(my-branch)$ git reset --hard HEAD~4
# or
(master)$ git checkout -f
```

重置某个特殊的文件, 你可以用文件名做为参数:

```sh
$ git reset filename
```

<a href="i-want-to-discard-specific-unstaged-changes"></a>
### 我想丢弃某些未暂存的内容

如果你想丢弃工作拷贝中的一部分内容，而不是全部。

签出(checkout)不需要的内容，保留需要的。

```sh
$ git checkout -p
# Answer y to all of the snippets you want to drop
```

另外一个方法是使用 `stash`， Stash所有要保留下的内容, 重置工作拷贝, 重新应用保留的部分。

```sh
$ git stash -p
# Select all of the snippets you want to save
$ git reset --hard
$ git stash pop
```

或者, stash 你不需要的部分, 然后stash drop。

```sh
$ git stash -p
# Select all of the snippets you don't want to save
$ git stash drop
```

## 分支(Branches)

<a name="pull-wrong-branch"></a>
### 我从错误的分支拉取了内容，或把内容拉取到了错误的分支

这是另外一种使用 `git reflog` 情况，找到在这次错误拉(pull) 之前HEAD的指向。

```sh
(master)$ git reflog
ab7555f HEAD@{0}: pull origin wrong-branch: Fast-forward
c5bc55a HEAD@{1}: checkout: checkout message goes here
```

重置分支到你所需的提交(desired commit):

```sh
$ git reset --hard c5bc55a
```

完成。

<a href="discard-local-commits"></a>
### 我想扔掉本地的提交(commit)，以便我的分支与远程的保持一致

先确认你没有推(push)你的内容到远程。

`git status` 会显示你领先(ahead)源(origin)多少个提交:

```sh
(my-branch)$ git status
# On branch my-branch
# Your branch is ahead of 'origin/my-branch' by 2 commits.
#   (use "git push" to publish your local commits)
#
```

一种方法是:

```sh
(master)$ git reset --hard origin/my-branch
```

<a name="commit-wrong-branch"></a>
### 我需要提交到一个新分支，但错误的提交到了master

在master下创建一个新分支，不切换到新分支,仍在master下:

```sh
(master)$ git branch my-branch
```

把master分支重置到前一个提交:

```sh
(master)$ git reset --hard HEAD^
```

`HEAD^` 是 `HEAD^1` 的简写，你可以通过指定要设置的`HEAD`来进一步重置。

或者, 如果你不想使用 `HEAD^`, 找到你想重置到的提交(commit)的hash(`git log` 能够完成)， 然后重置到这个hash。 使用`git push` 同步内容到远程。

例如, master分支想重置到的提交的hash为`a13b85e`:

```sh
(master)$ git reset --hard a13b85e
HEAD is now at a13b85e
```

签出(checkout)刚才新建的分支继续工作:

```sh
(master)$ git checkout my-branch
```

<a name="keep-whole-file"></a>
### 我想保留来自另外一个ref-ish的整个文件

假设你正在做一个原型方案(原文为working spike (see note)), 有成百的内容，每个都工作得很好。现在, 你提交到了一个分支，保存工作内容:

```sh
(solution)$ git add -A && git commit -m "Adding all changes from this spike into one big commit."
```

当你想要把它放到一个分支里 (可能是`feature`, 或者 `develop`), 你关心是保持整个文件的完整，你想要一个大的提交分隔成比较小。

假设你有:

  * 分支 `solution`, 拥有原型方案， 领先 `develop` 分支。
  * 分支 `develop`, 在这里你应用原型方案的一些内容。

我去可以通过把内容拿到你的分支里，来解决这个问题:

```sh
(develop)$ git checkout solution -- file1.txt
```

这会把这个文件内容从分支 `solution` 拿到分支 `develop` 里来:

```sh
# On branch develop
# Your branch is up-to-date with 'origin/develop'.
# Changes to be committed:
#  (use "git reset HEAD <file>..." to unstage)
#
#        modified:   file1.txt
```

然后, 正常提交。

Note: Spike solutions are made to analyze or solve the problem. These solutions are used for estimation and discarded once everyone gets clear visualization of the problem. ~ [Wikipedia](https://en.wikipedia.org/wiki/Extreme_programming_practices).

<a name="cherry-pick"></a>
### 我把几个提交(commit)提交到了同一个分支，而这些提交应该分布在不同的分支里

假设你有一个`master`分支， 执行`git log`, 你看到你做过两次提交:

```sh
(master)$ git log

commit e3851e817c451cc36f2e6f3049db528415e3c114
Author: Alex Lee <alexlee@example.com>
Date:   Tue Jul 22 15:39:27 2014 -0400

    Bug #21 - Added CSRF protection

commit 5ea51731d150f7ddc4a365437931cd8be3bf3131
Author: Alex Lee <alexlee@example.com>
Date:   Tue Jul 22 15:39:12 2014 -0400

    Bug #14 - Fixed spacing on title

commit a13b85e984171c6e2a1729bb061994525f626d14
Author: Aki Rose <akirose@example.com>
Date:   Tue Jul 21 01:12:48 2014 -0400

    First commit
```

让我们用提交hash(commit hash)标记bug (`e3851e8` for #21, `5ea5173` for #14).

首先, 我们把`master`分支重置到正确的提交(`a13b85e`):

```sh
(master)$ git reset --hard a13b85e
HEAD is now at a13b85e
```

现在, 我们对 bug #21 创建一个新的分支:

```sh
(master)$ git checkout -b 21
(21)$
```

接着, 我们用 *cherry-pick* 把对bug #21的提交放入当前分支。 这意味着我们将应用(apply)这个提交(commit)，仅仅这一个提交(commit)，直接在HEAD上面。

```sh
(21)$ git cherry-pick e3851e8
```

这时候, 这里可能会产生冲突， 参见[交互式 rebasing 章](#interactive-rebase) [**冲突节**](#merge-conflict) 解决冲突.

再者， 我们为bug #14 创建一个新的分支, 也基于`master`分支

```sh
(21)$ git checkout master
(master)$ git checkout -b 14
(14)$
```

最后, 为 bug #14 执行 `cherry-pick`:

```sh
(14)$ git cherry-pick 5ea5173
```

<a name="delete-stale-local-branches"></a>
### 我想删除上游(upstream)分支被删除了的本地分支
一旦你在github 上面合并(merge)了一个pull request, 你就可以删除你fork里被合并的分支。 如果你不准备继续在这个分支里工作, 删除这个分支的本地拷贝会更干净，使你不会陷入工作分支和一堆陈旧分支的混乱之中。

```sh
$ git fetch -p
```

<a name='restore-a-deleted-branch'></a>
### 我不小心删除了我的分支

如果你定期推送到远程, 多数情况下应该是安全的，但有些时候还是可能删除了还没有推到远程的分支。 让我们先创建一个分支和一个新的文件:

```sh
(master)$ git checkout -b my-branch
(my-branch)$ git branch
(my-branch)$ touch foo.txt
(my-branch)$ ls
README.md foo.txt
```

添加文件并做一次提交

```sh
(my-branch)$ git add .
(my-branch)$ git commit -m 'foo.txt added'
(my-branch)$ foo.txt added
 1 files changed, 1 insertions(+)
 create mode 100644 foo.txt
(my-branch)$ git log

commit 4e3cd85a670ced7cc17a2b5d8d3d809ac88d5012
Author: siemiatj <siemiatj@example.com>
Date:   Wed Jul 30 00:34:10 2014 +0200

    foo.txt added

commit 69204cdf0acbab201619d95ad8295928e7f411d5
Author: Kate Hudson <katehudson@example.com>
Date:   Tue Jul 29 13:14:46 2014 -0400

    Fixes #6: Force pushing after amending commits
```

现在我们切回到主(master)分支，‘不小心的’删除`my-branch`分支

```sh
(my-branch)$ git checkout master
Switched to branch 'master'
Your branch is up-to-date with 'origin/master'.
(master)$ git branch -D my-branch
Deleted branch my-branch (was 4e3cd85).
(master)$ echo oh noes, deleted my branch!
oh noes, deleted my branch!
```

在这时候你应该想起了`reflog`, 一个升级版的日志，它存储了仓库(repo)里面所有动作的历史。

```
(master)$ git reflog
69204cd HEAD@{0}: checkout: moving from my-branch to master
4e3cd85 HEAD@{1}: commit: foo.txt added
69204cd HEAD@{2}: checkout: moving from master to my-branch
```

正如你所见，我们有一个来自删除分支的提交hash(commit hash)，接下来看看是否能恢复删除了的分支。

```sh
(master)$ git checkout -b my-branch-help
Switched to a new branch 'my-branch-help'
(my-branch-help)$ git reset --hard 4e3cd85
HEAD is now at 4e3cd85 foo.txt added
(my-branch-help)$ ls
README.md foo.txt
```

看! 我们把删除的文件找回来了。 Git的 `reflog` 在rebasing出错的时候也是同样有用的。

<a name="i-want-to-delete-a-branch"></a>
### 我想删除一个分支

删除一个远程分支:

```sh
(master)$ git push origin --delete my-branch
```

你也可以:

```sh
(master)$ git push origin :my-branch
```

删除一个本地分支:

```sh
(master)$ git branch -D my-branch
```

<a name="i-want-to-checkout-to-a-remote-branch-that-someone-else-is-working-on"></a>
### 我想从别人正在工作的远程分支签出(checkout)一个分支

首先, 从远程拉取(fetch) 所有分支:

```sh
(master)$ git fetch --all
```

假设你想要从远程的`daves`分支签出到本地的`daves`

```sh
(master)$ git checkout --track origin/daves
Branch daves set up to track remote branch daves from origin.
Switched to a new branch 'daves'
```

(`--track` 是 `git checkout -b [branch] [remotename]/[branch]` 的简写)

这样就得到了一个`daves`分支的本地拷贝, 任何推过(pushed)的更新，远程都能看到.

## Rebasing 和合并(Merging)

<a name="undo-rebase"></a>
### 我想撤销rebase/merge

你可以合并(merge)或rebase了一个错误的分支, 或者完成不了一个进行中的rebase/merge。 Git 在进行危险操作的时候会把原始的HEAD保存在一个叫ORIG_HEAD的变量里, 所以要把分支恢复到rebase/merge前的状态是很容易的。

```sh
(my-branch)$ git reset --hard ORIG_HEAD
```

<a name="force-push-rebase"></a>
### 我已经rebase过, 但是我不想强推(force push)

不幸的是，如果你想把这些变化(changes)反应到远程分支上，你就必须得强推(force push)。 是因你快进(Fast forward)了提交，改变了Git历史, 远程分支不会接受变化(changes)，除非强推(force push)。这就是许多人使用 merge 工作流, 而不是 rebasing 工作流的主要原因之一， 开发者的强推(force push)会使大的团队陷入麻烦。使用时需要注意，一种安全使用 rebase 的方法是，不要把你的变化(changes)反映到远程分支上, 而是按下面的做:

```sh
(master)$ git checkout my-branch
(my-branch)$ git rebase -i master
(my-branch)$ git checkout master
(master)$ git merge --ff-only my-branch
```

更多, 参见 [this SO thread](http://stackoverflow.com/questions/11058312/how-can-i-use-git-rebase-without-requiring-a-forced-push).

<a name="interactive-rebase"></a>
### 我需要组合(combine)几个提交(commit)

假设你的工作分支将会做对于 `master` 的pull-request。 一般情况下你不关心提交(commit)的时间戳，只想组合 *所有* 提交(commit) 到一个单独的里面, 然后重置(reset)重提交(recommit)。 确保主(master)分支是最新的和你的变化都已经提交了, 然后:

```sh
(my-branch)$ git reset --soft master
(my-branch)$ git commit -am "New awesome feature"
```

如果你想要更多的控制, 想要保留时间戳, 你需要做交互式rebase (interactive rebase):

```sh
(my-branch)$ git rebase -i master
```

如果没有相对的其它分支， 你将不得不相对自己的`HEAD` 进行 rebase。 例如：你想组合最近的两次提交(commit), 你将相对于`HEAD~2` 进行rebase， 组合最近3次提交(commit), 相对于`HEAD~3`, 等等。

```sh
(master)$ git rebase -i HEAD~2
```

在你执行了交互式 rebase的命令(interactive rebase command)后, 你将在你的编辑器里看到类似下面的内容:

```vim
pick a9c8a1d Some refactoring
pick 01b2fd8 New awesome feature
pick b729ad5 fixup
pick e3851e8 another fix

# Rebase 8074d12..b729ad5 onto 8074d12
#
# Commands:
#  p, pick = use commit
#  r, reword = use commit, but edit the commit message
#  e, edit = use commit, but stop for amending
#  s, squash = use commit, but meld into previous commit
#  f, fixup = like "squash", but discard this commit's log message
#  x, exec = run command (the rest of the line) using shell
#
# These lines can be re-ordered; they are executed from top to bottom.
#
# If you remove a line here THAT COMMIT WILL BE LOST.
#
# However, if you remove everything, the rebase will be aborted.
#
# Note that empty commits are commented out
```

所有以 `#` 开头的行都是注释, 不会影响 rebase.

然后，你可以用任何上面命令列表的命令替换 `pick`, 你也可以通过删除对应的行来删除一个提交(commit)。

例如, 如果你想 **单独保留最旧(first)的提交(commit),组合所有剩下的到第二个里面**, 你就应该编辑第二个提交(commit)后面的每个提交(commit) 前的单词为 `f`:

```vim
pick a9c8a1d Some refactoring
pick 01b2fd8 New awesome feature
f b729ad5 fixup
f e3851e8 another fix
```

如果你想组合这些提交(commit) **并重命名这个提交(commit)**, 你应该在第二个提交(commit)旁边添加一个`r`，或者更简单的用`s` 替代 `f`:

```vim
pick a9c8a1d Some refactoring
pick 01b2fd8 New awesome feature
s b729ad5 fixup
s e3851e8 another fix
```

你可以在接下来弹出的文本提示框里重命名提交(commit)。

```vim
Newer, awesomer features

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
# rebase in progress; onto 8074d12
# You are currently editing a commit while rebasing branch 'master' on '8074d12'.
#
# Changes to be committed:
#	modified:   README.md
#

```

如果成功了, 你应该看到类似下面的内容:

```sh
(master)$ Successfully rebased and updated refs/heads/master.
```

#### 安全合并(merging)策略
`--no-commit` 执行合并(merge)但不自动提交, 给用户在做提交前检查和修改的机会。 `no-ff` 会为特性分支(feature branch)的存在过留下证据, 保持项目历史一致。

```sh
(master)$ git merge --no-ff --no-commit my-branch
```

#### 我需要将一个分支合并成一个提交(commit)

```sh
(master)$ git merge --squash my-branch
```

<a name="rebase-unpushed-commits"></a>
#### 我只想组合(combine)未推的提交(unpushed commit)

有时候，在将数据推向上游之前，你有几个正在进行的工作提交(commit)。这时候不希望把已经推(push)过的组合进来，因为其他人可能已经有提交(commit)引用它们了。

```sh
(master)$ git rebase -i @{u}
```

这会产生一次交互式的rebase(interactive rebase), 只会列出没有推(push)的提交(commit)， 在这个列表时进行reorder/fix/squash 都是安全的。

<a name="check-if-all-commits-on-a-branch-are-merged"></a>
### 检查是否分支上的所有提交(commit)都合并(merge)过了

检查一个分支上的所有提交(commit)是否都已经合并(merge)到了其它分支, 你应该在这些分支的head(或任何 commits)之间做一次diff:

```sh
(master)$ git log --graph --left-right --cherry-pick --oneline HEAD...feature/120-on-scroll
```

这会告诉你在一个分支里有而另一个分支没有的所有提交(commit), 和分支之间不共享的提交(commit)的列表。 另一个做法可以是:

```sh
(master)$ git log master ^feature/120-on-scroll --no-merges
```

### 交互式rebase(interactive rebase)可能出现的问题

<a name="noop"></a>
#### 这个rebase 编辑屏幕出现'noop'

如果你看到的是这样:
```
noop
```

这意味着你rebase的分支和当前分支在同一个提交(commit)上, 或者 *领先(ahead)* 当前分支。 你可以尝试:

* 检查确保主(master)分支没有问题
* rebase  `HEAD~2` 或者更早

<a name="merge-conflict"></a>
#### 有冲突的情况

如果你不能成功的完成rebase, 你可能必须要解决冲突。

首先执行 `git status` 找出哪些文件有冲突:

```sh
(my-branch)$ git status
On branch my-branch
Changes not staged for commit:
  (use "git add <file>..." to update what will be committed)
  (use "git checkout -- <file>..." to discard changes in working directory)

	modified:   README.md
```

在这个例子里面, `README.md` 有冲突。 打开这个文件找到类似下面的内容:

```vim
   <<<<<<< HEAD
   some code
   =========
   some code
   >>>>>>> new-commit
```

你需要解决新提交的代码(示例里, 从中间`==`线到`new-commit`的地方)与`HEAD` 之间不一样的地方.

有时候这些合并非常复杂，你应该使用可视化的差异编辑器(visual diff editor):

```sh
(master*)$ git mergetool -t opendiff
```

在你解决完所有冲突和测试过后, `git add` 变化了的(changed)文件, 然后用`git rebase --continue` 继续rebase。

```sh
(my-branch)$ git add README.md
(my-branch)$ git rebase --continue
```

如果在解决完所有的冲突过后，得到了与提交前一样的结果, 可以执行`git rebase --skip`。

任何时候你想结束整个rebase 过程，回来rebase前的分支状态, 你可以做:

```sh
(my-branch)$ git rebase --abort
```

<a name="miscellaneous-objects"></a>
## 杂项(Miscellaneous Objects)

<a name="clone-submodules"></a>
### 克隆所有子模块

```sh
$ git clone --recursive git://github.com/foo/bar.git
```

如果已经克隆了:

```sh
$ git submodule update --init --recursive
```

<a name="delete-tag"></a>
### 删除标签(tag)

```sh
$ git tag -d <tag_name>
$ git push <remote> :refs/tags/<tag_name>
```

<a name="recover-tag"></a>
### 恢复已删除标签(tag)

如果你想恢复一个已删除标签(tag), 可以按照下面的步骤: 首先, 需要找到无法访问的标签(unreachable tag):

```sh
$ git fsck --unreachable | grep tag
```

记下这个标签(tag)的hash，然后用Git的 [update-ref](http://git-scm.com/docs/git-update-ref):

```sh
$ git update-ref refs/tags/<tag_name> <hash>
```

这时你的标签(tag)应该已经恢复了。

<a name="deleted-patch"></a>
### 已删除补丁(patch)

如果某人在 GitHub 上给你发了一个pull request, 但是然后他删除了他自己的原始 fork, 你将没法克隆他们的提交(commit)或使用 `git am`。在这种情况下, 最好手动的查看他们的提交(commit)，并把它们拷贝到一个本地新分支，然后做提交。

做完提交后, 再修改作者，参见[变更作者](#commit-wrong-author)。 然后, 应用变化, 再发起一个新的pull request。

## 跟踪文件(Tracking Files)

<a href="i-want-to-change-a-file-names-capitalization-without-changing-the-contents-of-the-file"></a>
### 我只想改变一个文件名字的大小写，而不修改内容

```sh
(master)$ git mv --force myfile MyFile
```

<a href="remove-from-git"></a>
### 我想从Git删除一个文件，但保留该文件

```sh
(master)$ git rm --cached log.txt
```

## 配置(Configuration)

<a name="adding-command-aliases"></a>
### 我想给一些Git命令添加别名(alias)

在 OS X 和 Linux 下, 你的 Git的配置文件储存在 ```~/.gitconfig```。我在```[alias]``` 部分添加了一些快捷别名(和一些我容易拼写错误的)，如下:

```vim
[alias]
    a = add
    amend = commit --amend
    c = commit
    ca = commit --amend
    ci = commit -a
    co = checkout
    d = diff
    dc = diff --changed
    ds = diff --staged
    f = fetch
    loll = log --graph --decorate --pretty=oneline --abbrev-commit
    m = merge
    one = log --pretty=oneline
    outstanding = rebase -i @{u}
    s = status
    unpushed = log @{u}
    wc = whatchanged
    wip = rebase -i @{u}
    zap = fetch -p
```

<a name="credential-helper"></a>
### 我想缓存一个仓库(repository)的用户名和密码

你可能有一个仓库需要授权，这时你可以缓存用户名和密码，而不用每次推/拉(push/pull)的时候都输入，Credential helper能帮你。

```sh
$ git config --global credential.helper cache
# Set git to use the credential memory cache
```

```sh
$ git config --global credential.helper 'cache --timeout=3600'
# Set the cache to timeout after 1 hour (setting is in seconds)
```

<a href="#ive-no-idea-what-i-did-wrong"></a>
## 我不知道我做错了些什么

你把事情搞砸了：你 `重置(reset)` 了一些东西, 或者你合并了错误的分支, 亦或你强推了后找不到你自己的提交(commit)了。有些时候, 你一直都做得很好, 但你想回到以前的某个状态。

这就是 `git reflog` 的目的， `reflog` 记录对分支顶端(the tip of a branch)的任何改变, 即使那个顶端没有被任何分支或标签引用。基本上, 每次HEAD的改变, 一条新的记录就会增加到`reflog`。遗憾的是，这只对本地分支起作用，且它只跟踪动作 (例如，不会跟踪一个没有被记录的文件的任何改变)。

```sh
(master)$ git reflog
0a2e358 HEAD@{0}: reset: moving to HEAD~2
0254ea7 HEAD@{1}: checkout: moving from 2.2 to master
c10f740 HEAD@{2}: checkout: moving from master to 2.2
```

上面的reflog展示了从master分支签出(checkout)到2.2 分支，然后再签回。 那里，还有一个硬重置(hard reset)到一个较旧的提交。最新的动作出现在最上面以 `HEAD@{0}`标识.

如果事实证明你不小心回移(move back)了提交(commit), reflog 会包含你不小心回移前master上指向的提交(0254ea7)。

```sh
$ git reset --hard 0254ea7
```

然后使用git reset就可以把master改回到之前的commit，这提供了一个在历史被意外更改情况下的安全网。

([摘自](https://www.atlassian.com/git/tutorials/rewriting-history/git-reflog)).

# 其它资源(Other Resources)

## 书(Books)

* [Pro Git](https://git-scm.com/book/en/v2) - Scott Chacon's excellent git book
* [Git Internals](https://github.com/pluralsight/git-internals-pdf) - Scott Chacon's other excellent git book

## 教程(Tutorials)

* [Learn Git branching](https://learngitbranching.js.org/) 一个基于网页的交互式 branching/merging/rebasing 教程
* [Getting solid at Git rebase vs. merge](https://medium.com/@porteneuve/getting-solid-at-git-rebase-vs-merge-4fa1a48c53aa)
* [git-workflow](https://github.com/asmeurer/git-workflow) - [Aaron Meurer](https://github.com/asmeurer)的怎么使用Git为开源仓库贡献
* [GitHub as a workflow](http://hugogiraudel.com/2015/08/13/github-as-a-workflow/) - 使用GitHub做为工作流的趣事, 尤其是空PRs

## 脚本和工具(Scripts and Tools)

* [firstaidgit.io](http://firstaidgit.io/) 一个可搜索的最常被问到的Git的问题
* [git-extra-commands](https://github.com/unixorn/git-extra-commands) - 一堆有用的额外的Git脚本
* [git-extras](https://github.com/tj/git-extras) - GIT 工具集 -- repo summary, repl, changelog population, author commit percentages and more
* [git-fire](https://github.com/qw3rtman/git-fire) - git-fire 是一个 Git 插件，用于帮助在紧急情况下添加所有当前文件, 做提交(committing), 和推(push)到一个新分支(阻止合并冲突)。
* [git-tips](https://github.com/git-tips/tips) - Git小提示
* [git-town](https://github.com/Originate/git-town) - 通用，高级Git工作流支持！ http://www.git-town.com

## GUI客户端(GUI Clients)
* [GitKraken](https://www.gitkraken.com/) - 豪华的Git客户端 Windows, Mac & Linux
* [git-cola](https://git-cola.github.io/) - 另外一个Git客户端 Windows & OS X
* [GitUp](https://github.com/git-up/GitUp) - 一个新的Git客户端，在处理Git的复杂性上有自己的特点
* [gitx-dev](https://rowanj.github.io/gitx/) - 图形化的Git客户端 OS X
* [Source Tree](https://www.sourcetreeapp.com/) - 免费的图形化Git客户端 Windows & OS X
* [Tower](http://www.git-tower.com/) - 图形化Git客户端 OS X(付费)
