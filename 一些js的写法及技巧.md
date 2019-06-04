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

## 2.判断对象的数据类型

```js
const isType = type => target => `[object ${type}]` === Object.prototype.toString.call(target)
const isArray = isType('Array')
const isObject = isType('Object')
console.log(isArray([]))  // true
console.log(isArray({}))  // false
console.log(isObject({})) // true
console.log(isObject([])) // false

// 使用 Object.prototype.toString 配合闭包，通过传入不同的判断类型来返回不同的判断函数，一行代码，简洁优雅灵活（注意传入 type 参数时首字母大写）

// 不推荐将这个函数用来检测可能会产生包装类型的基本数据类型上,因为 call 会将第一个参数进行装箱操作

```

## 3. ES5实现数组 map 方法

```js
const seltMap = function(fn, context){
  let arr = Array.prototype.slice.call(this)
  let mappedArr = []
  for(let i = 0; i < arr.length; i++){
    if(!arr.hasOwnProperty(i)) continue
    mappedArr.push(fn.call(context,arr[i],i,this))
  }
  return mappedArr
}

// 值得一提的是，map 的第二个参数为第一个参数回调中的 this 指向，如果第一个参数为箭头函数，那设置第二个 this 会因为箭头函数的词法绑定而失效

// 另外就是对稀疏数组的处理，通过 hasOwnProperty 来判断当前下标的元素是否存在与数组中

```

## 4. 使用 reduce 实现数组 map 方法

```js
const selfMap2 = function(fn,context){
  let arr = Array.prototype.slice.call(this)
  return arr.reduce((pre,cur,index)=>{
    return [...pre,fn.call(context,cur,index,this)]
  },[])
}
```
## 5. ES5 实现数组 filter 方法

```js
const selfFilter = function(fn,context){
  let arr = Array.prototype.slice.call(this)
  let filteredArr = []
  for(let i = 0; i < arr.length; i++){
    if(!arr.hasOwnProperty(i)) continue
    fn.call(context,arr[i],this) && filteredArr.push(arr[i])
  }
  return filteredArr
}
```

## 6. 使用 reduce 实现 filter

```js
const selfFilter2 = function(fn,context){
  return this.reduce((pre,cur,index)=>{
    return fn.call(context,cur,index,this) ? [...pre, cur] : [...pre]
  },[])
}
```
