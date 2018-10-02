## 日常积累

+ 任意位数随机验证码
```js
/**
 * [任意位数随机验证码]
 * @param  {Number} n [随机验证码的位数]
 * @return {String}   [返回的验证码]
 */
function randomCode(n){
    var mycode = '';
    for(var i=0;i<n;i++){
        mycode += parseInt(Math.random()*10);
    }
    return mycode;
}
//使用示例
// randomCode(2);
// randomCode(6);
```