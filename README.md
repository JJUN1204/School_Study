# JSP_FIRST_STEP
## <JSP웹 페이지 구성 요소>
### <%@ 무언가의 내용 %> : 지시 문, JavaScript 페이지 속성 지정

### <%-- 주석 내용 --%> : 주석 문

### <jsp:액션 속성> </jsp:액션 속성> : 액션 태그, 
  다른 페이지 포함(include),  
  다른 페이지 이동(forward)   

### <%  무언가의 내용  %> : 가장 일반적인 형식, 
스크립트릿,   
자바 코드를 묶는 블록,    
변수 선언 시 이용, 지역 변수   

### <%!  전역 변수, 메서드 선언  %> : 선언 문

### <%=  웹 브라우저에 출력하고자 하는 값  %> : 표현 식
****

전역변수 VS 지역변수   
![image](https://github.com/JJUN1204/JSP_FIRST_STEP/assets/108847513/3fa055cd-29ca-4d94-afca-e2dcc17fc8e5)   
### <JSP의 코딩 영역 >   
#### <%! 선언부 %>
**: 변수 및 함수 등을 선언하는 영역(거의 사용되지 않는다)**   
**변수: 전역변수(문서 내 어느 곳에서든 호출 가능하다, 선언된 부분 상단에서도 사용 가능)**   
**함수: jsp에서는 거의 만들지 않는다. java에서 만든 파일을 import해서 사용한다.**  
****
#### <% 스크립릿 %>   
**: 코딩 영역(처리식 등) -> 함수 생성 불가. 호출만 가능.**   
**변수는 지역변수: 선언한 이후에만 사용 가능하다.**   
**이 안에서 출력을 하려면 out.print() 명령 사용**   
### <출력화면>   
![image](https://github.com/JJUN1204/JSP_FIRST_STEP/assets/108847513/d06ab2b9-fc45-47b4-9191-99c8ecaceb5a)   
#### <%= 출력부 %>
**: 문자열, 변수값, 함수 리턴값 등등 출력**   
**마감표시 ';'사용 없다. 한 줄만 출력할 수 있다.**   
**출력부를 사용하여 웹 화면에 띄울 수 있다.**
****
## <jsp에서 배열 선언하기>
### * 1차원 배열 선언
- 데이터 형[ ] 배열 명;
- 데이터 형 배열 명[ ];

### - 1차원 배열 생성
- 배열 명 = new 데이터 형[배열 크기];

### - 1차원 배열 선언과 생성을 동시에
- 데이터 형[ ] 배열 명 = new 데이터 형[배열 크기];
- 데이터 형 배열 명[ ] = new 데이터 형[배열 크기];

###  <연습 문제>
3과목 국, 영, 수 의 점수(90, 80, 70)와 과목명을 각각 1차원 배열로 정의하고
총점과 평균을 구하는 성적처리 프로그램을 jsp로 구현하시오.   
<details>
<summary>코드</summary>
  
  ```jsp
<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
<!DOCTYPE html>
<html>
<head>
<style>
b{
margin : 100px;
}
</style>
<meta charset="UTF-8">
<title>Insert title here</title>
</head>
<body>
<%
	String [] subject = {"국어","영어","수학"};
	int [] score = {90,80,70};
	int total = 0;
	float avg = 0;
	
	for(int i = 0; i < subject.length; i++){
		total += score[i];
	}
	
	avg = total / 3;


%>

<b>국어 : </b><%=score[0] %><br>
<b>영어 : </b><%=score[1] %><br>
<b>수학 : </b><%=score[2] %><br>
<b>점 : </b><%=total %><br>
<b>평균 : </b><%=avg %><br>




</body>
</html>
  
  ```
</details>

****
## 2차원 배열 생성

### 데이터 형[ ][ ] 배열 명 = new 데이터 형[행 원소 수][열 원소 수];
### 데이터 형 배열 명[ ][ ] = new 데이터 형[행 원소 수][열 원소 수];

### ex) int jumsu[][] = new int[2][3];
      int jumsu[][] = {{80,90,70}, {50, 80, 70}};

| 80 | 90 | 70 |
| --- | --- | --- |
| 50 | 25 | 30 |

### <2차원 배열을 이용한 성적 처리 프로그램>
학생 2명(김미영, 김민성)의 국, 영, 수 3과목의 점수를 2차원 배열로 정의하고,
학생별 총점과 평균을 구하시오.

<details>
  <summary>코드</summary>
  
  ```jsp
    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>2차원 배열을 이용한 성적 처리 프로그램</title>
    </head>
    <body>
    	<%!
    		int[][] score = {{80,90,70}, {50, 25, 30}};
    		String[] subject = {"국어", "영어", "수학"};
    		String[] name = {"김미영", "김민성"};
    	%>
    	<h2>2차원 배열을 이용한 성적 처리 프로그램</h2>
    	<b>
    		<%
    			int sum = 0;
    			float avg = 0;
    			
    			for(int i = 0;i<score.length;i++){
    	            for(int j = 0;j<3;j++){
    	                out.print(name[i] +"의 "+ subject[j] +"점수 : " + score[i][j] + "점<br>");
    	            }
    	            for(int j : score[i]){
    	            	sum += j;
    	            }
    	            avg = sum/score[i].length;
    	            
    	            out.print(name[i] + "의 총점 : " + sum + "점<br>");
    	            out.print(name[i] + "의 평균 : " + avg + "점<br><br>");
    	            sum=0;
    			}
    		%>
    	</b>
    </body>
    </html>
```
    
</details>

## 조건문을 활용한 연습 문제

---

### <대학에서 학년 별로 영문 호칭을 판정하는 프로그램>
**switch case 문으로 구현 하고, 학년 구간을 벗어난 경우에는
’학년오류‘ 라는 메세지를 출력하시오**

**1 → fresh man**
**2 → sophomore**
**3 → junior**
**4 → senior**
**1~4 이외의 값들은 : 학년오류**

**출력 내용 : 대학의 N학년은 <영문명>입니다.**


<details>
  <summary>코드</summary>
  
    ```jsx
    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>대학에서 학년 별로 영문 호칭을 판정하는 프로그램</title>
    </head>
    <body>
    <%
    	int year = 1;
    	String msg = null;
    	switch(year){
    		case 1 :  msg = "fresh man";
    			break;
    		case 2 : msg = "sophomore";
    			break;
    		case 3 : msg = "junior";
    			break;
    		case 4 : msg = "senior";
    			break;
    		default : msg = "학년오류";
    			break;
    	}
    %>
    <b>대학의 <%= year %>학년은 <%= msg %> 입니다.</b>
    </body>
    </html>
    ```
</details>
    
  
### <if문을 이용한 회원가입 프로그램>
1) 사용자의 아이디가 일치한 후, 비밀번호까지 일치하면
⇒ 방문을 환영합니다.
2) 사용자의 아이디가 일치한 후, 비밀번호까지 일치하지 않으면
⇒ 비밀번호가 틀립니다.
3) 사용자의 아이디가 일치하지 않으면,
⇒ 회원 가입을 해주세요.
하는 메시지를 출력하시오.
**사용자 아이디 “abc” 비밀번호 “1234”**
**로그인 입력 아이디와 비밀번호는 변수로 지정하시오.**

#### 출력 내용 : 
#### 사용자 ID : <결과>, 사용자 Password : <결과>
#### 로그인 ID : <결과>, 로그인 Password : <결과>
#### 로그인 메시지 : <결과>

<details>
  <summary>코드</summary>
    ```jsx
    <%@ page language="java" contentType="text/html; charset=UTF-8"
        pageEncoding="UTF-8"%>
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="UTF-8">
    <title>if문을 이용한 회원가입 프로그램</title>
    </head>
    <body>
    <h3>로그인 확인</h3>
    <%!
    	String id = "abc";
    	String password = "1234"; 
    %>
    <%
    	String userId = "abc";
    	String userPassword = "1234";
    	String result = null;
    	
    	if(userId != id){
    		result = "회원 가입을 해주세요";
    	} else if(userPassword != password){
    		result = "비밀번호가 틀립니다.";
    	} else{
    		result = "방문을 환영합니다.";
    	}
    %>
    <b>사용자 ID : <%= userId %>, 사용자 Password : <%= userPassword %></b> <br>
    <b>로그인 ID : <%= id %>, 로그인 Password : <%= password %></b> <br>
    <b>로그인 메시지 : <%= result %></b>
    </body>
    </html>
    ```
</details>
    
  


