+ css3新增了哪些特性

    1. CSS3实现圆角（border-radius），阴影（box-shadow），

    2. 对文字加特效（text-shadow、），线性渐变（grtransform）adient），旋转（

    3. transform:rotate(9deg) scale(0.85,0.90) translate(0px,-30px) skew(-9deg,0deg);// 旋转,缩放,定位,倾斜

    4. 增加了更多的CSS选择器  多背景 rgba

        1.CSS3的选择器
        1）E:last-child 匹配父元素的最后一个子元素E。
        2）E:nth-child(n)匹配父元素的第n个子元素E。 
        3）E:nth-last-child(n) CSS3 匹配父元素的倒数第n个子元素E。

    5. 在CSS3中唯一引入的伪元素是 ::selection.

    6. 媒体查询，多栏布局

    7. border-image

    8. @Font-face 特性

        Font-face 可以用来加载字体样式，而且它还能够加载服务器端的字体文件，让客户端显示客户端所没有安装的字体。


+ HTML5新增了哪些特性

    1. HTML5 新元素

        <header>：代表HTML的头部数据

        <footer>：页面的脚部区域

        <nav>：页面导航元素

        <article>：自包含的内容

        <section>：使用内部article去定义区域或者把分组内容放到区域里

        <aside>：代表页面的侧边栏内容

    
    2. 新增表单元素type：
        email、url、tel、number（min、max、step）、range（进度条）、color（颜色面板）、search

    1. 拖拽释放(Drag and drop) API

    2. 语义化更好的内容标签（header,nav,footer,aside,article,section）

    3. 音频、视频API(audio,video)

    4. 画布(Canvas) API

    5. 地理(Geolocation) API

    6. 本地离线存储 localStorage 长期存储数据，浏览器关闭后数据不丢失；

    7. sessionStorage 的数据在浏览器关闭后自动删除

    8. 表单控件，calendar、date、time、email、url、search  

    9. 新的技术webworker, websocket, Geolocation



+ 自适应：不同大小设备呈现同样的页面效果，只是文字、图片等的大小不一样，但是相对位置一样。例如：百分比布局、弹性盒布局flex、分栏布局。

+ 响应式：同一页面在不同大小设备(窗口)可能呈现不一样的页面效果，自适应布局+媒体查询即可实现。（应用：相对简单、内容较少的页面）


+ 什么是响应式设计？（优缺点）

    它是关于网页制作的过程中让不同的设备有不同的尺寸和不同的功能。响应式设计是让所有的人能在这些设备上让网站运行正常

    优点：
    用户体验，可以根据特定设备进行量身定制（兼容性好，跨平台）
    开发维护和运营上成本降低

    缺点：
    代码量大
    缓慢的页面加载速度
    响应式设计会花费更多
    不适合一些大型的门户网或者电商网站（页面多）
    图片并没有根据设备调整到适宜的大小

+ 什么是自适应布局（优缺点）




### 清除浮动的本质
+ 清除浮动主要是为了解决父级元素因为子级元素浮动引起内部高度为0的问题，清除浮动之后，父级元素就会根据浮动的子元素盒子自动计算高度，父级元素就有了高度，就不会影响下面的标准流


