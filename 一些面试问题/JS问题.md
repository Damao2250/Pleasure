```js
var fn = function(){
  var count =1
  console.log(count);
}
var uniq = function(){
  var count = 2
  console.log(count);
}
fn() || uniq()
// 1  2

// 逻辑或 ||
// fn() 没有return值，函数默认值为 undefined
// undefined || uniq()    所以会执行两次
```

