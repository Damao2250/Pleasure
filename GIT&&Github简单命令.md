```js
//查看git的版本信息
git --version  

//配置用户信息
git config --global user.email "xxx@163.com"
git config --global user.name "xxx"

//获取当前登录的用户&&登录用户的邮箱
git config --global user.name   
git config --global user.email  

//初始化仓库
git init

//全部添加到缓存区
git add .

//添加版本信息
git commit -m "对当前提交的描述信息" 

//查看版本
git log --oneline
//比较差异
//比较的是暂存区和工作区的差异
git diff 
//比较的是暂存区和历史区的差异
git diff --cached

//显示目录的状体 有没有添加或者修改文件
git status

//不需要服务器端提交的内容可以写到忽略文件 .gitignore 里
.gitignore忽略内容如下：
    /*
        .git
        .idea
    */

//回滚最近的一个版本 
//查看
git log
//回滚
git reset --hard HEAD/commit_id

//分支管理
//查看当前分支
git branch
//查看全部分支
git branch  -a 
//创建dev分支
git branch dev
//切换分支
git checkout dev
//创建分支并切换分支
git checkout -b dev
//删除分支
git branch -d dev
//在分支上提交新的版本
git commit -a -m 'dev1'
//合并分支
git merge dev
//分支的合并后显示log
git log --oneline --graph --decorate

// 删除某一个分支,前提是在该分支和产生该分支的主分支已经合并了(merge)
$ git branch -d 分支名
// 删除某一个分支,无论是否合并都强制删除
$ git branch -D 分支名  

//与GitHub有关的：
//先有本地库，后有远程库，将本地库push到远程库:
//1.关联本地仓库和GitHub库
git remote add origin 网站上的仓库地址
//2.第一次将本地仓库推送到GitHub上：
git push –u origin master

//先有远程库，后有本地库，从远程库clone到本地库:
//1.从远程库克隆到本地
git clone 网站上的仓库地址
//网站地址可以选择HTTPS协议（https://github.com...）、SSH协议（git@github.com...）。

//SSH Key
//如果选择SSH协议，必须将Ubuntu的公钥添加到GitHub上。

//生成SSH Key：
ssh-keygen –t rsa –C "你的邮箱@xx.com"
//生成Key时弹出选项，回车选择默认即可。
//Key保存位置：/root/.ssh (即C盘用户下面的，你的电脑名称的那个文件夹，里面的.ssh文件夹)
//登陆GitHub，创建new SSH key，其内容为/root/.ssh/id_rsa.pub中文本
//已经有了本地库和远程库，二者实现同步

//本地库的改动提交到远程库（上传）
git push origin master
//更新本地库至远程库的最新改动（拉取）
git pull

//要查看远程库的信息、
git remote
//显示更详细的信息
git remote -v

//克隆一个GitHub仓库
git clone github仓库地址

```