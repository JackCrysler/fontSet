#### 以下是用rem作为单位进行页面排版时依赖的脚本，原理是根据设计图的宽度来动态设置根元素的大小，从而实现自适应的目的（与媒体查询media query有异曲同工之处）。默认宽度等于640。取设计图上量出来的值除以100即可。
 
	(function (doc, win, image_width) {

	    var docEl = doc.documentElement, //获取html标签
			//orientationchange方向改变事件
		resizeEvt = 'orientationchange' in window ? 'orientationchange' : 'resize',
		recalc = function () {
				//当前设备视口宽度
		    var clientWidth = docEl.clientWidth;
		    if (!clientWidth) return;
		    docEl.style.fontSize = 100 * (clientWidth / image_width) + 'px';
		};

	    if (!doc.addEventListener) return;
	    win.addEventListener(resizeEvt, recalc, false);
	    doc.addEventListener('DOMContentLoaded', recalc, false);

	})(document, window, 640);
