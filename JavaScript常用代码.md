* 获取函数的参数&&参数个数
```js
function argument (){
    //获取参数（Array）
    console.log(arguments)
    //参数长度
    console.log(arguments.length)
}
argument (1,3,5,7,9)
```

* 简单递归解析
```js
function num(n){
    if(n<=0){
        return
    }
    n--;
    num(n);
    console.log(n)
}
num(5)
//输出 0、1、2、3、4

//解析 (等函数完全执行完才会输出)
num(5)
    num(4)  //1.等num(3)执行完才会输出4     //9.num(3)执行完输出4
        num(3)  //2.等num(2)执行完才会输出3     //8.num(2)执行完输出3
            num(2)  //3.等num(1)执行完才会输出2     //7.num(1)执行完输出2
                num(1)  //4.等num(0)执行完才会输出1     //6.num(0)执行完输出1
                    num(0)  //5.num(0)执行完成输出0
                    console.log(0)
                console.log(1)
            console.log(2)
        console.log(3)
    console.log(4)

```
```js
//递归计算5的阶乘
function factorial(n){
    if(n<=1){
        return 1
    }
    return n*factorial(n-1)
}
factorial(5)

```

```js
// 使用reduce方法将数组转换为对象
// reduce操作数组：arr.reduce(callback,[initialValue]),第一个参数回调函数，第二个初始值

['a','b','c'].reduce((acc,current)=>{
    acc[current] = current
    return acc
},{})

```

* 日期时间格式化
```js
/**
 * 日期时间格式化
 * @param {*} fmt 格式
 * @param {*} date 
 * 用法：
 * let date = new Date()
 * dateFormat("YYYY-mm-dd HH:MM:SS", date)
 */
export const dateFormat = (fmt, date) => {
  let ret;
  const opt = {
      "Y+": date.getFullYear().toString(),        // 年
      "m+": (date.getMonth() + 1).toString(),     // 月
      "d+": date.getDate().toString(),            // 日
      "H+": date.getHours().toString(),           // 时
      "M+": date.getMinutes().toString(),         // 分
      "S+": date.getSeconds().toString()          // 秒
      // 有其他格式化字符需求可以继续添加，必须转化成字符串
  };
  for (let k in opt) {
      ret = new RegExp("(" + k + ")").exec(fmt);
      if (ret) {
          fmt = fmt.replace(ret[1], (ret[1].length == 1) ? (opt[k]) : (opt[k].padStart(ret[1].length, "0")))
      };
  };
  return fmt;
}
```

* 获取今天是周几
```js
export const weekDay = () => {
    return "星期" + "日一二三四五六".charAt(new Date().getDay());
}

```

* 高阶函数 - after
```js
//after  意思是执行一定次数后执行一个方法,例如下边函数  执行count次后再执行fn函数

    function after(count,fn){
        return ()=>{
            //这里说说 count--  和 --count   很好解释  减号在前边就会立刻执行减一操作  在后边 下次才会执行
            if(--count === 0){
                fn()
            }
        }
    }
    function callBack(){
        console.log("两次以后执行结果")
    }

    let countAfter = after(2,callBack)

    countAfter()
    countAfter()  //执行两次以后执行结果

//    *实现解析  利用闭包的原理 存储count数  每执行一次做一次减减* 完成条件执行函数


// 理解
function after(count,fn){
  var num = count
  function decrease(){
    if(--num === 0){
      fn()
    }
  }
  return decrease
}

function callBack(){
  console.log("两次以后执行结果")
}

let countAfter = after(2,callBack)

countAfter()
countAfter()  //执行两次以后执行结果js


```
