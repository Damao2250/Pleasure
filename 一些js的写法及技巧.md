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

## 7. ES5 实现数组 some 方法

```js
const selfSome = function(fn,context){
  let arr = Array.prototype.slice.call(this)

  if(!arr.length) return false
  let flag = false
  for(let i = 0; i < arr.length; i++){
    if(!arr.hasOwnProperty(i)) continue
    let res = fn.call(context, arr[i],i,this)
    if(res){
      flag = true
      break
    }
  }
  return flag
}

// 执行 some 方法的数组如果是一个空数组，最终始终会返回 false，而另一个数组的 every 方法中的数组如果是一个空数组，会始终返回 true
```

## 8.console.log()方法中%s的作用

```js
一、console.log("log信息");

二、console.log("%s","first","second");

输出结果:first second

三.将对象转换为普通字符串后执行
console.log("%s","guoyansi",{name:"思思博士"});
//输出结果:guoyansi { name: '思思博士' }

四、

//将字符串作为数值进行转换
console.log("%d","25.6");
//输出结果:25.6
console.log("%d","guoyansi");
//输出结果:guoyansi

五  输出%
console.log("%%");
//输出结果:%
console.log("%%","gys");
//输出结果:% gys

六 将console.error信息输出到文件中去
//页面代码:
console.error("guoyansi is error");
//利用node app.js 2>err.txt启动这个页面
//会在同级目录下多一个err.txt文件.文件里面还有"guoyansi is error"

 

七 直接在命令行启动一个并不存在的文件javascript.js,这样:
// node javascript.js 2>info.txt
//输出结果:会在命令行所在的目录下多出一个文件info.txt;
//info.txt文件中的内容如下

/*
 module.js:340
 throw err;
 ^
 Error: Cannot find module 'E:\node\gys\javascript.js'
 at Function.Module._resolveFilename (module.js:338:15)
 at Function.Module._load (module.js:280:25)
 at Function.Module.runMain (module.js:497:10)
 at startup (node.js:119:16)
 at node.js:906:3
 */
```


1. 类型强制转换

1.1 string强制转换为数字

可以用 *1来转化为数字(实际上是调用 .valueOf方法)
然后使用 Number.isNaN来判断是否为 NaN，或者使用 a!==a 来判断是否为 NaN，因为 NaN!==NaN
```js
"2333" * 1          // 2333
"test" * 1        // NaN 
null * 1          // 0
undefined * 1     // NaN
1 * { vulueOf: ()=> "3" } // 3

// 使用 + 也是同等效果
+ "2333"          // 2333
+ "test"        // NaN 
+ null          // 0
+ undefined     // NaN
+ { vulueOf: ()=> "3" } // 3
```
