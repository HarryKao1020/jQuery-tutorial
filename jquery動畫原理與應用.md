# jQuery 動畫操作原理
## 載入外掛:
* jquery更改顏色 https://cdnjs.cloudflare.com/ajax/libs/jquery-color/2.1.2/jquery.color.min.js
* jquery使用的過渡效果: https://cdnjs.cloudflare.com/ajax/libs/jquery-easing/1.4.1/jquery.easing.min.js
* velocity https://cdnjs.cloudflare.com/ajax/libs/velocity/1.5.0/velocity.min.js
## 1. hide / show (時間,時間完後要執行的函數)  : 有縮放效果

html
```html
.rect.rect1
button.btn1 顯示
button.btn1h 隱藏
```
css
```css
.rect{
	width: 100px;
	height: 100px;
	border: 5px solid black;
	position: relative;
	
}
```
JS : 當按下按鈕時
```javascript
// callback 上文字
function showText(){
	$(this).text("hello world")
}
// ------show / hide
$(".btn1").click(function(){
	$(".rect1").show(1000,showText)
})
$(".btn1h").click(function(){
	$(".rect1").hide(1000)
})
```
---
## 2. fadeIn / fadeOut(speed,callback)  : 
html
```html
.rect.rect2
button.btn2  淡入
button.btn2h 淡出
```
js
```javascript
$(".btn2").click(function(){
	$(".rect2").fadeIn(1000)
})
$(".btn2h").click(function(){
	$(".rect2").fadeOut(1000)
})
```
---
## 3. slideUp / slideDown(speed,callback) :有上下縮放的效果
html
```html
.rect.rect3 我誰?<br> 我丸 
button.btn3  顯示
button.btn3h 隱藏
```
JS
```javascript
// slideUp/Down
$(".btn3").click(function(){
	$(".rect3").slideDown(1000)
})
$(".btn3h").click(function(){
	$(".rect3").slideUp(1000)
})
```
---
## 4. animate({styles},speed,easing,callback) :
html
```html
.rect.rect4 
button.btn4  移動
button.btn4h 隱藏
```
JS
```javascript
// animate
$(".btn4").click(function(){
	$(".rect4").animate({
		left: "200px",
		height: "200px"
	},{
		duration : 500
	}).animate({
		left: "+=300px",
		height: "150px"
	},{
		duration: 1000
	}).delay(1000).animate({
		left: "+=300px",
		height: "150px",
// 		引入jquery-color
		backgroundColor: "red"
	},{
		duration: 1000,
		complete: function(){
			console.log("I'm red")
			$(".rect4").text("載入完畢")
		}
	}).animate({
		left: "+=100px",
		width: "50px",
		height: "50px",
		borderRadius : "50%"
	}).animate({
		left: "0px"
// 		加入jquery-easing
	},2000,"easeOutElastic")
})

$(".btn4h").click(function(){
	$(".rect4").hide(1000)
})

```
---
## 5. velocity: 外掛，請使用第一版，可以使用transform的一些屬性，以及可以來回撥放。
html
```html
.rect.rect5 
button.btn5  轉動
button.btn5h 隱藏
```
JS
```javascript
// 旋轉  /  加入velocity.js
$(".btn5").click(function(){
	$(".rect5").velocity({
		translateX: "30px",
		rotateZ: "45deg"
	},{
		loop: 4
	})
})
