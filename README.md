# ImagepreviewTailor
一个图片预览并支持裁剪的demo，采用Jcrop插件实现裁剪功能

##主要功能代码
```javascript
//预览函数，通过FileReader实现预览功能，在IE低版本浏览器不支持
function preImg(sourceId, targetId) {
	if (typeof FileReader === 'undefined') {
		alert('Your browser does not support FileReader...');
		return;
	}
	var reader = new FileReader();

	reader.onload = function(e) {
		var img = document.getElementById(targetId);
		img.src = this.result;

		//对预览的图片添加裁剪插件
		$('#'+targetId).Jcrop({
	        aspectRatio:1,
	        onSelect:updateCoords,
        });
	}
	reader.readAsDataURL(document.getElementById(sourceId).files[0]);
}
```

##Demo展示效果
![展示效果](https://github.com/RedstoneCMX/ImagepreviewTailor/blob/master/showimages/show1.png)
