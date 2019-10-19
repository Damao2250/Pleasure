## css书写顺序
```js
  // 1.位置属性(position, top, right, z-index, display, float等)
  // 2.大小(width, height, padding, margin)
  // 3.文字系列(font, line-height, letter-spacing, color- text-align等)
  // 4.背景(background, border等)
  // 5.其他(animation, transition等)
```

## vue 引入背景
```html
<style>
  .bg{
    background: url("~@/assets/img/login-bg.png") center center no-repeat;
    background: rgba($color: #608cc7, $alpha: 0.3);
  }
</style>

```
控制台
document.designMode="on"
可以编写页面
