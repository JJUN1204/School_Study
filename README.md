# 숫자야구게임
### [숫자로 하는 야구 게임]
## 0.간단한 설명
- 숫자는 1~9까지로 제한
- 서로 다른 숫자 3개로 이루어진 두 개의 배열(com[], usr[])을 비교하여 볼카운트 계산
   **컴퓨터가 내는 숫자는  => 입력받는 인수 VS 컴퓨터가 발생시키는 난수
- 컴퓨터가 내는 숫자 3개의 배열 ==? 사용자가 내는 숫자 3개의 배열
  : 숫자와 배열의 자릿수가 일치할 때는 strike!
   : 숫자는 일치하지만 자릿수가 틀릴 때는 ball!
  ex) 컴퓨터 내는 숫자가 [3][6][9], 사용자가 내는 숫자가 [6][3][9] 이면 strike : 1 & ball:2
- 총 11번의 기회를 제공하며, 3strike 일 경우 게임 종료. 볼카운트를 이용하여 사용자가 숫자를 추측한다.

## 1.인수가 없는 무작위 난수 메소드 생성

``` java
import java.util.*;
import java.io.*;

public class BaseBall
{
public static int playGame() throws IOException //컴퓨터가 3개의 난수를 발생시키는 메소드
{
int x, y, z; //컴퓨터가 선택하는 3개 숫자
Random r= new Random(); //난수발생 Random()메소드로 객체변수 r 생성

x= Math.abs(r.nextInt() % 9) + 1; // 1~9 사이의 난수 발생

do{
y= Math.abs(r.nextInt() % 9) + 1;
}while(y==x); // 만일 난수 y가 x와 같은 수일 때 다시 한 번 난수 발생 반복

do{
z= Math.abs(r.nextInt() % 9) + 1;
}while((z==x)||(z==y)); // 만일 난수 y가 x 혹은 y와 같은 수일 때 다시 한 번 난수 발생 반복

System.out.println(x +", "+ y +", "+ z); //컴퓨터가 발생시킨 난수 확인(게임 시 비공개)

return playGame(x, y, z);
}
```
## 2. 인수가 있는 무작위 난수 메소드 생성 
``` java
public static int playGame(int x, int y, int z) throws IOException
// 인수 3개가 주어지는 메소드
{

int count; //게임을 시도하는 횟수
int strike, ball; // 숫자 매칭에 따른 결과

int[] usr = new int[3]; // 사용자가 입력하는 숫자 3개를 저장하는 배열
int[] com = { x, y, z }; // 컴퓨터가 선택한 숫자 3개를 저장하는 배열

System.out.println("숫자 야구 게임");

count= 0;
```
****
```java
do{

count++;

do{
System.out.println("\n카운트: "+count);

BufferedReader in= new BufferedReader(new InputStreamReader(System.in));
// 콘솔 화면에서 사용자가 입력하는 데이터를 받아들이는 BufferedReader() 메소드의
객체변수 in 생성
String user;//객체변수 in에 들어있는 데이터내용을 문자형데이터로 저장할 변수생성

System.out.print("1번째 숫자: ");
user= in.readLine(); // 사용자가 입력하는 데이터를 변수 user 에 저장
usr[0]= new Integer(user).intValue(); //변수 user에 저장된 데이터를 정수형으로 변환시켜
배열 0번칸에 저장

System.out.print("2번째 숫자: ");
user= in.readLine(); // 사용자가 입력하는 데이터를 변수 user 에 저장
usr[1]= new Integer(user).intValue(); //변수 user에 저장된 데이터를 정수형으로 변환시켜
배열 1번칸에 저장

System.out.print("3번째 숫자: ");

user= in.readLine(); // 사용자가 입력하는 데이터를 변수 user 에 저장
usr[2]= new Integer(user).intValue(); //변수 user에 저장된 데이터를 정수형으로 변환시켜
배열 2번칸에 저장
```
