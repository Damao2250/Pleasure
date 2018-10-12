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

+ 数据类型判断

```js
/**
 * 数据类型判断
 * @param  {Every} data [任意数据类型]
 * @return {String}      [返回数据类型对应的字符串]
 */
function type(data){
	return Object.prototype.toString.call(data).slice(8,-1).toLowerCase();
}
//type(10);//number
//type(/10/);//regexp
```

+ Cookie操作
````js
// Cookie的操作
var Cookie = {
	/**
	 * 设置cookie
	 * @param {String} name   [cookie名]
	 * @param {String} value  [cookie值]
	 * @param {[Object]} params [参数，是一个对象]
	 	* expires	{Date}		有效期
	 	* path		{String}	保存路径
	 	* domain	{String}	域名
	 	* secure	{Booolean}	安全性
	 */
	set:function(name,value,params){
		// 必填
		var str = name + '=' + value;

		// 判断是否有参数
		if(params){

			// 有效期
			if(params.expires){
				str += ';expires=' + params.expires.toUTCString();
			}

			// 保存路径
			if(params.path){
				str += ';path='+params.path;
			}

			// 域名
			if(params.domain){
				str += ';domain='+params.domain;
			}

			// 安全性
			if(params.secure){
				str += ';secure';
			}
		}

		document.cookie = str;
	},

	/**
	 * [获取name对应的cookie值]
	 * @param  {String} name [cookie名]
	 * @return {String}      [返回name对应的cookie的值]
	 */
	get:function(name){
		// 获取所有cookie
		var allCookies = document.cookie;


		// 用于保存结果
		var res = '';


		// String->Array
		allCookies = allCookies.split('; ');

		// 遍历找出所需cookie
		allCookies.forEach(function(item){
			// 拆分name,value
			var arr = item.split('=');

			if(arr[0] === name){
				res = arr[1];
			}
		});

		return res;
	},

	remove:function(name){
		var now = new Date();
		now.setDate(now.getDate()-1);

		// document.cookie = name + '=null;expires='+now.toUTCString();
		this.set(name,'x',{expires:now});
	}
}

// Cookie.set('username','laoxie')
// Cookie.set('password','123',{expires:date,});
// Cookie.remove('password');
// Cookie.get('left');//47px;
```

* 扩展运算符
	+ 扩展运算符用三个点号表示，功能是把数组或类数组对象展开成一系列用逗号隔开的值
```js
var num = function(a, b, c) {
    console.log(a);
    console.log(b);
    console.log(c);
}

var arr = [1, 2, 3];

//传统写法
num(arr[0], arr[1], arr[2]);

//使用扩展运算符
num(...arr);
//1
//2
//3
```
```js
//扩展运算符简单应用
//arrayMax 返回数组中的最大值
const arrayMax = arr => Math.max(...arr);
// arrayMax([10, 1, 5]) -> 10
```

