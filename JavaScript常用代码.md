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

+ 任意范围内随机整数
```js
/**
 * 任意范围内的随机整数
 * @param  {Number} min [最小值]
 * @param  {Number} max [最大值]
 * @return {Number}     [min-max间的随机整数]
 */

// Math.random();//0-1（不包括1）的数
/*
    Math.random()		        res
    0					min
    1					max
 */

function randomNumber(min,max){
    return parseInt(Math.random()*(max-min+1))+min;
}

// randomNumber(0,10);
//包括0和10
```

+ 随机颜色
```js
/**
 * 随机颜色
 * @return {String} [rgb颜色]
 */
function randomColor(num){
    if(num === 16){
	    var str = '0123456789abcdef';
	    var color = '#';
	    for(var i=0;i<6;i++){
		    // 获取随机索引值
		    var idx = parseInt(Math.random()*str.length);
		    // 根据随机索引值得到随机16进制字符
		    color += str[idx];
	    }
	    return color;
    }else{
	    var r = parseInt(Math.random()*256);
	    var g = parseInt(Math.random()*256);
	    var b = parseInt(Math.random()*256);
	    return 'rgb('+r+','+g+','+b+')';	
    }
}
//randomColor(16);
//#66ccff
//randomColor();
//rgb(0,0,0)
```