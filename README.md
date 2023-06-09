#### [움직이는 강아지 분양 동적사이트 만들기]
![image](https://github.com/JJUN1204/Web/assets/108847513/b8355fef-31a6-4adb-896c-3adc083c770a)
js를 사용해서 움직이는 사이트를 만듬   
### [로그인 화면]
![image](https://github.com/JJUN1204/Web/assets/108847513/af29fe0c-3159-443b-9ebd-a292d637a171)
### [회원가입 화면]
![image](https://github.com/JJUN1204/Web/assets/108847513/4366ac56-318f-40a4-baa7-08e3606db9c3)
### [Main HTML 코드]
```HTML
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<link rel="stylesheet" href="css/style.css" type="text/css">
<script src="https://ajax.googleapis.com/ajax/libs/jquery/1.12.4/jquery.min.js" defer = "defer"></script>
<script src="js/script.js" defer="defer"></script>
</head>

<body>
<div id='page'>
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
<div class='clear'></div> <!-- float 속성 해제 -->
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

<div class='clear'></div> <!-- float 속성 해제 -->

<div class="notice">
	<h2>강아지분양현황</h2>
	<table class="table">
		<tr>
			<th>내용</th>
			<th>날짜</th>
		</tr>
		
		<tr>
			<td><a href="#">골든리트리버 남아(1세)</a></td>
			<td>2022-06-01</td>
		</tr>
		
		<tr>
			<td><a href="#">포메라니안 중성화O(3세)</a></td>
			<td>2022-05-01</td>
		</tr>
		
		<tr>
			<td><a href="#">웰시코기 3개월 여아</a></td>
			<td>2022-10-01</td>
		</tr>
		
		<tr>
			<td><a href="#">도베르만핀셔 남아(1세)</a></td>
			<td>2022-11-01</td>
		</tr>
		
		<tr>
			<td><a href="#">급(공지사항)</a></td>
			<td>2022-12-01</td>
		</tr>
	</table>
</div>

<div class='clear'></div> <!-- float 속성 해제 -->
	<footer>
	<div id='address' align="center">
		<img src='imgs/address.png'>
	</div>
	</footer>
</div> <!-- 아이디 page의 끝 -->
</body>
</html>
```

### [CSS 코드]
```CSS
@charset "UTF-8";
*{
	padding:0;
	margin:0;
}

li{
	list-style: none;
}

.clear{
	clear: both;
}

a{
	color:inherit;
	text-decoration: none;
}

#page{
	width:955px;
	margin: 0 auto;
}
header{
	width:995px;
	height: 120px;
	margin-top: 10p;
	border: solid 1px pink;
}

#logo{
	float:left;
	margin-top: 20px;	
}

#top{
	float: right;
	margin: 20px 20px 0 0;
}

.main-menu{
	width:600px;
	height: 40px;
	margin-top: 10px;
	background-color: #F499C2;
	line-height: 40px;
	color: white;
}

.main-menu li{ /* 학교소개, 학교생활, members */
	float: left;
	width: 150px;
	text-align: center;
}

.main-menu li:hover{
	color: white;
	background-color: maroon;
}

.sub{
	position: absolute;
	width: 150px;
	background-color: #aabbdd;
	display: none;
	z-index: 1;
}

.sub li:hover{
	background-color: #ddbbaa;
}

section{
	width: 995px;
	height: 240px;
	float: left;
	margin-top: 10px;
	align-content: center;
}

.imgs{
	width: 995px;
	height: 220px;
	position: absolute;
	overflow: hidden;
}

.imgs>img{
	position: absolute;
	transition: all 2s;
}

.welcome{
	position: relative;
	text-align: center;
	margin: -35px 0 0 -350px !important;
	width: 750px;
	height: 50px;
	line-height: 50px;
	background-color: yellow;
	border-radius: 30px;
	left: 50%;
	top: 50%;
}

span{
	color:white ;
}

.notice{
	width: 995px;
	margin-top: 10px;
	float: left;
}

h2{
	text-align: center;
}

.table{
	width: 995px;
	border-collapse: collapse;
	font-size: 1rem;
	color: #888;
}

.table tr>th{
	padding: 5px;
}

.table tr>td{
	padding: 5px;
	text-align: center;
}

.table tr:nth-child(2n){
	background-color: #cccccc;
}

footer{
	width: 995px;
	height: 130;
	border-top: solid 1px #cccccc;
	margin-top: 20px;
}

#address{
	margin: 30px 0 0 50px;
}
```
### [JS 풀코드]
```js
$(".main-menu > li").mouseover(function(){
           $(this).children(".sub").stop().slideDown();
//    $(".sub").stop().slideDown();
});
$(".main-menu > li").mouseleave(function(){
            $(this).children(".sub").stop().slideUp();
//    $(".sub").stop().slideUp();
});

start();
var imgs=5;
var now =0;

function start(){
    $(".imgs>img").eq(0).siblings().css({"margin-left":"-2000px"});    
    setInterval(function(){slide();}, 2000);
}

function slide(){
    now = now == imgs?0:now+=1;
    $(".imgs>img").eq(now-1).css({"margin-left":"-2000px"});
    $(".imgs>img").eq(now).css({"margin-left":"0px"});
}

function winOpen1(){
 var win1 = window.open('login.html','child1','toolbar = no, location= no , status = no, menubar = no, resizable = no , scrollbars = no, width = 700, height = 700')
}
function winOpen2(){
 var win2 = window.open('join.html','child2','toolbar = no, location= no , status = no, menubar = no, resizable = no , scrollbars = no, width = 1850, height = 1700')
}
```
### [Login HTML 풀코드]
```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>로그인페이지</title>
</head>
<body>
<form>
		<p> ID : <input type="text" name="username"></p>
		<p> Password : <input type="password" name="password"> </p>
		<p> <input type="submit" value="확인"> &nbsp; <input type='reset' value="취소"> </p>
	</form>
</body>
</html>
```
### [Join HTML 코드]
```
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<title>Insert title here</title>
<style>
	body{
		font-size : 14px;
		font-family : 돋움;
	}
	table {
		width : 800px;
		margin : 0 auto;
	}
	table, tr,th,td{
		border : 1px solid #333;
		border-spacing : 0;
	}
	strong{color : red;}
	caption{
		text-align: right;
	}
	th, td{
		padding : 10px 15px;
	}
	span{color : red;}
	th{text-align : right;}
	#btn{float : right;}
</style>
</head>
<body>
<form action="">
<table>
<caption>(*)표시는<strong>필수입력</strong> 사항입니다.</caption>
<tr>
	<th><span>*</span>회원유형</th>
	<td>학생</td>
</tr>

<tr>
	<th><span>*</span>이름(실명)</th>
	<td>홍길동</td>
</tr>

<tr>
	<th><span>*</span>아이디</th>
	<td><p><input type = "text" size = "20" maxlength = "15"></p>
		<p>6~15자의 영문소문자, 숫자만 가능합니다.</p>
	</td>
</tr>

<tr>
	<th><span>*</span>비밀번호</th>
	<td><p><input type = "password" size = "20"></p>
		<p>비밀번호는 <strong>영대문자, 영소문자, 숫자, 특수문자의 조합</strong>으로 이루어져야합니다.<
			- 조합이 2종류 이상인 경우 10자리 이상,<br>
			- 조합이 3종류 이상인 경우 8자리 이상 가능합니다.,
		</p>
	</td>
</tr>



<tr>
	<th><span>*</span>비밀번호 확인</th>
	<td><p><input type = "password" size = "20"></p></td>
</tr>
<tr>
	<td colspan = "2"><p>학교 홈페이지에 가입하시겠습니다?<span id = "btn"><input type = "submit" value = "확인">
	&nbsp;<input type = "reset" value = "취소">
	</span></p></td>
</tr>

</table>
</form>
</body>
</html>
```
