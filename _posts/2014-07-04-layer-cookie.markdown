---
layout: post
title:  오늘 하루 그만보기 스크립트
date:   2014-07-04 12:33:00
category: work
tags : 오늘 하루 그만보기
---


레이어 팝업 용!


{% highlight javascript %}
    function closeLayer(){
        $('.pop_result').hide();
        $('.popBG').hide();
    }

    function filterTime(){

        var now = new Date();
        var nowYear = now.getFullYear();
        var nowMonth = now.getMonth()+1;
        var nowDate = now.getDate();
        var nowHours = now.getHours();
        var nowMinutes = now.getMinutes();
        var nowSeconds = now.getSeconds();
        
        nowMonth = ( nowMonth < 10 ) ? '0'+nowMonth : nowMonth;
        nowDate = ( nowDate < 10 ) ? '0'+nowDate : nowDate;
        nowHours = ( nowHours < 10 ) ? '0'+nowHours : nowHours;
        nowMinutes = ( nowMinutes < 10 ) ? '0'+nowMinutes : nowMinutes;
        nowSeconds = ( nowSeconds < 10 ) ? '0'+nowSeconds : nowSeconds;

        // var nowAll = nowYear + "-" + nowMonth + "-" + nowDate + " " + + nowHours + ":" + nowMinutes + ":" + nowSeconds + " ";
        var nowAll =  '2014-07-05 14:59:59';

        var strStart =  '2014-07-04 14:59:59';

        var year = strStart.substring(0,4);
        var month = strStart.substring(5,7);
        var day = strStart.substring(8,10);
        var hour = strStart.substring(11,13);
        var minute = strStart.substring(14,16);
        var second = strStart.substring(17,19);

        var paseDate = new Date(year, month, day, hour, minute, second);

        var endYear = paseDate.getFullYear();
        var endMonth = paseDate.getMonth();
        var endDay = paseDate.getDate();
        var endHours = paseDate.getHours();
        var endMinutes = paseDate.getMinutes();
        var endSeconds = paseDate.getSeconds();


        endMonth = ( endMonth < 10 ) ? '0'+endMonth : endMonth;
        endDay = ( endDay < 10 ) ? '0'+endDay : endDay;
        endHours = ( endHours < 10 ) ? '0'+endHours : endHours;
        endMinutes = ( endMinutes < 10 ) ? '0'+endMinutes : endMinutes;
        endSeconds = ( endSeconds < 10 ) ? '0'+endSeconds : endSeconds;

        var date1 = endYear + "-" + endMonth + "-" + endDay + " " + + endHours + ":" + endMinutes + ":" + endSeconds + " ";

        if (GetCookie('popCookie') != 'done' && nowAll > date1) {
            document.getElementById('pop_result').style.display = 'block';
            document.getElementById('popBG').style.display = 'block';
        }
    }   
    // popup
    function pop_setcookie(name, value, expiredays) {
        var todayDate = new Date();
        todayDate.setDate(todayDate.getDate() + expiredays);
        document.cookie = name + "=" + escape(value) + "; path=/; expires=" + todayDate.toGMTString() + ";"
    }
    function closeWin() {
        pop_setcookie("popCookie", "done", 30); //popCookie 쿠키명설정
        //document.getElementById('pop_result').style.display = 'none'; //숨길 팝업 ID
    }
    window.onload = function () {
        filterTime();
    }
    function getCookieVal(offset) {
        var endstr = document.cookie.indexOf(";", offset);
        if (endstr == -1) endstr = document.cookie.length;
        return unescape(document.cookie.substring(offset, endstr));
    }
    function GetCookie(name) {
        var arg = name + "=";
        var alen = arg.length;
        var clen = document.cookie.length;
        var i = 0;
        while (i < clen) {
            var j = i + alen;
            if (document.cookie.substring(i, j) == arg)
            return getCookieVal(j);
            i = document.cookie.indexOf(" ", i) + 1;
            if (i == 0) break;
        }
        return null;
    }
    $(document).ready(function(){
        $('#pop_done').click(function(e){
            if($('#pop_done').is(':checked')){
                closeWin();
            }
        });
    });
{% endhighlight %}