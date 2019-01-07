## vue父子组件间通信之 props 、$ref 、$emit  
+ prop 静态传递
```html
<!-- 父组件 -->
<template>
  <div>
    <h1>我是父组件！</h1>
    <child message="我是子组件一！"></child>  //通过自定义属性传递数据
  </div>
</template>
<script>
import Child from '../components/child.vue'
export default {
  components: {Child},
}
</script>

 <!-- 子组件 -->
<template>
  <h3>{{message}}</h3>
</template>
<script>
  export default {
    props: ['message']   //声明一个自定义的属性
  }
</script>
```

+ prop 动态传递
```html
<!-- 父组件 -->

<template>
  <div>
    <h1>我是父组件！</h1>
    <child message="我是子组件一！"></child> 

    <!-- 这是一个 JavaScript 表达式而不是一个字符串。-->
    <child v-bind:message="a+b"></child>

    <!-- 用一个变量进行动态赋值。-->
    <child v-bind:message="msg"></child>
  </div>
</template>
<script>
import Child from '../components/child.vue'
export default {
  components: {Child},
  data() {
    return {
      a:'我是子组件二！',
      b:112233,
      msg: '我是子组件三！'+ Math.random()
    }
  }
}
</script>

 <!-- 子组件 -->
<template>
  <h3>{{message}}</h3>
</template>
<script>
  export default {
    props: ['message']
  }
</script>
```

+ 通过$ref 实现通信
  如果ref用在子组件上，指向的是组件实例，可以理解为对子组件的索引，通过$ref可能获取到在子组件里定义的属性和方法。
  如果ref在普通的 DOM 元素上使用，引用指向的就是 DOM 元素，通过$ref可能获取到该DOM 的属性集合，轻松访问到DOM元素，作用与JQ选择器类似。
```html
<!-- 父组件 -->
<template>
  <div>
    <h1>我是父组件！</h1>
    <child ref="msg"></child>
  </div>
</template>
<script>
  import Child from '../components/child.vue'
  export default {
    components: {Child},
    mounted: function () {
      console.log( this.$refs.msg);
      this.$refs.msg.getMessage('我是子组件一！')
    }
  }
</script>

<!-- 子组件 -->
<template>
  <h3>{{message}}</h3>
</template>
<script>
  export default {
    data(){
      return{
        message:''
      }
    },
    methods:{
      getMessage(m){
        this.message=m;
      }
    }
  }
</script>
```
+ 通过$emit 实现通信
  vm.$emit( event, arg )
  $emit 绑定一个自定义事件event，当这个这个语句被执行到的时候，就会将参数arg传递给父组件，父组件通过@event监听并接收参数。
```html
<!-- 父组件 -->

<template>
  <div>
    <h1>{{title}}</h1>
    <child @getMessage="showMsg"></child>
  </div>
</template>

<script>
  import Child from '../components/child.vue'
  export default {
    components: {Child},
    data(){
      return{
        title:''
      }
    },
    methods:{
      showMsg(title){
       this.title=title;
      }
  }
  }
</script>

<!-- 子组件 -->
<template>
  <h3>我是子组件！</h3>
</template>
<script>
  export default {
    mounted: function () {
      this.$emit('getMessage', '我是父组件！')
    }
  }
</script>
```