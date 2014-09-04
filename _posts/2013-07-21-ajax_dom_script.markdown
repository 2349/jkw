---
layout: post
title:  Ajax Dom 스크립팅 1page~
date:   2013-07-21 03:05:00
category: book
tags : Ajax Dom 스크립팅

---

<h2>01. DOM의 개요</h2>
<h3>1장 유저 인터페이스</h3>
<p>DOM(Document Object Model)은 프로그램으로 HTML(HyperText Markup Language) 도큐먼트(Document : 문서)의 구조, 스타일(style), 콘텐츠(Content)를 제어하기 위한 방법을 정의한 것이다. 그럼, 이것은 무엇을 위한 것인가? 바로 웹 어플리케이션(Web Application) 사용자를 위한 것이며 유저 인터페이스(User Interface:UI)를 위한 것이다.<br /><a href="http://www.w3.org/DOM/Bindings" target="_blank" title="새창">http://www.w3.org/DOM/Bindings</a></p>

{% highlight html %}
/* 예제1. 소스 Object.html */
<div id="groupOne"><div id="show1"></div></div>
<script language="javascript">
var elementOne = document.getElementById('show1');
var textNode = document.createTextNode('엘리먼트 오브젝트');
elementOne.appendChild(textNode);
</script>
{% endhighlight %}
<div id="groupOne"><div id="show1"></div></div>
<br />
<br />



{% highlight html %}
/* 예제1_2. 소스 domcss.html */
<div id="groupOne">
 <p id="likeSport" style="font-size:20px">좋아하는 스포츠</p>
 <input type="button" onClick="useMethod()" value="스타일 변경" />
</div>

<script language="javascript">
function useMethod(){
 var elementOne = document.getElementById('likeSport');
 elementOne.style.backgroundColor = 'yellow';
 elementOne.style.width ='100px';
}
</script>
{% endhighlight %}
<div id="groupOne">
<p id="likeSport" style="font-size:20px">좋아하는 스포츠</p>
<input type="button" onClick="useMethod()" value="스타일 변경" />
</div>
<br />
<br />



<div id="groupOne">
<input type="text" id="entryName" />
<div id="groupOne"><div id="show2"></div></div>
</div>

<div id="groupOne">
<button id="okClick2" type="button">DOM 지원 체크</button>
<div id="show3"></div>
<div id="show4"></div>
<div id="show5"></div>
</div>

<script>
//예제1
var elementOne = document.getElementById('show1');
var textNode = document.createTextNode('엘리먼트 오브젝트');
elementOne.appendChild(textNode);
//예제2
function useMethod(){
 var elementOne = document.getElementById('likeSport');
 elementOne.style.backgroundColor = 'yellow';
 elementOne.style.width ='100px';
}
//예제3
window.onload = function(){
 var dataElmt = document.getElementById('entryName');
 if (dataElmt.addEventListener){
  dataElmt.addEventListener('keyup', Show.okClick, false);
 } else {
  dataElmt.attachEvent('onkeyup', Show.okClick);
 }
}
var Show = {
 okClick: function(event){
  var entryData = document.getElementById('entryName').value;
  var showOne = document.getElementById('show2');
  if(showOne.hasChildNodes() && showOne.childNodes[0].nodeType == 3){
   showOne.childNodes[0].nodeValue = entryData;
  } else {
   var textNode = document.createTextNode(entryData);
   showOne.appendChild(textNode);
  }
 }
}
//예제4
window.onload = function() {
 var buttonClick = document.getElementById('okClick2');
 if(buttonClick.addEventListener){
  buttonClick.addEventListener('click', Show2.okClick2, false);
 } else {
  buttonClick.attachEvent('onclick', Show2.okClick2);
 }
}

var Show2 = {
 okClick2: function(event){
  document.getElementById('show3').innerHTML = 'DOM 레벨 2 Events 모듈: ' + document.implementation.hasFeature('Events', '2.0');
  document.getElementById('show4').innerHTML = 'DOM 레벨 2 Core 모듈: ' + document.implementation.hasFeature('Core', '2.0');
  document.getElementById('show5').innerHTML = 'DOM 레벨 3 Core 모듈: ' + document.implementation.hasFeature('Core', '3.0');
 }
}
</script>