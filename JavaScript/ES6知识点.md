##　ES6 箭头函数 return 用法
+ 如果代码块部分多于一条语句 就必须使用{}和return
```js
const test1 = (a,b) => {
  a+b
}
test1(1,2) // undefined

const test2 = (a,b) => {
  return a+b
}
test1(1,2) // 3
```
+ 如果只有一行语句块，可以省略{}和return
```js
const test3 = (a,b) => a+b
test3(1,2) // 3
```