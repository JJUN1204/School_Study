## [움직이는 강아지 분양 동적사이트 만들기]
![녹화_2023_07_12_10_53_58_271](https://github.com/JJUN1204/Petshop_web/assets/108847513/672f52d7-2adf-43c0-8a76-02ef5c0a2e41)
****
## [로그인 화면]
![image](https://github.com/JJUN1204/Petshop_web/assets/108847513/d6a8a94e-bfdb-4918-a5a8-11be73003105)
****
## [회원가입 화면]
![image](https://github.com/JJUN1204/Web/assets/108847513/4366ac56-318f-40a4-baa7-08e3606db9c3)
****
### [MENU바 요소들]
```HTML
<header>
<div id='logo'>
	<img src="imgs/pet.png" alt="style size" style="width:320px; height:100px">
</div>

<div id='top'>
	<ul class="main-menu">
		<li><a href="#">강아지종류</a>
		
	<ul class="sub">
		<li><a href="#">골든리트리버</a></li>
		<li><a href="#">포메라니안</a></li>
		<li><a href="#">도베르만</a></li>
		<li><a href="#">웰시코기</a></li>
	</ul>
		</li>
	<li><a href="#">먹이종류</a>
		<ul class="sub">
		<li><a href="#">개껌</a></li>
		<li><a href="#">개사료</a></li>
		<li><a href="#">육포</a></li>
		<li><a href="#">개우유</a></li>
		</ul>
	</li>
	
	<li><a href="#">게시판</a>
		<ul class='sub'>
		<li><a href="#">공지사항</a></li>
		<li><a href="#">오시는길</a></li>
		<li><a href="#">건의사항</a></li>
		<li><a href="#">Q&A</a></li>
		</ul>
	</li>
	
	<li><a href="#">계정 생성</a>
		<ul class="sub">
		<li onclick="winOpen1()"><a href="#">로그인</a></li>
		<li onclick="winOpen2()"><a href="#">회원가입 클릭</a></li>
			</ul>
		</li>
	</ul>
	</div>
	</header>
</div> <!-- 아이디 page의 끝 -->
</body>
</html>
```
****
### [MENU 자바스크립트 코드-1]
```js
$(".main-menu > li").mouseover(function(){ //마우스를 올렸을때 반응함
           $(this).children(".sub").stop().slideDown();
//    $(".sub").stop().slideDown();
});

```
**위 코드는 메뉴바의 요소들 위에 마우스를 올릴 시에는 슬라이드가 내려오는 애니메이션 효과가 나타납니다.**   
**.stop() : 현재 동작하고 있는 애니메이션은 즉시 동작을 중단시킨는 역할을 한다.**
### [MENU 자바스크립트 코드-2]
```js
$(".main-menu > li").mouseover(function(){ //마우스를 올렸을때 반응함
           $(this).children(".sub").stop().slideDown();
//    $(".sub").stop().slideUp();
});

```
**위 코드는 메뉴바의 요소들 위에 마우스를 때었을 시에는 슬라이드가 올라가는 애니메이션 효과가 나타납니다.**   
**.stop() : 현재 동작하고 있는 애니메이션은 즉시 동작을 중단시킨는 역할을 한다.**
****
### [메인 배너 이미지html 코드]
```html
<section>
		<div class='imgs'>
			<img src='imgs/dog1.jpg'>
			<img src='imgs/dog2.jpg'>
			<img src='imgs/dog3.jpg'>
			<img src='imgs/dog4.jpg'>
			<div class="welcome">
				<h2><span>유기견 보호소에 오신것을 환영합니다.</span></h2>
			</div>
		</div>
</section>
```
#### [이미지를 통한 애니메이션 js코드]
```js
start();
var imgs=5;
var now =0;

function start(){
    $(".imgs>img").eq(0).siblings().css({"margin-left":"-2000px"}); //반응형 이미지의 이동
    setInterval(function(){slide();}, 2000);
}

function slide(){ //반응형 이미지의 이동
    now = now == imgs?0:now+=1;
    $(".imgs>img").eq(now-1).css({"margin-left":"-2000px"});
    $(".imgs>img").eq(now).css({"margin-left":"0px"});
}
```
**해당코드는 eq()를 통해 현재 인덱스 번호(now)를 불러와 이미지를 교체해주고**   
**css를 실시간적으로 변화시켜 애니메이션 효과를 주었다.**
****
### [clock.js 코드]
```js
//시간 불러오기
function getTime(){
    let now = new Date();
    timeDiv.textContent = now;
    let year = now.getUTCFullYear();
    let month = now.getMonth();
    let date = now.getDate();
    let hour = now.getHours();
    let min = now.getMinutes();
    let second = now.getSeconds();

    month = month < 10 ? `0${month}` : month;
    date = date < 10 ? `0${date}` : date;
    hour = hour < 10 ? `0${hour}` : hour;
    min = min < 10 ? `0${min}` : min;
    second = second < 10 ? `0${second}` : second;

    todayDiv.textContent = `${year}년 ${month}월 ${date}일`
    timeDiv.textContent = `${hour}시 ${min}분 ${second}초`
}
```
**위의 코드는 현재 시간을 불러와 TEXT 형태로 변환하여 출력한다.**
****
### [로그인,회원가입]
```html
<li><a href="#">계정 생성</a>
		<ul class="sub">
		<li onclick="winOpen1()"><a href="#">로그인</a></li>
		<li onclick="winOpen2()"><a href="#">회원가입 클릭</a></li>
			</ul>
		</li>
	</ul>
```
```js
function winOpen1(){ //로그인
 var win1 = window.open('login.html','child1','toolbar = no, location= no , status = no, menubar = no, resizable = no , scrollbars = no, width = 700, height = 700')
}
function winOpen2(){ //회원가입
 var win2 = window.open('join.html','child2','toolbar = no, location= no , status = no, menubar = no, resizable = no , scrollbars = no, width = 1850, height = 1700')
}
```
**-위 코드는 winOpen()함수를 만들어 로그인바 또는 회원가입바를 눌렀을때 해당 페이지로 이동을 시켜준다.**   
**-window.open ()는 웹브라우저에서 새창(팝업창)을 열기 위해서 가장 간단히 사용할 수 있는 방법이 바로 자바스크립트 window 객체의 open() 함수를 사용하는 것이다.**
