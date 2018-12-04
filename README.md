# frontend-summary
前端开发常用解决方法

# 设置 rem
```js
  //动态设置字体大小  字体大小 = 基础值 * 要设配的屏幕的宽度 / 设计稿的宽度
  function setHTML() {
    // 基础值
    var baseVal = 100;
    // 设计稿的宽度
    var pageWidth = 375;
    // 要适配的屏幕的宽度?
    var screenWidth = document.querySelector("html").offsetWidth;
    // 要设置的fontsize
    var fontsize = screenWidth * baseVal / pageWidth;
    // 设置到html标签的中
    document.querySelector("html").style.fontSize = fontsize + "px";
  }
```

# 验证手机号码
```js
  function checkPhone(phone) {
    if (!(/^1[34578]\d{9}$/.test(phone))) {
      return false;
    } else {
      return true;
    }
  }
```

# 验证邮箱
```js
  function checkEmail(myemail) {
    // 规则
    var myReg = /^[a-zA-Z0-9_-]+@([a-zA-Z0-9]+\.)+(com|cn|net|org)$/;
    // 判断值是否符合规则
    if (myReg.test(myemail)) {　　　　
      return true;　　
    } else {　　　　
      return false;
    }
  }
```

# 截取字符串中文传参
```js
  //截取字符串中文传参
	function getUrlVal(key) { 
		// 获取参数 
		var url = window.location.search; 
		// 正则筛选地址栏 
		var reg = new RegExp("(^|&)" + key + "=([^&]*)(&|$)"); 
		// 匹配目标参数 
		var result = url.substr(1).match(reg); 
		//返回参数值 
		return result ? decodeURIComponent(result[2]) : null; 
	}
	//id与name
  var ID = getUrlVal("id");
  var Name = getUrlVal("name"); 
  //例子: www.baidu.com/?id=1&name=jack  ---> 1  jack
```

# 获取 url 上的键值对
```js
  function getQueryString(name) {
    var reg = new RegExp("(^|&)" + name + "=([^&]*)(&|$)", "i");
    var r = window.location.search.substr(1).match(reg);
    if (r != null) return decodeURI(r[2]);
    return null;
  }
  // 获取http://baidu.com/id=1 p的值  ---->  getQueryString(p)  输出1
```

# bootstrap 屏幕宽度种类
```js
  function whatScreen() {
    var width = window.screen.width;
    var title = document.querySelector("title");
    if (width <= 768) {
        title.innerHTML = "极小屏幕-" + width;
    } else if (width > 768 && width <= 992) {
        title.innerHTML = "小屏幕-" + width;
    } else if (width > 992 && width <= 1200) {
        title.innerHTML = "普通屏幕-" + width;
    } else if (width > 1200) {
        title.innerHTML = "大屏幕-" + width;
    }
  }
```

# 兼容性滚动条
```js
  function scroll(){
    //移动端滚动兼容
    var scrollTop=document.documentElement.scrollTop || window.pageYOffset || document.body.scrollTop;
  }
```

# 去除空格
```js
  function returnNoSpace(str) {
    return str.replace(/\s+/g, ' ');
  }
```

# 将超出行数的部分 变成 ...
```css
  .line2 {
    display: -webkit-box;
    overflow: hidden;
    white-space: normal!important;
    text-overflow: ellipsis;
    word-wrap: break-word;
    -webkit-line-clamp: 2;
    -webkit-box-orient: vertical
  }
```

# 页面开启摄像头
```html
  <!DOCTYPE html>
  <html lang="en">

  <head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
  </head>

  <body>
    <video src="" width="600" height="600" autoplay controls></video>
    <script>
      var video = document.querySelector("video");

      navigator.getUserMedia({
        video: true
      }, success, error);
      function success(stream) {
        video.src = window.URL.createObjectURL(stream);
      }
      function error(err) {
        console.log(err);

      }
    </script>
  </body>

  </html>
```

# 正在等待效果
```css
  /* 基于 font-awesome 的字体图标 */
  .loadding {
    &::before {
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      height: 100%;
      background-color: #fff;
      opacity: .5;
      content: "";
      z-index: 100;
    }
    &::after {
      font: normal normal normal 14px/1 FontAwesome;
      position: fixed;
      top: 40%;
      left: 50%;
      margin-left: -50px;
      font-size: 100px;
      color: #0094ff;
      content: "\f013";
      z-index: 101;
      animation: fa-spin 1s infinite linear;
    }
  }
```





















