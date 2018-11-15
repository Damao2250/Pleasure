###  Vue 实例生命周期（8个阶段）

```js
//所有的生命周期钩子自动绑定 this 上下文到实例中，因此你可以访问数据，对属性和方法进行运算。这意味着你不能使用箭头函数来定义一个生命周期方法

beforeCreate（创建前）
//在实例初始化之后，数据观测 (data observer) 和 event/watcher 事件配置之前被调用

// created（创建后）
// beforeMount(挂载前)
// mounted（挂载后）
// beforeUpdate（更新前）
// updated（更新后）
// beforeDestroy（销毁前）
// destroyed（销毁后）

//两个特殊的（使用keep-alive）：activated、deactivated

//v2.5.0+新增： errorCaptured

```


### 路由生命周期

```js
// beforeRouterEnter
// beforeRouterUpdate
// beforeRouteLeave

//路由守卫
//全局&路由独享：beforeEach、beforeResolve（v2.5.0+新增）、afterEach ；//beforeEnter（路由独享，类似beforeEach）
//组件内：beforeRouteEnter、beforeRouteUpdate (2.2 新增)、beforeRouteLeave

```