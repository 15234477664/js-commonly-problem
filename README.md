# js-commonly-problem（js工作中常遇到的问题总结）
## 如何判断是否为PC端 还是 移动端
```js
function goPAGE() {
  if((navigator.userAgent.match(/(phone|pad|pod|iPhone|iPod|ios|iPad|Android|Mobile|BlackBerry|IEMobile|MQQBrowser|JUC|Fennec|wOSBrowser|BrowserNG|WebOS|Symbian|Windows Phone)/i))) {
        /*window.location.href="你的手机版地址";*/
        alert("mobile")
  }else {
    /*window.location.href="你的电脑版地址"; */
    alert("pc")
  }
}
goPAGE();
```
## 回到顶部
```js
$(".return_btnbox").click(function(){
    $('body,html').animate({scrollTop:0},500);
});
```
## 判断滚轮向上或向下移动：
移动端：
```js
var windowTop=0;//初始话可视区域距离页面顶端的距离
$(window).scroll(function() {
    var scrolls = $(this).scrollTop();//获取当前可视区域距离页面顶端的距离
    if(scrolls>=windowTop){//表示页面在向下滑动   //需要执行的操作
        windowTop=scrolls;
        console.log("向下滑动")
    }else{//表示页面在向上滑动 //需要执行的操作
        windowTop=scrolls;
        console.log("向上滑动")
    }
});
```
pc端：
```js
方式一：（不兼容火狐）
document.onmousewheel = function(e) {
    e = e || window.event;
    var wheelDelta = e.wheelDelta;
    if (wheelDelta > 0) {
        console.log("鼠标向上滚动");
        console.log(1);
    } else {
        console.warn("鼠标向下滚动");
        console.log(2);
    }
}
方式二：兼容火狐
var agent = navigator.userAgent;
if (/.*Firefox.*/.test(agent)) {
    document.addEventListener("DOMMouseScroll", function(e) {
        e = e || window.event;
        var detail = e.detail;
        if (detail > 0) {
            console.log("鼠标向下滚动");
        } else {
            console.warn("鼠标向上滚动");
        }
    });
} else {
    document.onmousewheel = function(e) {
        e = e || window.event;
        var wheelDelta = e.wheelDelta;
        if (wheelDelta > 0) {
            console.log("鼠标向上滚动");
        } else {
            console.warn("鼠标向下滚动");
        }
    }
}
```
## 一定位置显示
方式一：
```js
$(window).scroll(function(){
    var st = $(this).scrollTop();
    if(st > 100){
        $('.right_bigbox').show();
    }else{
        $('.right_bigbox').hide();
    }
});
```
方式二：
```js
$(window).scroll(function(){
    if ($(window).scrollTop()>200){
        $(".return_btnbox").fadeIn();
    }else{
        $(".return_btnbox").fadeOut();
    }
});
```
## 获取多个input选中状态：
```js
var chk_value =[];
$("input[type='checkbox']:checked").each(function(){
    chk_value.push($(this).val());
});
console.log(chk_value);
```
## 单个input选中
```js
$('input[type='checkbox']:checked'）.val()
```
## 循环获取文本内容
```js
var h3=$("h3.a");
for(i=0,len=h3.length;i<len;i++){

    if($(h3[i]).text()!==""){
        $(h3[i]).before("<em>"+$(h3[i]).text()+"</em>");
        $(h3[i]).remove();
    }
}
```
## js控制页面 
```js
window.history.go(-1);
window.location.href=“”
```
