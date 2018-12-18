### git svn

- SVN属于集中化的版本控制系统，有个不太精确的比喻:SVN = 版本控制+ 备份服务器
- SVN使用起来有点像是档案仓库的感觉，支持并行读写文件，支持代码的版本化管理，功能包括取出、导入、更新、分支、改名、还原、合并等。

    - SVN 的优缺点

        SVN对中文支持好，操作简单，使用没有难度，美工人员，产品人员，测试人员，实施人员都可轻松上手。使用界面统一，功能完善，操作方便。

- Git是一个分布式版本控制系统，操作命令包括：clone，pull，push,branch ,merge ,push,rebase，Git擅长的是程序代码的版本化管理。

    - Git的优缺点

      对程序源代码进行差异化的版本管理，代码库占极少的空间。易于代码的分支化管理。不支持中文，图形界面支持差，使用难度大。不易推广。

### npm

- NPM（node package manager），通常称为node包管理器。顾名思义，它的主要功能就是管理node包，包括：安装、卸载、更新、查看、搜索、发布等。
- 

### 25、Node的应用场景

- 特点：
  - 1、它是一个`Javascript`运行环境
  - 2、依赖于`Chrome V8`引擎进行代码解释
  - 3、事件驱动
  - 4、非阻塞`I/O`
  - 5、单进程，单线程

- 优点：
  - 高并发（最重要的优点）

- 缺点：
  - 1、只支持单`核CPU`，不能充分利用`CPU`
  - 2、可靠性低，一旦代码某个环节崩溃，整个系统都崩溃

### PHP

是什么
- PHP 是服务器端脚本语言。
- PHP（全称：PHP：Hypertext Preprocessor，即"PHP：超文本预处理器"）是一种通用开源脚本语言。
- PHP 脚本在服务器上执行。
- PHP 文件可包含文本、HTML、JavaScript代码和 PHP 代码
- PHP 代码在服务器上执行，结果以纯 HTML 形式返回给浏览器

能做什么
- PHP 可以生成动态页面内容
- PHP 可以创建、打开、读取、写入、关闭服务器上的文件
- PHP 可以收集表单数据
- PHP 可以发送和接收 cookies
- PHP 可以添加、删除、修改您的数据库中的数据
- PHP 可以限制用户访问您的网站上的一些页面
- PHP 可以加密数据
- 通过 PHP，您不再限于输出 HTML。您可以输出图像、PDF 文件，甚至 Flash 电影。您还可以输出任意的文本，比如 XHTML 和 XML。

为什么使用
- PHP 可在不同的平台上运行（Windows、Linux、Unix、Mac OS X 等）
- PHP 与目前几乎所有的正在被使用的服务器相兼容（Apache、IIS 等）
- PHP 提供了广泛的数据库支持
- PHP 是免费的，可从官方的 PHP 资源下载它： www.php.net
- PHP 易于学习，并可高效地运行在服务器端

### mysql

MySQL 是一个关系型数据库管理系统

简单操作：

增
INSERT INTO 表名（字段名1，字段名2，…）VALUES（值1，值2，…）

删
DELETE FROM 表名 [WHERE 条件表达式]

改
UPDATE 表名 SET 字段名1=值1，[ ，字段名2=值2，…] [ WHERE 条件表达式 ]

查
SELECT * FROM 表名 [where 条件表达式]


### webpack 与 gulp 

区别：

Gulp是任务运行工具
webpack 是基于配置实现的构建工具

使用这两种工具，可以处理几乎每种类型的工作流。 在可用性方面，Gulp是获胜者：更容易定义和执行您的任务。Webpack的配置选项更加灵活，开发速度非常快，每天都有一个社区规模扩大。


### 小程序

- 常用 API
    wx.request https网络请求
    缓存：wx.setStorage、wx.getStorage、wx.removeStorage、wx.clearStorage
    wx.showToast 显示、隐藏消息提示框
    wx.setNavigationBarTitle动态设置当前页面的标题
    wx.getUserInfo 获取用户信息，需要先调用wx.login 接口
    wx.getSystemInfo获取系统信息（异步接口）
    wx.makePhoneCall 拨打电话
    wx.getLocation 获取当前的地理位置、速度
    wx.scanCode 调起客户端扫码界面进行扫码


### 混合开发

1、混合开发概述

Hybrid App主要以JS+Native两者相互调用为主，从开发层面实现“一次开发，多处运行”的机制，成为真正适合跨平台的开发。Hybrid App兼具了Native App良好用户体验的优势，也兼具了Web App使用HTML5跨平台开发低成本的优势。

目前已经有众多Hybrid App开发成功应用，比如美团、爱奇艺、微信等知名移动应用，都是采用Hybrid App开发模式。

2、移动应用开发的三种方式比较

移动应用开发的方式，目前主要有三种：

Native App： 本地应用程序（原生App）
Web App：网页应用程序（移动web）
Hybrid App：混合应用程序（混合App

详细：https://www.cnblogs.com/yuanyingke/p/6060150.html