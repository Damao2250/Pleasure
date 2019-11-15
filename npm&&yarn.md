## npm

```js
// 全局安装
npm i xxx -g

// 初始化新项目
npm init [项目名称]

// 安装一个包
npm i [package]
npm install [package]
npm install [package]@[version]

// 升级/更新依赖包
npm update [package]

// 查看过期包
npm outdated [package]

// 查看包版本
npm ls [package]
npm list [package]


// 查看安装信息
npm list
npm list -g

// 删除依赖
npm uninstall [package]

// 安装全部依赖
npm i

```




## yarn 
```js
// 全局安装
yarn global add xxx

// 初始化新项目
yarn init

// 添加依赖包
yarn add [package]
yarn add [package]@[version]
yarn add [package]@[tag]

// 升级依赖包
yarn upgrade [package]
yarn upgrade [package]@[version]
yarn upgrade [package]@[tag]

// 将依赖添加到不同依赖类别
yarn add [package] --dev          // devDependencies
yarn add [package] --peer         // peerDependencies
yarn add [package] --optional     // optionalDependencies

// 移除依赖包
yran remove [package]

// 安装全部依赖
yarn
or
yarn install


```