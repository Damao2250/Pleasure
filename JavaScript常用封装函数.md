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
```js
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
+ 节点操作
```js
var Element = {
	// 对象的方法

	/**
	 * 过滤非元素节点
	 * @param  {Array} nodes [节点集合]
	 * @return {Array} [返回只包含元素节点的数组]
	 */
	get:function(nodes){
		// 用于存放结果
		var res = [];

		// 删除非元素节点
		for(var i=0;i<nodes.length;i++){
			if(nodes[i].nodeType === 1){
				res.push(nodes[i]);
			}
		}

		return res;
	},

	/**
	 * [得到ele元素下的所有子元素]
	 * @param  {Element} ele [父元素]
	 * @return {Array}     [ele元素的所有子元素]
	 */
	children:function(ele){
		// var res = [];

		// for(var i=0;i<ele.childNodes.length;i++){
		// 	if(ele.childNodes[i].nodeType === 1){
		// 		res.push(ele.childNodes[i]);
		// 	}
		// }

		// return res;

		return this.get(ele.childNodes);
	},

	// 得到前一个元素节点
	prev:function(ele){
		var res = ele.previousSibling;

		// while循环方案
		// while(res.nodeType !== 1 && res !== null){
		// 	res = res.previousSibling
		// }

		// return res;


		// 递归方案
		if(res===null || res.nodeType === 1){
			return res;
		}

		return this.prev(res);
	},

	// 得到后一个元素节点
	next:function(ele){
		var res = ele.nextSibling;
		if(res===null || res.nodeType === 1){
			return res;
		}

		return this.next(res);
	},

	// 拓展：兼容IE8-
	getByClass:function(name){

	}
}
```

+ 获取元素css样式
```js
/**
 * [获取元素的css样式，兼容IE8-]
 * @param  {Element} ele  [获取样式的元素]
 * @param  {String} attr [css属性名]
 * @return {String}      [返回attr对应的css属性值]
 */
function getCss(ele,attr){
	// 不要判断是否为IE6,IE7,IE8
	// 而是判断用户的浏览器是否支持某一个方法
	if(window.getComputedStyle){
		// 标准浏览器
		return getComputedStyle(ele)[attr];
	}else if(ele.currentStyle){
		// IE6,7,8
		return ele.currentStyle[attr];
	}else{
		// 其他浏览器，直接返回内联样式
		return ele.style[attr];
	}
}


// getCss(box,'font-size');//30px
```

+ 元素绑定事件
```js
/**
 * 给元素绑定事件，兼容IE8-
 * @param  {Node}  ele       [绑定事件的元素]
 * @param  {String}  type      [事件类型]
 * @param  {Function}  handler   [事件处理函数]
 * @param  {Boolean} isCapture [是否捕获]
 */
function bind(ele,type,handler,isCapture){
	// 标准浏览器
	if(ele.addEventListener){
		ele.addEventListener(type,handler,isCapture);
	}

	// IE8-
	else if(ele.attachEvent){
		ele.attachEvent('on'+type,handler);
	}

	// 其他浏览器
	else{
		ele['on'+type] = handler;
	}
}

// // 移除事件
// function unbind(){

// }


// // 只能绑定一次的事件
// function one(){

// }

var Event = {
	// 绑定事件
	bind:function(){},

	// 移除事件
	unbind:function(){},

	// 只能绑定一次的事件
	one:function(){}
}

// 封装函数时，如果不知如何下手
// 先用
// bind(box,'click',function(){},true);

```

+ 动画函数1
```js
function animate(ele,attr,target){
	// 拼接定时器名字width->widthTimer,opacity->opacityTimer
	var timerName = attr + 'Timer';

	clearInterval(ele[timerName]);
	ele[timerName] = setInterval(function(){
		// 获取当前值left,top,width,fontSize,opaicty.....
		// var current = getComputedStyle(ele)[attr];
		var current = getCss(ele,attr);//100px,16px,0.5,45deg...

		// 提取单位
		var unit = current.match(/[a-z]+$/);//

		// 避免报错
		if(unit===null){
			unit = '';
		}else{
			unit = unit[0];
		}

		// 提取值
		current = parseFloat(current);

		// 计算缓冲速度
		// 避免速度过小，同时避免速度为0
		var speed = (target-current)/10;

		if(attr === 'opacity'){
			// 避免小数位过多
			current = current.toFixed(2)*1;

			if( speed<0 && speed>-0.01){
				speed = -0.01;
			}

			if( speed>0 && speed<0.01){
				speed = 0.01;
			}
			// console.log(speed)
			// speed = speed>0 ? 0.01 : -0.01;
		}else{
			speed = speed>0 ? Math.ceil(speed) : Math.floor(speed)
		}

		var val = current + speed;

		// console.log(val);

		// 到达目标值
		// 停止定时器
		if(val === target){
			clearInterval(ele[timerName]);

			val = target;
		}


		ele.style[attr] = val + unit;


	},30);
}

// animate(div,'left',200);
```

+ 动画函数2
```js
function animate(ele,options,callback){//undefined
	// target,attr
	// 先获取定时器数量
	var timerLen = 0;
	for(var key in options){
		timerLen++;

		(function(attr){
			var timerName = attr + 'Timer';

			// 获取目标值
			var target = options[attr];

			clearInterval(ele[timerName]);
			
			ele[timerName] = setInterval(function(){
				var current = getCss(ele,attr);//100px,16px,0.5,45deg...

				// 提取单位
				var unit = current.match(/[a-z]+$/);//

				// 避免报错
				if(unit===null){
					unit = '';
				}else{
					unit = unit[0];
				}

				// 提取值
				current = parseFloat(current);

				// 计算缓冲速度
				// 避免速度过小，同时避免速度为0
				var speed = (target-current)/10;

				if(attr === 'opacity'){
					// 避免小数位过多
					current = current.toFixed(2)*1;

					if( speed<0 && speed>-0.01){
						speed = -0.01;
					}

					if( speed>0 && speed<0.01){
						speed = 0.01;
					}
					// console.log(speed)
					// speed = speed>0 ? 0.01 : -0.01;
				}else{
					speed = speed>0 ? Math.ceil(speed) : Math.floor(speed);
				}

				var val = current + speed;

				// console.log(val);

				// 到达目标值
				// 停止定时器
				if(val === target){
					clearInterval(ele[timerName]);

					val = target;

					// 每完成一个动画，数量减1
					timerLen--;

					// 当定时器为最后一个，且有回调函数时，执行回调函数
					if(timerLen===0 && typeof callback === 'function'){
						callback();
					}
				}


				ele.style[attr] = val + unit;
			},30);

		})(key);
	}
}

// animate(div,'left',200);
```

+ 时间戳转化时间格式

```js
//formatDate(123456789) ---> 年-月-日 时：分：秒
//formatDate(123456789,1) ---> 年-月-日 时：分
//formatDate(123456789,0) ---> 年-月-日
function formatDate(secs,format){
	var t = new Date(secs);
	var year = t.getFullYear();
	var month = t.getMonth() + 1;
	if(month < 10){month = '0' + month;}
	var date = t.getDate();
	if(date < 10){date = '0' + date;}
	var hour = t.getHours();
	if(hour < 10){hour = '0' + hour;}
	var minute = t.getMinutes();
	if(minute < 10){minute = '0' + minute;}
	var second = t.getSeconds();
    if(second < 10){second = '0' + second;}
    if(format===0){
        return year+'-'+month+'-'+date;
    }else if(format===1){
        return year+'-'+month+'-'+date+' '+hour+':'+minute;
    }else{
        return year+'-'+month+'-'+date+' '+hour+':'+minute+':'+second;   
    }
}
```

+  防抖
```js
/**
 *  防抖
 * 	其中一种解决方案就是每次用户停止输入后，延迟超过500ms时，才去搜索此时的String，这就是防抖。 
 *  原理：将若干个函数调用合成为一次，并在给定时间过去之后仅被调用一次。
**/
function debounce(fn, delay) {
  // 维护一个 timer，用来记录当前执行函数状态
  let timer = null;
  return function() {
    // 通过 ‘this’ 和 ‘arguments’ 获取函数的作用域和变量
    let context = this;
    let args = arguments;
    // 清理掉正在执行的函数，并重新执行
    clearTimeout(timer);
    timer = setTimeout(function() {
      fn.apply(context, args);
    }, delay);
  }
}
let flag = 0; // 记录当前函数调用次数
// 当用户滚动时被调用的函数
function foo() {
  flag++;
  console.log('Number of calls: %d', flag);
}

// 在 debounce 中包装我们的函数，过 2 秒触发一次
document.body.addEventListener('scroll', debounce(foo, 2000));

/**
 * debounce函数封装后，返回内部函数
 * 每一次事件被触发，都会清除当前的timer然后重新设置超时并调用。这会导致每一次高频事件都会取消前一次的超时调用，导致事件处理程序不能被触发
 * 只有当高频事件停止，最后一次事件触发的超时调用才能在delay时间后执行
**/

```

+ 节流

 ```js
/**
 *  节流
 * 	原理：节流函数不管事件触发有多频繁，都会保证在规定时间内一定会执行一次真正的事件处理函数。（一段时间内只允许函数执行一次） 
 * 	代码实现有两种，一种是时间戳，另一种是定时器 
 *  应用场景如： 输入框的联想、可以限定用户在输入时，只在每两秒钟响应一次联想(或是两秒钟发送一次搜索请求)
 */

//1.定时器
var throttle = function (func, delay) {
  var timer = null;
  return function () {
    var context = this;
    var args = arguments;
    if (!timer) {
      timer = setTimeout(function () {
        func.apply(context, args);
        timer = null;
      }, delay);
    }
  }
}

//2.时间戳
function throttle(func, delay){
  let prev = Date.now();
  return function(){
    const context = this;
    const args = arguments;
    const now = Date.now();
    if(now - prev >= delay){
      func.apply(context, args);
      prev = Date.now();
    }
  }
}
```

+ 现金额大写转换函数
```js
    //upDigit(168752632)
    //result："人民币壹亿陆仟捌佰柒拾伍万贰仟陆佰叁拾贰元整"
    //upDigit(1682)
    //result："人民币壹仟陆佰捌拾贰元整"
    //upDigit(-1693)
    //result："欠人民币壹仟陆佰玖拾叁元整"
    function upDigit(n) {
        var fraction = ['角', '分', '厘'];
        var digit = ['零', '壹', '贰', '叁', '肆', '伍', '陆', '柒', '捌', '玖'];
        var unit = [
            ['元', '万', '亿'],
            ['', '拾', '佰', '仟']
        ];
        var head = n < 0 ? '欠人民币' : '人民币';
        n = Math.abs(n);
        var s = '';
        for (var i = 0; i < fraction.length; i++) {
            s += (digit[Math.floor(n * 10 * Math.pow(10, i)) % 10] + fraction[i]).replace(/零./, '');
        }
        s = s || '整';
        n = Math.floor(n);
        for (var i = 0; i < unit[0].length && n > 0; i++) {
            var p = '';
            for (var j = 0; j < unit[1].length && n > 0; j++) {
                p = digit[n % 10] + unit[1][j] + p;
                n = Math.floor(n / 10);
            }
            s = p.replace(/(零.)*零$/, '').replace(/^$/, '零') + unit[0][i] + s;
            //s = p + unit[0][i] + s;
        }
        return head + s.replace(/(零.)*零元/, '元').replace(/(零.)+/g, '零').replace(/^整$/, '零元整');
    }
```

+ 清除对象中值为空的属性

```js

//filterParams({a:"",b:null,c:"010",d:123})
//Object {c: "010", d: 123}
filterParams: function(obj) {
	var _newPar = {};
	for (var key in obj) {
		if ((obj[key] === 0 || obj[key]) && obj[key].toString().replace(/(^\s*)|(\s*$)/g, '') !== '') {
			_newPar[key] = obj[key];
		}
	}
	return _newPar;
}
```

+ 封装ajax函数

```js
/* 封装ajax函数
	* @param {string}obj.type http连接的方式，包括POST和GET两种方式
	* @param {string}obj.url 发送请求的url
	* @param {boolean}obj.async 是否为异步请求，true为异步的，false为同步的
	* @param {object}obj.data 发送的参数，格式为对象类型
	* @param {function}obj.success ajax发送并接收成功调用的回调函数
	* @param {function}obj.error ajax发送失败或者接收失败调用的回调函数
	*/
//  ajax({
//      type:'get',
//      url:'xxx',
//      data:{
//          id:'111'
//      },
//      success:function(res){
//          console.log(res)
//      }
//  })
ajax: function(obj) {
	obj = obj || {};
	obj.type = obj.type.toUpperCase() || 'POST';
	obj.url = obj.url || '';
	obj.async = obj.async || true;
	obj.data = obj.data || null;
	obj.success = obj.success || function() {};
	obj.error = obj.error || function() {};
	var xmlHttp = null;
	if (XMLHttpRequest) {
		xmlHttp = new XMLHttpRequest();
	} else {
		xmlHttp = new ActiveXObject('Microsoft.XMLHTTP');
	}
	var params = [];
	for (var key in obj.data) {
		params.push(key + '=' + obj.data[key]);
	}
	var postData = params.join('&');
	if (obj.type.toUpperCase() === 'POST') {
		xmlHttp.open(obj.type, obj.url, obj.async);
		xmlHttp.setRequestHeader('Content-Type', 'application/x-www-form-urlencoded;charset=utf-8');
		xmlHttp.send(postData);
	} else if (obj.type.toUpperCase() === 'GET') {
		xmlHttp.open(obj.type, obj.url + '?' + postData, obj.async);
		xmlHttp.send(null);
	}
	xmlHttp.onreadystatechange = function() {
		if (xmlHttp.readyState == 4 && xmlHttp.status == 200) {
			obj.success(xmlHttp.responseText);
		} else {
			obj.error(xmlHttp.responseText);
		}
	};
}
```

+ 图片没加载出来时用一张图片代替

```js
function aftLoadImg(obj, url, errorUrl, cb) {
	var oImg = new Image(),
		_this = this;
	oImg.src = url;
	oImg.onload = function() {
		obj.src = oImg.src;
		if (cb && _this.istype(cb, 'function')) {
			cb(obj);
		}
	}
	oImg.onerror = function() {
		obj.src = errorUrl;
		if (cb && _this.istype(cb, 'function')) {
			cb(obj);
		}
	}
}
```

+ 图片滚动懒加载

```js

//@className {string} 要遍历图片的类名
//@num {number} 距离多少的时候开始加载 默认 0
//比如，一张图片距离文档顶部3000，num参数设置200，那么在页面滚动到2800的时候，图片加载。不传num参数就滚动，num默认是0，页面滚动到3000就加载
//html代码
//<p><img data-src="lawyerOtherImg.jpg" class="load-img" width='528' height='304' /></p>
//<p><img data-src="lawyerOtherImg.jpg" class="load-img" width='528' height='304' /></p>
//<p><img data-src="lawyerOtherImg.jpg" class="load-img" width='528' height='304' /></p>....
//data-src储存src的数据，到需要加载的时候把data-src的值赋值给src属性，图片就会加载。
//详细可以查看testLoadImg.html

//window.onload = function() {
//  loadImg('load-img',100);
//  window.onscroll = function() {
//      loadImg('load-img',100);
//      }
//}
loadImg: function(className, num, errorUrl) {
	var _className = className || 'ec-load-img',
		_num = num || 0,
		_this = this,
		_errorUrl = errorUrl || null;
	var oImgLoad = document.getElementsByClassName(_className);
	for (var i = 0, len = oImgLoad.length; i < len; i++) {
		if (document.documentElement.clientHeight + document.documentElement.scrollTop > oImgLoad[i].offsetTop - _num && !oImgLoad[i].isLoad) {
			//记录图片是否已经加载
			oImgLoad[i].isLoad = true;
			//设置过渡，当图片下来的时候有一个图片透明度变化
			oImgLoad[i].style.cssText = "transition: ''; opacity: 0;"
			if (oImgLoad[i].dataset) {
				this.aftLoadImg(oImgLoad[i], oImgLoad[i].dataset.src, _errorUrl, function(o) {
					setTimeout(function() {
						if (o.isLoad) {
							_this.removeClass(o, _className);
							o.style.cssText = "";
						}
					}, 1000)
				});
			} else {
				this.aftLoadImg(oImgLoad[i], oImgLoad[i].getAttribute("data-src"), _errorUrl, function(o) {
					setTimeout(function() {
						if (o.isLoad) {
							_this.removeClass(o, _className);
							o.style.cssText = "";
						}
					}, 1000)
				});
			}
			(function(i) {
				setTimeout(function() {
					oImgLoad[i].style.cssText = "transition:all 1s; opacity: 1;";
				}, 16)
			})(i);
		}
	}
}
```

+ 手机类型判断

```js

browserInfo: function(type) {
	switch (type) {
		case 'android':
			return navigator.userAgent.toLowerCase().indexOf('android') !== -1
		case 'iphone':
			return navigator.userAgent.toLowerCase().indexOf('iphone') !== -1
		case 'ipad':
			return navigator.userAgent.toLowerCase().indexOf('ipad') !== -1
		case 'weixin':
			return navigator.userAgent.toLowerCase().indexOf('micromessenger') !== -1
		default:
			return navigator.userAgent.toLowerCase()
	}
}
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


