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