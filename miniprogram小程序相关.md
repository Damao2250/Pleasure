### 分包机制

1. 首次启动时，先下载小程序主包，显示主包内的页面；

2. 如果用户进入了某个分包的页面，再下载这个对应分包，下载完毕后，显示分包的页面。

3. 采用分包加载，对开发者而言，能使小程序有更大的代码体积，承载更多的功能与服务；而对用户而言，可以更快地打开小程序，同时在不影响启动速度前提下使用更多功能。

### 遇到的问题

1. mpvue构建出来的小程序项目，使用微信开发工具打开时报错：
    “未找到入口 app.json 文件，或者文件读取失败，请检查后重新编译。”
    解决：找到项目根目录下的 project.config.json 文件 将 "miniprogramRoot": "dist"改为 "miniprogramRoot": "dist/wx"


### mpvue使用步骤

```js
    // 全局安装 vue-cli
    npm install --global vue-cli
    // 创建一个基于 mpvue-quickstart 模板的新项目
    vue init mpvue/mpvue-quickstart my-project

    // 安装依赖
    cd my-project
    npm install
    // 启动构建
    npm run dev

    // 保留了 vue.runtime 核心方法，无缝继承了 Vue.js 的基础能力
    //mpvue-template-compiler 提供了将 vue 的模板语法转换到小程序的 wxml 语法的能力
    //修改了 vue 的建构配置，使之构建出符合小程序项目结构的代码格式： json/wxml/wxss/js 文件
```