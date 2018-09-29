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
*

## 函数

## 数组

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





