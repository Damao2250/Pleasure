###  Vue 实例生命周期（8个阶段）

生命周期函数：在对应时刻被自执行的函数，this指向实例，

```js
//所有的生命周期钩子自动绑定 this 上下文到实例中，因此你可以访问数据，对属性和方法进行运算。这意味着你不能使用箭头函数来定义一个生命周期方法

//beforeCreate（创建前）
//在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前被调用

// created（创建后）（应用loading）
// beforeMount(挂载前)
// mounted（挂载后）（应用Ajax、结束loading）
// beforeUpdate（更新前）
// updated（更新后）
// beforeDestroy（销毁前）
// destroyed（销毁后）（执行destory()后，不会改变已生成的DOM节点，后续页不受vue控制）

//两个特殊的（使用keep-alive）：activated、deactivated

//v2.5.0+新增： errorCaptured

```


|vue 1.0+       | vue 2.0       |  description
|:-------------:|:-------------:|:-------------|
|init           |befortCreate   |组件实例刚被创建，组件属性计算之前，如data属性等
|created        |created        |组件实例创建完成，属性已绑定，但DOM还未生成，`$el` 属性还不存在
|beforeCompile  |befortMount    |模板编译/过载前
|compiled       |mounted        |模板编译/过载后
|ready          |mounted        |模板编译/过载后（不保证组件已存在 document 中）
|-              |beforeUpdate   |组件更新前
|-              |update         |组件更新后
|-              |activated      |for `keep-alive` ,组件被激活时调用
|-              |deactivated    |for `keep-alive` ,组件被移除时调用
|attached       |-              |(已弃用)
|detached       |-              |(已弃用)
|beforeDestory  |beforeDestory  |组件销毁前调用
|destory        |destory        |组件销毁后调用


### 路由生命周期

```js
// beforeRouterEnter
// beforeRouterUpdate
// beforeRouteLeave

//路由守卫
//全局&路由独享：beforeEach、beforeResolve（v2.5.0+新增）、afterEach ；//beforeEnter（路由独享，类似beforeEach）
//组件内：beforeRouteEnter、beforeRouteUpdate (2.2 新增)、beforeRouteLeave

```

函数提升 变量提升

jq常用api

倒序 ：
msg:hello world

msg.split('').reverse().join('')

