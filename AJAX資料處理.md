# AJAX入門
## 什 麼 是 A J A X ?
### AJAX全名為:非同步 JavaScript 及 XML（Asynchronous JavaScript and XML，AJAX）
## 為 何 使 用 A J A X ?
### 想想你在博客來點選一本書想看他的詳細內容時
#### 未使用AJAX :
##### 會傳送給伺服器一個要求查看詳細內容的請求，伺服器再回傳一個新的網頁給使用者，但回傳的新網頁有大部分的HTML(畫面)是跟原本網頁相同的，所以占用的頻寬相對的大，載入就會變慢。
#### 使用AJAX :
##### 用了AJAX應用可以僅向伺服器傳送並取回必須的資料(書本的詳細資訊)，並在JavaScript處理來自伺服器的回應。因為在伺服器和瀏覽器之間交換的資料大量減少，伺服器回應更快了。
#### 簡單來說:
#### AJAX意味著可以在不重新載入整個網頁的情況下，對網頁的某部分進行更新。
---
## JQuery使用AJAX
```javascript
$.ajax({
        url: API網址,
        data: {一些要傳的資料..},
        error: function(){載入錯誤回應..},
        method: 使用的方法(預設為get),
		success: function(res){
			...執行動作(e.g.:更新網頁)
		},
	})
```
#### 範例
```javascript
// 資料網址
var cataurl = "https://2017.awiclass.monoame.com/api/demo/shop"

// 存放資料的陣列
var items = []

function downloadList(){
	$.ajax({
		url: cataurl,
		success: function(res){
			console.log(res)
			items = res,
			updateList()
		},
		error: function(){
			console.log("載入失敗")
		}
	})
}
```