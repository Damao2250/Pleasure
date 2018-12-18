## 1
```js
const obj1 = { x: 1 }
const obj2 = { y: 2 }

const obj3 = {
 ...obj1,
 ...obj2
}

obj3 = { x: 1, y: 2 }

//把其他对象合并到 obj3 里
```