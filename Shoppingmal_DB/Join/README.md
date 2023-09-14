## 회원가입 페이지 구현
![image](https://github.com/JJUN1204/School_Study/assets/108847513/357983be-c682-4082-a937-451555fa8355)<br/>
**-Wepapp 폴더 안에 join.jsp 파일과 join_p.jsp 파일을 생성한다.**
****
## 주요코드
``` jsp
<%@ page import ="DB.DBConnect" %> <%-- 지시문형식을 통해 DB연결 자바파일 불러오기  --%>
<%@ page import = "java.sql.*" %>  <!-- 지시문형식을 통해 SQL 관련 라이브러리 불러오기  -->

<%@ page language="java" contentType="text/html; charset=UTF-8"
    pageEncoding="UTF-8"%>
 
 <%
        String sql = "select max(custno) from member_tbl_02"; // 쿼리문 형식의 문자열이 변수명 sql에 저장
 
        Connection conn = DBConnect.getConnection(); // DB 연결 기능을 객체변수 conn 에 저장 -> 1.DB연결
        PreparedStatement pstmt = conn.prepareStatement(sql);  // sql변수에 저장되어 있는 문장이 쿼리문이 됨 ->2.DB연결 후 쿼리문이 생성\
        ResultSet rs = pstmt.executeQuery(); // 변수pstmt에 저장되어있는 SQL문을 실행하여 객체변수 rs에 저장
        rs.next(); //변수 rs에 결과값이 저장되는 경우 next()를 호출하여 마지막 값을 확인
        
        int num = rs.getInt(1) + 1; //num에는 오라클 member 테이블의 마지막 회원번호 + 1 값이 정수로 저장
 %>
```

-**스크립트릿<% %>에서 DB연결 및 SQL문을 실행하여 num에 값을 불러오는 코드**

![image](https://github.com/JJUN1204/School_Study/assets/108847513/7bd7d39c-8865-4a15-83ea-4b69b6e10b87)   
****
**-등록 버튼을 누를시에 join_p.jsp를 통해 입력 값을 받아 DB에 저장한다.**
## 주요코드
``` jsp
 <%
        request.setCharacterEncoding("UTF-8");
        String sql = "insert into member_tbl_02 values(?, ?, ?, ?, ?, ?, ?)";
        
        Connection conn = DBConnect.getConnection();
        PreparedStatement ps = conn.prepareStatement(sql);
        
        ps.setInt(1, Integer.parseInt(request.getParameter("custno")));
        
        
        ps.setString(2, request.getParameter("custname"));
        ps.setString(3, request.getParameter("phone"));
        ps.setString(4, request.getParameter("address"));
        ps.setString(5, request.getParameter("joindate"));
        ps.setString(6, request.getParameter("grade"));
        ps.setString(7, request.getParameter("city"));
        
        
        ps.executeQuery();
        
    %>
```




