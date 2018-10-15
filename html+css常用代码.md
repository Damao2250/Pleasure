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