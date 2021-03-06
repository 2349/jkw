---
layout: post
title:  jQuery 이벤트 & 셀렉터 & 메소드 
date:   2013-10-02 08:05:00
category: etc
tags : jquery
---

jQuery 이벤트 & 셀렉터 & 메소드 

{% highlight text %}
이벤트
e.preventDefault() - 대상을 클릭했을때 발생하는 이벤트를 방지(링크 이동 등등 막기)
$(this) - 현재 이벤트가 적용된 개체 (DOM)
.ready(fn); - 페이지 로딩시 fn 실행
.click(fn); - 클릭시 fn 실행
.one(fn); - 딱한번만 이벤트가 실행되고 해제됨
.dblclick(fn) - 더블클릭시 fn실행
.blur(fn) - 포커스를 잃었을때 fn실행
.focus(fn) - 포커스를 얻었을때 fn실행
.toggle(fn1,fn2); - 클릭시 fn1 과 fn2을 번갈아 실행
.scroll(fn) - window 창에서 scroll 이벤트가 발생할때마다 콜백함수 fn 을 실행
.change(fn) - 대상이 바뀌는 지 감지하여 fn을 실행
.keyUp(fn) - 키를 땔때 fn 실행
.keydown(fn) - 키를 누를때fn실행
.keypress(fn) - 연속으로 빨리 keydown이 일어날때 fn실행
.bind({click:fn(){}, mouseover:fn(){}, mouseout:fn(){}}); - 대상에 동적으로 이벤트 바인딩, 이벤트 핸들러 다중 바인딩 가능
.unbind("event") - event 해제
.focusin(fn); - 포커스가 들어왓을때 fn 실행
.focusout(fn); - 포커스가 나갓을때 fn 실행
.select(fn) - 텍스트 필드에서 텍스트를 선택했을때 fn실행
.submit(fn) - 폼제출시 fn실행
.mousedown(fn) - 마우스 버튼를 누를때
.mouseup(fn) - 마우는 버튼을 눌렀다가 땔때
.hover(fn1,fn2) - 마우스오버시 fn1,마우스아웃시 fn2 실행

메소드
.show(시간);
.hide(시간);
.slideUp(시간); - 보이기
.slideDown(시간); - 숨기기
.slideToggle(시간) - 보이고 안보이게 하기
.scrollTop(); - 현재 스크롤바의 위치값
.next(); 다음대상
.prev(); 전 대상
.stop(); - 보통 animate정지에 쓰임
.animate(매개변수,진행시간); - ({"속성":"값"} ,1000) 1초동안 매개변수를 실행
매개변수 - width,height,opacity,fontsize
.attr(속성); - 속성의 값 가져오기
.attr({속성:값, 속성:값}); - 대상의 속성을 값으로 설정
.removeAttr(속성) - 대상의 속성 제거하기
.fadeOut(시간);
.fadeIn(시간);
.fadeTo(시간,투명도); - 대상을 시간동안 투명도를 적용 투명도1~100
.appendTo("대상"); - $("<div><p>Hello,World!</p></div>").appendTo("body");
.append(변수); - $("#result").append(내용); - 대상의 안에 내용추가
$('<br/>').insertAfter(".Content") - .Content 뒤에 <br/> 추가
.insertBefore(); - 앞에 추가
//서브 메뉴를 기준으로 보면 아래와 같음
$('#menu').clone().insertBefore('#submenu');
$('#menu').clone().prependTo('#submenu');
//원래 하단 메뉴가 있는 위치
$('#menu').clone().appendTo('#submenu');
$('#menu').clone().insertAfter('#submenu');
.before(내용) - 대상 앞에 내용 추가
$('h3').wrap('<u></u>') - <h3></h3> 태그를 <u></u>태그로 감쌈
.unwrap(); - 대상을 감싸고있는 부모 엘레멘트를 제거
.clone(); - 대상을 복사
.replaceWith() - 검색된 대상을 변경 ex) $(this).replaceWith("<div>" + $(this).text() + "</div>");
.each(fn) - 대상 수 많큼 반복하여 fn 실행
.size(); - 대상의 개수 알아오기
.html("<input ~>"); - 대상에 html추가
.text("아야어여"); - 대상에 text 추가
.end() - 실행취소함수 바로 전단계의 객체로 돌아감.
.data("link", "messages.jsp"); - 사용법 $(".tab").click(function(){
	window.parent.frames['content'].location = $(this).data("link");
});
.eq(위치); - 대상의 위치번째 요소 셀렉트
.css("background-color","#000000"); - 대상에 스타일을 줌
.removeAttr(속성) - 대상의 속성을 제거
.delay(시간) - 시간만큼 지연
.has(엘레멘트); - 엘레멘트를 가지고 있는 대상만 반환
.contains(엘레멘트1,엘레멘트2) - 엘레멘트1이 엘레멘트2를 포함하고있는지를 boolean 형식으로 반환
.addClass(); - 스타일을 추가
.remove() - 대상 제거
.removeClass(); - 스타일을 제거
.val() - input 의 value값을 가져온다
.addClass("a") - 대상에 a클래스를 추가한다.
.removeClass("a") - 대상에 a클래스를 제거한다.
.get(0).tagName - 대상의 첫번째 요소의 태그이름을 가져옴
.filter(expr) - 지정된 표현식과 매치되지 않는 모든 요소 제거 즉, 매치되는요소만 가져옴
.filter(fn) - 지정된 함수와 매치되지 않는 요소들을 제거
.is(expr) - 대상이 표현식에 해당하면 true 여러 표현식이 있을 경우 한조건만 맞아도 true
.map(callback) - 개체안에 있는 요소들의 집합을 다른 집합으로 변경하여 옮긴다
.not(expr) - 지정된 표현식과 매치디는 모든 요소들을 제거
.slice(n,index) - 왼쪽에서 n번째 문자열 반환 ex) .slice(1,3).addClass('red'); 1번째 인덱스에서 (3-1)번째 인덱스까지
$.trim(문자열) - 양쪽 공백 제거
JQuery.browser.version - 브라우져의 버전
~~~.msie - ie사용시 true
~~~.mozilla - FireFox
~~~.safari
~~~.opera
imgSrc.substr(imgSrc.lastIndexOf("/") + 1); - 순수한 파일명 얻기
msg += $("#select").val().join("|")+'n'; - 셀렉트박스의 값구분자로 구분하여 가져오기
.width() - 대상의 가로길이
.height() - 대상의 세로 길이
.outerWidth(true) - true 마진을 포함한 가로길이
.outerHeight(true) - true 마진을 포함한 세로길이 true제거시 마진 미포함
.trigger("event") - 해당 이벤트를 코드로 강제실행
.load('url',params,callback fn) - Ajax의 기능으로 html을 로드하여 DOM에 삽입
.getJSON('url',fn(data)) - entry[name] 형식으로 json을 읽어옴
- fn내에서 $.each(data,fn(index,entry){table += index + '<br/>'; table+= entry["name"];}; 이런식으로 사용
$.getscript('JQuery.script.js') - 동적으로 자바스크립트 로드, 보통 'JQuery.script.js'에 처리될내용기재하여 클릭이벤트시 실행
$.get('~~.xml',fn()) - XML파일 로드
$.get("~~.aspx", { 'Msg':$(this).val() } ,fn(data){ } ); - get방식의 ajax
$.post("~~.aspx", { 'Msg':'post방식으로 전송'},fn(data){ }); - post방식의 ajax
$.ajax({
	type:"get,post",
	dataType:"json",
	url:"js,aspx,asp,jsp",
	dataType:"script,post,get",
	success:function(data){SuccessFunction(data);},
	error:function(data){AlertFunction(data);}
});
$.ajaxSetup - 반복 사용되는 속성을 상단에 설정하여 코드를 줄인다
({
	url:"~~.asp",
	dataType:"json"
});

기본셀렉터
* : 모든 엘리먼트와 일치
E : 태그명이 E인 모든 엘리먼트와 일치
E F : E의 자손이면서 태그명이 F인 모든 엘리먼트와 일치
E>F : E의 바로 아래 자식이면서 태그명이 F인 모든 엘러먼트와 일치
E+F : E의 형제 엘리먼트로 바로 다음에 나오는 엘리먼트 F와 일치
E~F : E의 형제 엘리먼트로 다음에 나오는 모든 엘리먼트 F와 일치
E:has(F) : 태그명이 F인 자손을 하나 이상 가지는 태그명이 E인 모든 엘리먼트와 일치
E.C : 클래스명 C를 가지는 모든 엘리먼트 E와 일치, E의 생각은 *.C와 동일함
E#I : 아이디가 I인 엘리먼트 E와 일치. E의 생략은 *#I와 동일함
E[A] : 어트리뷰트 A를 가지는 모든 엘리먼트 E와 일치
E[A=V] : 값이 V인 어트리뷰트 A를 가지는 모든 엘리먼트 E와 일치
E[A^=V] : 값이 V로 시작하는 어트리뷰트 A를 가지는 모든 엘리먼트 E와 일치
E[A$=V] : 값이 V로 끝나는 어트리뷰트 A를 가지는 모든 엘리먼트 E와 일치
E[A*=V] : 값에 V를 포함하는 어트리뷰트 A를 가지는 모든 엘리먼트 E와 일치
위치기반 셀렉터
:first : 페이지에서 처음으로 일치하는 엘리먼트. li a:first는 리스트 아이템의 첫번째 링크를 반환함
:last : 페이지에서 마지막으로 일치하는 엘리먼트. li a:last는 리스트 아이템의 마지막 링크를 반환함
:first-child : 첫번째 자식 엘리먼트. li:first-child는 각 리스트의 첫번째 아이템을 반환한다.
:last-child : 마지막 자식 엘리먼트. li:last-child는 각 리스트의 마지막 아이템을 반환한다.
:only-child : 형제가 없는 모든 엘리먼트 반환
:nth-child(n) : n번째 자식 엘리먼트. li:nth-child(2)는 각 리스트의 두번째 리스트 아이템을 반환함
:nth-child(event|odd) : 짝수 또는 홀수 자식 엘리먼트. li:nth-child(event)은 각 목록의 짝수 번째 자식 엘리먼트 반환
:nth-child(Xn + Y) : 전달된 공식에 따른 n번째 자식 엘리먼트. Y는 0인경우 생략가능하다. li:nth-child(3n)은 3의 배수번째 아이템을 반환, li:nth-child(5n+1) 은 5의 배수 +1번째 아이템을 반환
:event / :odd : 페이지 전체의 짝수/홀수 번째 엘리먼트. li:even은 모든 짝수번째 아이템을 반환한다.
:eq(n) : n번째로 일치하는 엘리먼트
:gt(n) : n번째 엘리먼트(포함안됨) 이후의 엘리먼트와 일치
:lt(n) : n번째 엘리먼트(포함안됨) 이전의 엘리먼트와 일치

필터 셀렉터
:animated : 현재 애니메이션이 적용되고 있는 엘리먼트를 선택
:button : 모든 버튼을 선택함(input[type=submit], input[type=reset], input[type=button], button)
:checkbox : 체크박스 엘리먼트만 선택(input[type=checkbox])
:checked : 선택된 체크박스나 라디오 버튼만을 선택
:contains(foo) : 텍스트 foo를 포함하고 있는 엘리먼트만 선택
:disabled : 인터페이스에서 비활성화 상태인 모든 폼 엘리먼트를 선택한다.
:enabled : 인터페이스에서 활성화 상태인 모든 폼 엘리먼트를 선택한다.
:file : 모든 파일 엘리먼트를 선택함(input[type=file])
:header : 헤더 엘리먼트만 선택한다. 예를 들어 <h1>부터 <h6>엘리먼트만 선택한다.
:hidden : 감춰진 엘리먼트만 선택한다.
:image : 폼 이미지를 선택한다.(input[type=image])
:input : 폼 엘리먼트만 선택한다.(input, select, textarea, button)
:not(filter) : 필터의 값을 반대로 변경한다.
:parent : 빈 엘리먼트를 제외하고, 텍스트도 포함해서 자식 엘리먼트를 가지는 엘리먼트를 선택한다.
:password : 패스워드 엘리먼트만 선택한다. (input[type=password])
:radio : 라디오 버튼 엘리먼트만 선택한다.(input[type=radio])
:reset : 리셋 버튼을 선택(input[type=reset], button[type=reset])
:selected : 선택된 엘리먼트만 선택한다.
:submit : 전송 버튼을 선택한다.(button[type=submit], input[type=button])
:text : 텍스트 엘리먼트만 선택(input[type=text])
:visible : 보이는 (visible)엘리먼트만 선택한다.
:empty : 자식 또는 내부 텍스트를 가지지않는 요소들만 선택
:has(selector) : 지정된 셀렉터에 해당하는 요소를 갖는 모든 요소만 선택
[출처] JQuery 이벤트 , 메소드|작성자 지나니
 {% endhighlight %}