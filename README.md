# JSP_Second_STEP
## 회원가입 웹 페이지를 만들어서 정보를 jsp 파일에 전달하기
## 주요 메소드
**-request: 내장 객체는 클라이언트가 요청하는 http 정보 저장**   
**-getParameter(String name): 해당 name 속성의 파라미터 값 리턴**      
**-getParameterValues(String name): 해당 name 속성의 파라미터의 모든 값(복수) 리턴**
## 회원가입 화면
![image](https://github.com/JJUN1204/JSP_Second_STEP/assets/108847513/4079d78e-2bcc-4e75-ad10-7c97ae3d9209)   
**-전송 버튼을 눌러서  jsp서버에 데이터를 전송하거나 취소버튼을 눌러 취소할 수 있습니다.**
## 전송 화면
![image](https://github.com/JJUN1204/JSP_Second_STEP/assets/108847513/8710b26a-3ad6-4a36-a9ff-49fb6689a68e)   
**전송버튼을 눌러 jsp서버에 잘 저장된 것을 보실 수 있습니다.**
## jsp 코드
![image](https://github.com/JJUN1204/JSP_Second_STEP/assets/108847513/ffb8cda4-39c0-499a-82f2-dd36f4dfce22)   
**-아이디,비밀번호,이름,성별은 하나의 데이터만 저장하기 때문에 request.getParameter()를 사용하여 입력한 값의 데이터를 불러온다.**   
![image](https://github.com/JJUN1204/JSP_Second_STEP/assets/108847513/f945555f-8b4c-4ad7-be6d-1a79d2c3ae49)   
**-하지만 취미는 여려개를 선택하여 여러개의 데이터가 들어오기 때문에 배열을 선언한뒤,   
request.getParameterValues()를 통해 value 값을 for문으로 반복하여 저장한다**




