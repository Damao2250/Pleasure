+ 一个页面从输入 URL 到页面加载完的过程

    1、浏览器的地址栏输入URL并按下回车。

　　2、浏览器查找当前URL是否存在缓存，并比较缓存是否过期。

　　3、DNS解析URL对应的IP。

　　4、根据IP建立TCP连接 -> 浏览器向服务器发起tcp连接，与浏览器建立tcp三次握手

　　5、握手成功后，浏览器向服务器发送http请求，请求数据包。

　　6、服务器处理请求，浏览器接收HTTP响应。

　　7、浏览器解析html源码 ，构建DOM树，渲染页面。

　　8、关闭TCP连接（四次挥手）。


    三次握手：A去B家，A敲门说“我是A，你在家吗”，B确认是A后说“我在家，你进来吧”，A确认B在家后说“好的，我进去了”

    四次挥手：A和B打电话，通话即将结束后，A说“我没啥要说的了”，B回答“我知道了”，但是B可能还会有要说的话，A不能要求B跟着自己的节奏结束通话，于是B可能又巴拉巴拉说了一通，最后B说“我说完了”，A回答“知道了”，这样通话才算结束。

[参考](https://www.cnblogs.com/daijinxue/p/6640153.html)



+ 常见端口号

    FTP：20 21

    SSH：22

    TELNET：23

    DNS：53

    HTTP：80
    
    HTTPS：443

    MYSQL：3306


+ 同源策略


+ 跨域







# 项目相关
1. 
+ 做过最满意的项目是什么？
+ 项目背景
    - 为什么要做这件事情？
    - 最终达到什么效果？
+ 你处于什么样的角色，起到了什么方面的作用？
+ 在项目中遇到什么技术问题？具体是如何解决的？
+ 如果再做这个项目，你会在哪些方面进行改善？

# 技术相关
1. 技术面
+ 描述一个你遇到过的技术问题，你是如何解决的？
    - 这个问题很常见，有没有遇到过很不常见的问题？比如在网上根本搜不到解决方法的？
    - 是否有设计过通用的组件？
+ 请设计一个 Dialog（弹出层） / Suggestion（自动完成） / Slider（图片轮播） 等组件
    - 你会提供什么接口？
    - 调用过程是怎样的？可能会遇到什么细节问题？

2. 技术面
+ 你最擅长的技术是什么？
    - 你觉得你在这个技术上的水平到什么程度了？你觉得最高级别应该是怎样的？
+ 浏览器及性能
    - 一个页面从输入 URL 到页面加载完的过程中都发生了什么事情？越详细越好
        - （这个问既考察技术深度又考察技术广度，其实要答好是相当难的，注意越详细越好）
    - 谈一下你所知道的页面性能优化方法？
        - 这些优化方法背后的原理是什么？
        - 除了这些常规的，你还了解什么最新的方法么？
    - 如何分析页面性能？
+ 其它
    - 除了前端以外还了解什么其它技术么？
    - 对计算机基础的了解情况，比如常见数据结构、编译原理等


# 兴趣相关

+ 最近在学什么？接下来半年你打算学习什么？
+ 做什么方面的事情最让你有成就感？需求设计？规划？具体开发？
+ 后续想做什么？3 年后你希望自己是什么水平？


# 常见问题

+ 你昨天/本周学到了什么？
+ 你对编码有什么兴趣或兴趣？
+ 您最近遇到的技术挑战是什么？您是如何解决的？
+ 在构建新网站或维护网站时，您能解释一些用于提高性能的技术吗？
+ 你能描述一下你最近使用的一些SEO最佳实践或技巧吗？
+ 您能否解释一下前端安全方面遇到的常见技术或最新问题？
+ 您个人对最近的项目采取了哪些措施来提高代码的可维护性？
+ 谈谈您首选的开发环境。
+ 您熟悉哪种版本控制系统？
+ 您可以在创建网页时描述您的工作流程吗？
+ 如果你有5种不同的样式表，你最好如何将它们整合到网站中？
+ 你能描述渐进增强和优雅降级之间的区别吗？
+ 您如何优化网站的资产/资源？
+ 浏览器一次从给定域下载多少资源？
    - 有什么例外？
+ 列举3种减少页面加载（感知或实际加载时间）的方法。
+ 如果你跳过一个项目而他们使用了标签并且你使用了空格，你会怎么做？
+ 描述如何创建一个简单的幻灯片页面。
+ 如果你今年可以掌握一项技术，它会是什么？
+ 解释标准和标准机构的重要性。
+ 什么是无格式内容的Flash？你如何避免FOUC？
+ 解释ARIA和屏幕阅读器是什么，以及如何使网站可访问。
+ 解释CSS动画与JavaScript动画的一些优缺点。
+ CORS代表什么，它解决了什么问题？
+ 你是如何处理与老板或合作者的分歧的？
+ 您使用哪些资源来了解最新的前端开发和设计？

# HTML相关

+ 怎么doctype办？（What does a doctype do?）
+ 如何为包含多种语言内容的页面提供服务？
+ 在设计或开发多语言网站时，您必须警惕哪些事情？
+ 什么data-属性有益？（What are data- attributes good for?）
+ 将HTML5视为一个开放的Web平台。HTML5的构建块是什么？
+ 描述之间的差异cookie，sessionStorage以及localStorage。
+ 描述之间的差别`<script>`，`<script async>`并`<script defer>`。
+ 为什么将CSS放在和之前的JS `<link>`之间通常是一个好主意？你知道有什么例外吗？`<head></head><script></body>`
+ 什么是渐进式渲染？
+ 为什么要srcset在图像标记中使用属性？解释浏览器在评估此属性的内容时使用的过程。
+ 您以前使用过不同的HTML模板语言吗？

+ What does a doctype do?
+ How do you serve a page with content in multiple languages?
+ What kind of things must you be wary of when design or developing for multilingual sites?
+ What are data- attributes good for?
+ Consider HTML5 as an open web platform. What are the building blocks of HTML5?
+ Describe the difference between a cookie, sessionStorage and localStorage.
+ Describe the difference between `<script>`, `<script async>` and `<script defer>`.
+ Why is it generally a good idea to position CSS `<link>`s between `<head></head>` and JS `<script>`s just before `</body>`? Do you know any exceptions?
+ What is progressive rendering?
+ Why you would use a srcset attribute in an image tag? Explain the process the browser uses when evaluating the content of this attribute.
+ Have you used different HTML templating languages before?


# CSS相关

+ 什么是CSS选择器特异性以及它如何工作？
+ CSS的“重置”和“规范化”有什么区别？你会选择哪个，为什么？
描述Floats及其工作原理。
+ 描述z-index以及如何形成堆叠上下文。
+ 描述BFC（块格式化上下文）及其工作原理。
什么是各种清算技术，哪些适合哪种情况？
+ 您将如何解决特定于浏览器的样式问题？
如何为功能受限的浏览器提供页面服务？
    + 你使用什么技术/流程？
+ 可视隐藏内容的不同方法有哪些（并且仅供屏幕阅读器使用）？
+ 你有没有使用过网格系统，如果有的话，你更喜欢什么？
+ 您是否使用或实施了媒体查询或移动特定布局/ CSS？
你熟悉SVG的样式吗？
+ 你能举出一个@media除了以外的财产的例子screen吗？
编写高效CSS有哪些“陷阱”？
+ 使用CSS预处理器有哪些优点/缺点？
+ 描述您对所使用的CSS预处理器的喜好和不喜欢。
您将如何实现使用非标准字体的网页设计补偿？
+ 解释浏览器如何确定哪些元素与CSS选择器匹配。
    + 描述伪元素并讨论它们的用途。
+ 解释您对盒子模型的理解，以及如何告诉CSS中的浏览器在不同的盒子模型中渲染您的布局。
+ 怎么* { box-sizing: border-box; }办？它的优点是什么？
+ 什么是CSS display属性，你能举几个例子来说明它的用法吗？
+ 内联块和内联块有什么区别？
+ “nth-of-type（）”和“nth-child（）”选择器之间有什么区别？
+ 相对，固定，绝对和静态定位元素之间的区别是什么？
+ 您在本地或生产中使用了哪些现有的CSS框架？你会如何改变/改善它们？
+ 您是否使用过新的CSS Flexbox或Grid规格？
+ 您能否解释一下网站编码响应与使用移动优先策略之间的区别？
+ 你曾经使用过视网膜图形吗？如果是这样，你何时使用什么技术？
+ 你有什么理由想要使用translate()而不是绝对定位，反之亦然？为什么？

# JS相关

+ 解释事件授权
+ 解释如何this在JavaScript中工作
+ 解释原型继承是如何工作的
+ 您如何看待AMD与CommonJS？
+ 解释为什么以下不能用作IIFE : function foo(){ }();.
    + 需要改变哪些才能使其成为IIFE？
+ 什么是变量之间的区别在于：null，undefined或者未申报？
    + 你会如何检查这些状态？
+ 什么是闭合，以及如何/为什么要使用闭合？
+ 你能描述一个forEach循环和.map()循环之间的主要区别吗？为什么你要选择一个与另一个？
+ 匿名函数的典型用例是什么？
+ 你如何组织你的代码？（模块模式，经典继承？）
+ 主机对象和本机对象之间有什么区别？
+ 区别：function Person(){}，var person = Person()，和var person = new Person()？
+ .call和之间有什么区别.apply？
+ 解释一下Function.prototype.bind。
+ 功能检测，功能推断和使用UA字符串之间有什么区别？
+ 尽可能详细地解释Ajax。
+ 使用Ajax有哪些优缺点？
+ 解释JSONP如何工作（以及它是如何不是真正的Ajax）。
+ 你曾经使用过JavaScript模板吗？
    + 如果是这样，您使用了哪些库？
+ 解释“hoisting”。
+ 描述事件冒泡。
+ 描述事件捕获。
+ “属性”和“属性”之间有什么区别？
+ 为什么扩展内置JavaScript对象不是一个好主意？
+ 窗口加载事件和文档DOMContentLoaded事件之间的区别？
+ ==和之间有什么区别===？
+ 解释有关JavaScript的同源策略。
+ 做这个工作：
    + 重复（[ 1，2，3，4，5 ]）; // [1,2,3,4,5,1,2,3,4,5]
+ 为什么它被称为三元运算符，“三元”这个词是什么意思？
+ 是什么"use strict";？使用它有什么优点和缺点？
+ 创建一个迭代的for循环，100同时输出“fizz”的倍数3，“buzz”的倍数5和“fizzbuzz”的倍数3和5
+ 一般来说，为什么将网站的全球范围保持原样并且从不接触它是一个好主意？
+ 你为什么要用这样的东西load？这个事件有缺点吗？你知道任何替代方案，为什么要使用它们？
+ 解释单页应用程序是什么以及如何使一个SEO友好。
+ 您对Promise和/或其polyfills的体验程度如何？
+ 使用Promise而不是回调的优点和缺点是什么？
+ 在编译为JavaScript的语言中编写JavaScript代码有哪些优点/缺点？
+ 您使用哪些工具和技术来调试JavaScript代码？
+ 您使用什么语言结构来迭代对象属性和数组项？
+ 解释可变对象和不可变对象之间的区别。
    + JavaScript中不可变对象的示例是什么？
    + 不变性的利弊是什么？
    + 如何在自己的代码中实现不变性？
+ 解释同步和异步函数之间的区别。
+ 什么是事件循环？
    + 调用堆栈和任务队列有什么区别？
+ 解释上的使用的差异foo之间function foo() {}和var foo = function() {}
+ 什么是使用创建的变量之间的差异let，var还是const？
+ ES6类和ES5函数构造函数之间有什么区别？
+ 你能为新的箭头=>函数语法提供一个用例吗？这种新语法与其他函数有何不同？
+ 在构造函数中使用箭头语法有什么优势？
+ 高阶函数的定义是什么？
+ 你能给出一个解构对象或数组的例子吗？
+ ES6模板文字在生成字符串方面提供了很大的灵活性，你举个例子吗？
+ 你能举一个咖喱函数的例子，为什么这种语法有优势？
+ 使用有什么好处，spread syntax它有什么不同rest syntax？
+ 你如何在文件之间共享代码？
+ 为什么要创建静态类成员？

# 测试问题

+ 测试代码有哪些优点/缺点？
+ 您将使用哪些工具来测试代码的功能？
+ 单元测试和功能/集成测试有什么区别？
+ 代码样式linting工具的目的是什么？

# 性能问题

+ 您将使用哪些工具在代码中查找性能错误？
+ 您可以通过哪些方式改善网站的滚动性能？
+ 解释布局，绘画和合成之间的区别。

# 网络问题

+ 传统上，为什么从多个域提供站点资产更好？
+ 尽力描述从您输入网站的URL到完成屏幕加载的过程。
+ Long-Polling，Websockets和Server-Sent Events之间有什么区别？
+ 解释以下请求和响应标头：
    + DIFF。在Expires，Date，Age和If-Modified -...之间
    + 不跟踪
    + 缓存控制
    + 传输编码
    + ETag的
    + X-框架，选项
    + Diff. between Expires, Date, Age and If-Modified-...
    + Do Not Track
    + Cache-Control
    + Transfer-Encoding
    + ETag
    + X-Frame-Options
+ 什么是HTTP方法？列出您知道的所有HTTP方法，并解释它们。

# 代码相关

1. Question: What is the value of foo?（值是什么）
```js
var foo = 10 + '20';
```
2. Question: What will be the output of the code below?（结果是什么）
```js
console.log(0.1 + 0.2 == 0.3);
```
3. Question: How would you make this work?（如何实现）
```js
add(2, 5); // 7
add(2)(5); // 7
```
4. Question: What value is returned from the following statement?（以下语句返回什么值）
```js
"i'm a lasagna hog".split("").reverse().join("");
```
5. Question: What is the value of window.foo?（值是什么）
```js
( window.foo || ( window.foo = "bar" ) );
```
6. Question: What is the outcome of the two alerts below?（以下两个alert的结果是什么？）
```js
var foo = "Hello";
(function() {
  var bar = " World";
  alert(foo + bar);
})();
alert(foo + bar);
```
7. Question: What is the value of foo.length?(值是什么)
```js
var foo = [];
foo.push(1);
foo.push(2);
```
8. Question: What is the value of foo.x?(值是什么)
```js
var foo = {n: 1};
var bar = foo;
foo.x = foo = {n: 2};
```
9. Question: What does the following code print?(以下代码打印什么？)
```js
console.log('one');
setTimeout(function() {
  console.log('two');
}, 0);
Promise.resolve().then(function() {
  console.log('three');
})
console.log('four');
```
10. Question: What is the difference between these four promises?(这四个promises之间有什么区别？)
```js
doSomething().then(function () {
  return doSomethingElse();
});

doSomething().then(function () {
  doSomethingElse();
});

doSomething().then(doSomethingElse());

doSomething().then(doSomethingElse);
```

# 题外话

+ 你最近在做什么很酷的项目？
+ 您喜欢使用哪些开发工具？
+ 谁在前端社区激励你？
+ 你有什么特别的计划吗？哪一种？
+ 你最喜欢ie的什么功能?？
+ 你觉得你的咖啡怎么样？

[github](https://github.com/h5bp/Front-end-Developer-Interview-Questions)