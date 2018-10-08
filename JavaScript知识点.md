## 基础语法
***
#### 1.输出方式
```js
    window.alert('popup');//弹出警告框，window可以省略
    document.write();//将内容写到HTML文档（如HTML已加载则会被覆盖）
    document.getElementById('test').innerHTML() = "Then is the test.";//将内容写入html元素
    console.log('debug');//在控制台输出，常用于调试
```
#### 2.数据类型
* 值类型
    + Number (数字)
        - NaN (Not a Number)
            - 非数值，进行数学运算无法得到数字时返回NaN
            - 不代表也不等于任何值，本身也不等于本身
            - 任何数据与它运算都会得到NaN
    + Strting (字符串)
    + Boolean (布尔)
        - true      -> 是/真/成立/1
        - false     -> 否/假/不成立/0
* 引用数据类型
    + Object (对象)
        - Array (数组)
* 特殊类型
    + Undefined (声明但不赋值)
    + Null
#### 3.运算
* 运算符
    + +(加)、-(减)、*(乘)、/(除)、%(取余)
* 赋值运算
    + = 赋值
    + += 在原来基础追加
    + -=
    + *= /= %=

    ```js
    var num = 10;//把10赋值给num

    var str = 'a';
    str += 'b';//结果 'ab'

    var num1 = 10;
    num1 -= 2;//结果 8
    ```

* 关系运算
    + 等于：==,===
        - == 类型不一样时会进行隐式转换
        - === 要求值和类型全等
    + 大于: >,>=
    + 小于: <,<=
    + 不等: !=,!==
    > 运算规则

        数字和数字比较，直接比较大小
        数字和字符串比较，字符串转为数字后比较
        字符串和字符串比较，则是进行ASCII码进行比较

* 逻辑运算
    + && 逻辑与
    + || 逻辑或
    + ! 逻辑非

* 一元运算
    + ++ 自增1
    + -- 自减1
        - 前置 （返回值是加或减后的值）
            ```js
                var num = 10;
                ++num;//结果 11
            ```
        - 后置 （返回值是没有加或减前的值）
             ```js
                var num = 10;
                num++;//结果 10
            ```

* 进制转换
    + 十进制转其他
    ```js
        var num = 10;
        num.toString(2);//转二进制
        num.toString(8);//转八进制
    ```
    + 其他转十进制
    ```js
        var num = '100';
        parseInt(num,2);//二进制转十进制
        parseInt(num,8);//八进制转十进制
        parseInt(num,16);//十六进制转十进制
    ```



## 语句
* 条件判断语句
    + if语句
    ```js
        //单分支
        if(条件){
            //返回true时执行
        }

        //双分支
        if(条件){
            //返回true时执行
        }else{
            //返回false时执行
        }

        //多分支
        if(条件1){
            //条件1返回true时执行
        }else if(条件2){
            //条件2返回false时执行
        }else{
            //以上条件都不满足时执行
        }
    ```
    + 三元运算
    ```js
        var a = 3;
        var b = 5;
        var sum = (a>b) ? (a-b) : (a+b);
        //如果a>b执行a-b 否则执行a+b
    ```
    + switch语句
    ```js
        switch(值) {
            case value1: //要求value1与值恒等
                //如果表达式的值恒等于value1，代码从这里开始执行
                break;
            case value2:
                //如果表达式的值恒等于value2，代码从这里开始执行
                break;
            case value3: 
                //如果表达式的值恒等于value3，代码从这里开始执行
                break;
            case value4: 
                //如果表达式的值恒等于value4，代码从这里开始执行
                break;
            default: 
                //如果以上条件都不成立，默认执行这里的代码
        }
        //switch比较值时是使用全等，不会进行类型转换
        //执行过程中遇到 break 就会跳出switch
    ```
* 循环语句
```js
    //while循环

    //变量初始化
    while(条件){
        //条件成立就会不断地执行这里的代码，直到条件不成立
        //所以这里一般会伴随着条件的更新
    }
```
```js
    //do…while循环
    
    //变量初始化
    do {
        //不管条件是否成立，先执行一次这里的代码，再进行条件判断，如果条件依然成立，则再次执行这里的代码，依此类推
        //所以这里一般会伴随着条件的更新
    } while(条件)
```
```js
    //for循环

    for(变量初始化; 条件判断; 变量更新){
        //循环条件成立，则执行这里的代码
    }
    //例如
    var n = 0
    for(var i = 0; i < 10; i++){
        n++;
    }
    //结果 n=10
```
> ps:  
 break：//退出当前整个循环(多层循环嵌套中，一个break语句只向外跳一层)  
continue：//跳过本次循环，继续下一次循环
+ 嵌套循环
```js
    for(var i=0;i<10;i++){
        for(var j=0;j<10;j++){
            console.log(i,j);
        }
    }
```

## 函数
* 函数定义方式
    + 声明式
    + 赋值式
    + 构造函数

* 分类
    + 匿名函数
    + 具名函数

* 调用方式
    + 手动
    + 事件驱动

* 参数
    + 形参
    + 实参
    + arguments

* 作用域
    + 全局所用域
    + 局部作用域
    + 变量访问规则

* 返回值
    + return
    + 默认返回值 undefined


* this
    + 当前对象
    + 谁调用函数，谁就是this

* 递归
    + 避免死循环
    + 退出条件

## 数组
* 创建
    + 字面量
    + 构造函数
* 操作
    + 引索
    + 读取
    + 写入
    + 遍历
* 属性与方法
    + length
    + 方法
        - push()
        - unshift()
        - shift()
        - pop()
        - splice()  ->添加、删除、替换
        - slice(start,[end])
        - join()
        - sort()
        - reverse()

* 排序
    + 冒泡排序
    + 选择排序
    + 快速排序
* 数据类型
    + 堆栈
    + 基本数据类型（值类型）
        - Number
        - String
        - Boolean
    + 引用数据类型
        - Object
        - Array
        - Function
    + 数据类型的传递
* 二维数组 & 多维数组

* 对象
    + 创建
        - 字面量
        - 构造函数
    + 操作
        - 读取
        - 添加
        - 遍历（for...in）

## String

## Date

## Math

## BOM

## DOM

## 事件

## Cookie

## RegExp(正则)

## ES5

## ES6

## OOP（面向对象思想）

## Closure$Inherit(原型对象)





