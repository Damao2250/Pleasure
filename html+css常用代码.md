## 日常积累

+ input文本输入框占位符居中，光标居左
```html
<input class ="login" placeholder ="请输入登录名">
```
```css
input {
    /* 设置光标颜色 */
    caret-color: #c20;
}
input::placeholder{
    /* WebKit, Blink, Edge */
    /* input::-webkit-input-placeholder  */

    /* Mozilla Firefox 4 to 18 */
    /* input:-moz-placeholder  */

    /* Mozilla Firefox 19+ */
    /* input::-moz-placeholder  */

    /* Internet Explorer 10-11 */
    /* input:-ms-input-placeholder  */

    /* placeholder颜色  */
    color: #66ccff;
    /* placeholder字体大小  */
    font-size: 12px;
    /* placeholder位置  */
    text-align: center;
}


text{
    /* 文字超出省略 ... */
    text-overflow: ellipsis; 
    /*  none : 　无装饰
        blink : 　闪烁
        underline : 　下划线
        line-through : 　贯穿线
        overline : 　上划线
     */
    text-decoration: none;           /* 无装饰 */
    text-decoration: underline;      /* 下划线样式 */
    text-decoration: line-through;   /* 删除线样式-贯穿线样式 */
    text-decoration: overline;       /* 上划线样式 */
}
```
+ 图标与文字对齐
```html
<div>
    <span></span>这里是文字。确保span标签跟文字在div里垂直对齐。
</div>
```
```css
div{
    width: 550px;
    height: 100px;
    border:1px solid red;
    line-height: 100px;
}
span{
    display:inline-block;
    vertical-align:middle;
    width: 50px;
    height: 50px;
    background-color: pink;
    margin-top: 0px;/*调margin时文字不会跟着动*/
}
```

## HTML的一些小标签
+ details 标签
    - `<details>` 标签将额外的详情信息隐藏起来，用户在需要的时候点击即可展开查看详情。
```html
<h3> 测试 details 标签</h3>
<details>
    <h2>在科仁努都，与一匹马交谈</h2>
    <p>科仁努都，沙地，木屋。</p>
    <p>一匹蒙古马被拴在树桩上，</p>
    <p>它矮小，颈短，宽额，</p>
    <p>长而黑的鬃毛骄傲地飘动，</p>
    <p>时而踢腿，蹓步，旋转，</p>
    <p>时而，无奈地望着空茫茫的远方。</p>
</details>

```
<h3> 测试 details 标签</h3>
<details>
    <h2>在科仁努都，与一匹马交谈</h2>
    <p>科仁努都，沙地，木屋。</p>
    <p>一匹蒙古马被拴在树桩上，</p>
    <p>它矮小，颈短，宽额，</p>
    <p>长而黑的鬃毛骄傲地飘动，</p>
    <p>时而踢腿，蹓步，旋转，</p>
    <p>时而，无奈地望着空茫茫的远方。</p>
</details>


#

+ sunmary 标签
    - `<details>` 标签的内容默认是 "详细信息"，在其内部放置 `<summary>` 标签可以指定该值：
```html
<h3> 测试 sunmary 标签</h3>
<details>
    <summary>在科仁努都...</summary>
    <h2>在科仁努都，与一匹马交谈</h2>
    <p>科仁努都，沙地，木屋。</p>
    <p>一匹蒙古马被拴在树桩上，</p>
    <p>它矮小，颈短，宽额，</p>
    <p>长而黑的鬃毛骄傲地飘动，</p>
    <p>时而踢腿，蹓步，旋转，</p>
    <p>时而，无奈地望着空茫茫的远方。</p>
</details>

```
<h3> 测试 sunmary 标签</h3>
<details>
    <summary>在科仁努都...</summary>
    <h2>在科仁努都，与一匹马交谈</h2>
    <p>科仁努都，沙地，木屋。</p>
    <p>一匹蒙古马被拴在树桩上，</p>
    <p>它矮小，颈短，宽额，</p>
    <p>长而黑的鬃毛骄傲地飘动，</p>
    <p>时而踢腿，蹓步，旋转，</p>
    <p>时而，无奈地望着空茫茫的远方。</p>
</details>

# 

+ dialog 标签
    - `<dialog>` 标签用来展示一个对话框，通过 open 属性来指定显示和隐藏。
```html
<dialog open>
    这是一个 dialog 对话框
</dialog>
```
<dialog open>
    这是一个 dialog 对话框
</dialog>

+  
+  

#  

+ time 标签
    - `<time>` 标签用于 `date` 或 `time` 的展示，效果上没有什么特别的，在开发的角度增加代码的可读性而已。
```html
<p>今天是2020年5月5日<time>12:00</time>,天气炎热</p>
```
<p>今天是2020年5月5日<time>12:00</time>,天气炎热</p>


# 

+ datalist 标签
    - `<datalist>` 标签用来为各种类型的 `<input>` 标签提供数据源，有点像 `<select>` 标签，但它结合 `<input>` 标签可以支持自定义输入和检索。
```html
<input list="lang" placeholder="请选择语言">
<datalist id="lang">
    <option>JavaScript</option>
    <option>Java</option>
    <option>C#</option>
    <option>Python</option>
    <option>Go</option>
</datalist>
```
<input list="lang" placeholder="请选择语言">
<datalist id="lang">
    <option>JavaScript</option>
    <option>Java</option>
    <option>C#</option>
    <option>Python</option>
    <option>Go</option>
</datalist>


# 

+ progress 标签
    - `<progress>` 标签用来表示某个任务的进度，效果是一个进度条。当不指定 value 属性时是动画效果。

```html
<label for="file1">正在加载</label>
<progress id="file1" value="50" max="100"></progress>

<label for="file2">正在加载</label>
<progress id="file2"></progress>
```
<label for="file1">正在加载</label>
<progress id="file1" value="50" max="100"></progress>

<label for="file2">正在加载</label>
<progress id="file2"></progress>

# 

+ small 标签
    - `<small>` 标签使用文本更小，一般用来修饰不重要的文本信息。

```html
<p>衬衫的价格为：9<small>.00</small>元</p>
```
<p>衬衫的价格为：9<small>.00</small> 元</p>

