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