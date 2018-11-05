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