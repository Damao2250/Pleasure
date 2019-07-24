## lement input第一次回车刷新页面问题
```js
// 在input中加上键盘回车事件@keyup.enter.native，如下：

<el-form ref="form"  :model="form">
  <el-input v-model="form.keyword"  placeholder="筛选关键词" @keyup.enter.native="search"></el-input>
</el-form>

// 原因如下：
// form内只有一个输入框时,按回车会自动提交

// 解决办法：
// 阻止form的默认事件。
// 即在form上加上这句话：@submit.native.prevent
<el-form ref="form"  :model="form" @submit.native.prevent>
  <el-input v-model="form.keyword"  placeholder="筛选关键词" @keyup.enter.native="search"></el-input>
</el-form>

```