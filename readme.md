## 页面中使用rem单位依赖的脚本，根据psd设计图的宽度来设置根元素的大小，默认psd宽度等于640
 
	(function (doc, win) {

	    var docEl = doc.documentElement, //获取html标签
			//orientationchange方向改变事件
		resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
		recalc = function () {
				//当前设备视口宽度
		    var clientWidth = docEl.clientWidth;
		    if (!clientWidth) return;
		    docEl.style.fontSize = 100 * (clientWidth / 640) + 'px';
		};

	    if (!doc.addEventListener) return;
	    win.addEventListener(resizeEvt, recalc, false);
	    doc.addEventListener('DOMContentLoaded', recalc, false);

	})(document, window);
