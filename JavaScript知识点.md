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
* 创建
    + 字面量
    + 构造函数
* 操作
    + 属性 length
    + 方法
        - 读取
            + charAt(idx)
            + 方括号[idx]
        - 查找&替换
            + indexOf()/lastIndexOf()
            + search()
            + match()
            + replace()
        - 截取
            + substring(start,[end])
            + slice(start,[end])
            + substr(start,[len])
        - 拆分
            + split(分隔符)
        - 大小写
            + toLowerCase()
            + toUpperCase()
    + 正则表达式
        - 创建
            + 字面量
            + 构造函数
        - 参数
            + i:忽略大小写
            + g:全局匹配
    + 编码
        - charCodeAt()
        - Staring.fromCharCode()
        - 分类
            + ASCII
            + Unicode
            + utf-8
## json字符串
* 格式要求
    + 属性名双引号
    + 值类型
        - Number
        - String （必须使用双引号）
        - Boolean
        - Objcet
        - Array
        - Null
    + 不能有注释
    + 不能有多余的逗号
* 操作
    + JSON
        - stringify(object/array)
        - parse(json)

## Date

## Math
* 属性
    + PI
* 方法
    + 取整
        - Math.round()
        - Math.cell()
        - Math.floor()
    + Math.max()
    + Math.min()
    + Math.abs()
    + Math.pow(x,y)
    + Math.sqrt()
    + Math.random()
    + 三角函数
        - Math.sin()
        - Math.cos()
        - Math.tan()
        - 弧度
## BOM
* 全局作用域
    - 全局作用域下声明的变量会成为window的属性
    - 避免全局环境的污染
* window对象
    - 属性
        - innerWidth
        - innerHeight
        - outerWidth
        - outerHeight
        - scrollX/scorllY
    - 方法
        - 滚动相关
            + scrollTop(x,y)
            + scrollBy(ox,oy)
        - 系统弹窗
            + alert()
            + confirm()
            + prompt()
            + open(url,name,options)
            + close()
            + print()
        - 数据类型
            + String()
            + Number()
            + Boolean()
            + Array()
            + Object()
            + Function()
            + Date()
            + Undefined
            + Null
        - 其他
            + parseInt()
            + parseFloat()
            + isNaN()
    + 事件
        - onlond
        - onresize
        - onscroll
        - onbeforeunload
    + 属性对象
        - Math
        - console    log()
        - location
            + href
            + search
            + has
            + reload()
        - history
            + length
            + back()
            + forward()
            + go()
        - document

## DOM
* 节点
    + 分类
        - 元素节点(1)
        - 文本节点(3)
        - 属性节点(2)
    + 属性
        - nodeType
        - nodeName
        - nodeValue
* 获取元素节点方式
    + document.getElementById()
    + document.getElementByTagName()
    + document.getElementByClassName()
    + document.getElementByName()
* 节点关系
    + 父节点
        - parentNode == parentElement
    + 子节点
        - childNodes == children
        - firstChild == firstElementChild
        - lastChild = lastElementChild
    + 兄弟节点
        - previousSibling == previousElementSibling
        - nextSibling == nextElementSlbling
    + 节点操作
        - 创建
            - document.createElement()
            - document.createTextNode()
        - 插入
            - parent.appengChild(ele)
            - parent.insertBefore(newEle,node)
        - 删除
            - parent.removeChild(ele)
        - 复制
            - ele.cloneNode()
        - 改
            - DOM属性
                - innerHTML
                - innerText
                - outerHTML
                - outerText
                - style:内联样式
                - className
                - id
            - html属性
                - setAttribute(attr,val)
                - getAttribute(attr)
                - removeAttribute(attr)
                - hasAttribute(attr)
    + 盒模型属性
        - offsetWidth
        - offsetHeight
        - offsetLeft
        - offsetTop
    + 获取css样式
        - getComputedStyle(ele,[p])
        - ele.currentStyle

## 事件
* 事件绑定方式
    + html属性
    + DOM节点绑定
    + 事件监听
        - addEventListener(type,fn,capture)
        - IE8:arrachEvent(type,fn)
* 事件分类
    + 鼠标事件
        - onclick
        - ondblclick
        - onmousedown
        - onmouseup
        - onmousemove
        - onmouseout
        - onmouseover
        - onmouseleave
        - onmouseenter
        - oncontextmenu
    + 键盘事件
        - onkeydown
        - onkeyup
        - onkeypress
    + 表单
        - onchange
    + 其他
        - onload
        - onresize
        - onscroll
* 事件传播
    + DOM树
    + 冒泡：事件委托
    + 捕获：事件监听
* 浏览器默认行为
    + 链接跳转
    + 右键菜单
    + 表单提交
* Event
    + 获取方式
        - 标准：事件处理函数的第一个参数
        - IE8: window.event
    + 属性
        - 鼠标
            - button
                - 0:左键
                - 1:滚轮
                - 2:右键
            - 光标位置
                - clinentX/clinentY
                - pageX/pageY
                - screenX/screenY
                - offsetX/offsetY
            - 键盘
                - keyCode/which
                    - 37,38,39,40:方向键
                    - 13:回车,27:ESC,32:空格
                - altKey
                - shiftKey
                - ctrlKey
            - 事件源对象
                - target
                - srcElement
        + 方法
            - 阻止默认行为
                - 标准: preventDefault()
                - IE8: returnValue=false
            - 停止事件传播
                - 标准: stopPrepagation()
                - IE8: cancelBubble=true

## Cookie
* 协议
    + 网络协议：ip
    + 通信协议：TCP、UDP、http/https
* 操作
    + 读取
        - document.cookie
        - 读取本域名下所有可访问的cookie
    + 写入
        - document.cookie='name=value'
        - 一次写入一个，只能写入字符串
    + 参数
        - expires
        - path
        - domain
        - secure
* 限制
    - 只能访问本域名下的cookie
    - 只能访问当前路径下cookie
    - 数量<=50;大小<=2M


## RegExp(正则)
* 创建
    + 字面量：/cdf/
    + 构造函数：new RegExp('cdf')
    + 参数
        - i:忽略大小写
        - g:全部匹配
        - m:多行匹配
    + 语法
        - 字符类
            - \d:数字   \D:非数字
            - \w:数字字母下划线     \W:非数字字母下划线
            - \s:空格   \S:非空格
            - \b:单词边界   \B:非单词边界
            - .:除换行符以外的所有字符
        - 数量词
            - {n}:匹配n个字符
            - {2,5}:匹配2-5个字符
            - {1,}:匹配一个或一个以上字符 <=> +
            - *:匹配0个或0个以上字符 <=> {0,}
            - ?:匹配0个或1个字符 <=> {0,1}
        - 特殊字符
            - ():分组
                - $1-$9
                - \1-\9
            - []:表示一个字符，里面的字符为或的关系
            - |:或
        - 锚点定位
            - ^:开始
            - $:结束
        - 模式
            - 贪婪模式（默认）: 尽可能多匹配
            - 非贪婪模式
                - 尽可能少匹配
                - 在数量词后加?
    + 方法
        - 正则方法
            - test()
            - exec()
        - 支持正则表达式的方法
            - match()
            - search()
            - replace()
            - split()

## ES5
* 模式
    + 正常模式
    + 严格模式 'use strict'(全局、局部)
* 兼容性：IE9 
* 数组扩展
* document加载事件
    + onreadystatechange
        - document.readyState
            - interactive
            - complete
    + DOMContentLoaded
        - 必须使用事件监听器绑定事件
* 获取页面元素
    + querySelector(css selector)
    + querySelectorAll(css selector)
* 函数扩展
    + bind():改变函数的this指向
* 类名操作 classList
    + length:类名长度
    + add():添加类名
    + remove():删除类名
    + toggle():切换类名
    + contains():判断是否存在某个类名
* 自定义属性操作 dataset
    + 返回一个包含所有自定义属性（键值）的对象
    + data-XXX  (符合w3c标准)
    

## ES6

## OOP（面向对象思想）

## Closure$Inherit(原型对象)





