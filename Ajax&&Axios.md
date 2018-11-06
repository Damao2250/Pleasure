## 跨域
* 域名组成部分
> http://www.damao2250.com:8080/script/jquery.js

| http:// | www.   | damao2250.com | :8080  | /script/jquery.js |
|---------|--------|---------------|--------|-------------------|
| 协议    | 子域名  |    主域名     | 端口号  | 请求资源地址
* 什么是跨域

    1. 当协议、子域名、主域名、端口号中任意一个不相同时，都算作不同域。不同域之间相互请求资源，就算作“跨域”。
    2. 之所以会跨域，是因为受到了同源策略的限制，同源策略要求源相同才能正常进行通信，即协议、域名、端口号都完全一致。

    注意：
    1. 跨域并不是请求发不出去，请求能发出去，服务端能收到请求并正常返回结果，只是结果被浏览器拦截了。
    2. 如果是协议和端口造成的跨域问题“前台”是无能为力的。
    3. 在跨域问题上，域仅仅是通过“URL的首部”来识别而不会根据域名对应的IP地址是否相同来判断。“URL的首部”可以理解为“协议, 域名和端口必须匹配”。

* 什么是同源策略及其限制

    1. 同源策略限制从一个源加载的文档或脚本如何与来自另一个源的资源进行交互。
    2. 这是一个用于隔离潜在恶意文件的关键的安全机制。
    3. 它的存在可以保护用户隐私信息，防止身份伪造等(读取Cookie)。

    同源策略限制内容有：
    1. Cookie、LocalStorage、IndexedDB 等存储性内容
    2. DOM 节点
    3. AJAX 请求不能发送

    但是有四个标签是允许跨域加载资源：
    ```html
    1. <img src=XXX>
    2. <link href=XXX>
    3. <script src=XXX>
    4. <iframe src=XXX>
    ```

* 处理跨域方法一——JSONP
1. JSON原理

    利用 `<script>` 元素的开放策略，网页可以得到从其他来源东陶产生的JSON数据，JSONP请求一定要对方的服务器做支持

2. JSONP和Ajax对比

    JSONP和AJAX相同，都是客户端向服务器端发送请求，从服务器端获取数据的方式。但AJAX属于同源策略，JSONP属于非同源策略（跨域请求）。

3. JSONP优缺点

    JSONP优点是兼容性好，可用于解决主流浏览器的跨域数据访问的问题。缺点是仅支持get方法具有局限性。

4. JSONP的流程
    + 声明一个回调函数，其函数名(如fn)当做参数值，要传递给跨域请求数据的服务器，函数形参为要获取目标数据(服务器返回的data)

    + 创建一个 `<script>`标签，把那个跨域的API数据接口地址，赋值给script的src，还要在这个地址中向服务器传递该函数名（可以通过问号传参 :?callback=fn）。
    
    + 服务器接收到请求后，需要进行特殊的处理：把传递进来的函数名和它需要给你的数据拼接成一个字符串，例如：传递进去的函数名是fn，它准备好的数据是 ` fn([{"name":"shuju"}]）`

    + 最后服务器把准备的数据通过HTTP协议返回给客户端，客户端再调用执行之前声明的回调函数（fn），对返回的数据进行操作。

    ```js
       <script type="text/javascript" >
            function fn(data) {
                console.log(data.msg);
            }
        </script>
        <script type="text/javascript" src = "http://crossdomain.com/jsonServerResponse?jsonp=fn"></script>

        //其中 fn 是客户端注册的回调的函数，目的获取跨域服务器上的json数据后，对数据进行在处理。
        //最后服务器返回给客户端数据的格式为：fn({ msg:'this  is  json  data'})
    ```
5. jQuery的jsonp形式

    JSONP都是GET和异步请求的，不存在其他的请求方式和同步请求，且jQuery默认就会给JSONP的请求清除缓存。

    ```js
    $.ajax({
        url:"http://crossdomain.com/jsonServerResponse",
        dataType:"jsonp",
        type:"get",//可以省略
        jsonpCallback:"fn",//->自定义传递给服务器的函数名，而不是使用jQuery自动生成的，可省略
        jsonp:"jsonp",//->把传递函数名的那个形参callback变为jsonp，可省略
        success:function(data){
            console.log(data);
        }
    });
    ```

* 处理跨域方法二——CORS
* 处理跨域方法三——WebSocket
* 处理跨域方法四——postMessage

* cors


    


