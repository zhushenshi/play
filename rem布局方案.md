### rem布局方案

```css
	//网易布局方案 
	//把当前的viewport宽度设置为 ideal viewport 的宽度
	//把当前的viewport宽度设置为 ideal viewport（理想适口宽度） 的宽度
//<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover">
	//设置html的字体 单位使用rem
	@media screen and (max-width: 320px)
		html {
			font-size: 42.667px;
			font-size: 13.33333vw;
		}

		@media screen and (max-width: 360px) and (min-width: 321px)
		html {
			font-size: 48px;
			font-size: 13.33333vw;
		}
		@media screen and (max-width: 375px) and (min-width: 361px)
		html {
			font-size: 50px;
			font-size: 13.33333vw;
		}
		@media screen and (max-width: 393px) and (min-width: 376px)
		html {
			font-size: 52.4px;
			font-size: 13.33333vw;
		}
		@media screen and (max-width: 412px) and (min-width: 394px)
		html {
			font-size: 54.93px;
			font-size: 13.33333vw;
		}
		@media screen and (max-width: 414px) and (min-width: 413px)
		html {
			font-size: 55.2px;
			font-size: 13.33333vw;
		}
		@media screen and (max-width: 480px) and (min-width: 415px)
		html {
			font-size: 64px;
			font-size: 13.33333vw;
		}
		@media screen and (max-width: 540px) and (min-width: 481px)
		html {
			font-size: 72px;
			font-size: 13.33333vw;
		}
		@media screen and (max-width: 640px) and (min-width: 541px)
		html {
			font-size: 85.33px;
			font-size: 13.33333vw;
		}
		@media screen and (max-width: 720px) and (min-width: 641px)
		html {
			font-size: 96px;
			font-size: 13.33333vw;
		}
		@media screen and (max-width: 768px) and (min-width: 721px)
		html {
			font-size: 102.4px;
			font-size: 13.33333vw;
		}
		@media screen and (min-width: 769px)
		html {
			font-size: 102.4px;
			font-size: 13.33333vw;
		}
		//vw无效时也可以使用
		//100vw/750px*100=13.333333
		//0.01rem=1px相对于设计稿（750px的设计稿）
```

### 1rem=100px

```javascript
//<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover">
//动态设置font-size的大小
//单位使用rem  //0.01rem=1px相对于设计稿（750px的设计稿）
(function (doc,win){
	var docEl = doc.documentElement,
		resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
		recalc = function(){
			var clientWidth = docEl.clientWidth;
			if (!clientWidth) return;
			if(clientWidth>=750){
				docEl.style.fontSize = '100px';
			}else{
				docEl.style.fontSize = 100 * (clientWidth / 750) + 'px';
			}
		};
	if (!doc.addEventListener) return;
	win.addEventListener(resizeEvt, recalc, false);
	doc.addEventListener('DOMContentLoaded', recalc, false);
})(document, window);
//设计稿750px
```



### 方案  //  

```javascript
//<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover">
//动态设置html的font-size
375 font-size：100px
750 font-size：200px
750 3.75rem
1px 0.005rem
document.documentElement.style.fontSize = document.documentElement.clientWidth / 375 *100 + 'px'; 
//加上 也可以使用rem  1rem=75px
```



### scale方案

```javascript
 //<meta name="viewport" content="width=device-width,initial-scale=1,minimum-scale=1,maximum-scale=1,user-scalable=no,viewport-fit=cover">
//使用px单位 
//需要刷新
 console.log(devicePixelRatio)
 console.log(document.documentElement.clientWidth)
 //var scale = 1 / devicePixelRatio;
var scale = document.documentElement.clientWidth/750; //相对于750px的单位等比放大缩小

document.querySelector('meta[name="viewport"]').setAttribute('content','initial-scale=' + scale + ', maximum-scale=' + scale + ', minimum-scale=' + scale + ', user-scalable=no');

document.documentElement.style.fontSize = document.documentElement.clientWidth / 10 + 'px'; //加上 也可以使用rem  1rem=75px
console.log(document.documentElement.clientWidth)
```

### lib-flexible 已弃用