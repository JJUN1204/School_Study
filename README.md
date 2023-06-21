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
**-난수 발생 라이브러리를 통하여 컴퓨터에서 발생한 난수를 배열에 저장**   
**-x= Math.abs(r.nextInt() % 9) + 1 절대값을 이용하여 양수로 치환하고 9로 나누고 1을 더하여 1~9까지의 난수만 발생하게 하였다.**
****
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
**-인수기 있는 랜덤 메소드를 생성**   
**-메소드에 사용되는 다양한 변수 선언**
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
**-BufferedReader in= new BufferedReader(new InputStreamReader(System.in));**   
**-버퍼 리더를 사용해 값을 입력받아 저장하기 위한 객체 in을 선언**
****
## 6.playGame()메소드에서 인수를 받는 메소드
```java
public static void main(String[] args) throws IOException
{
int result; //게임 결과값을 위한 변수 생성

if(args.length==3){ // 게임실행 주어진 3개인 경우, 각각 정수형으로 형변환을 통해 x,y,z 에
저장
int x= Integer.valueOf(args[0]).intValue();
int y= Integer.valueOf(args[1]).intValue();
int z= Integer.valueOf(args[2]).intValue();

result= playGame(x, y, z);
}else{ // 난수발생시키는 경우 즉, playGame()에 해당
result= playGame(); // return 값 즉, 시도횟수(count)를 결과값으로 반환하여 result에 저장
}
```
**-게임실행 주어진 3개의 인수를 각각 정수형으로 형변환을 통해 x,y,z 에 저장해 언제든 불러쓸수 있게함**
****
## 7.리턴 받은 카운터의 값을 통해 데이터 처리
```java
System.out.println();
if(result<=2){
System.out.println("참 잘했어요!"); //시도횟수가 2번 이하
}else if(result<=5){
System.out.println("잘했어요!");//시도횟수가 3번부터 5번 이하
}else if(result<=9){
System.out.println("보통이네요!"); //시도횟수가 6번~9번
}else{
System.out.println("분발하세요!");// 시도횟수가 10번
}
```
**카운터 값을 리턴받아 데이터 처리
  -2회 이하 시도 : 참 잘했어요   
  -5회 이하 시도 : 잘했어요   
  -9회 이하 시도 : 보통이에요   
  -10회이상 : 분발하세요**   
****
## 플레이 화면
**-예외적 상황 2인방**   
![image](https://github.com/JJUN1204/BaseBall_number_game/assets/108847513/5b46687d-ef77-4bdc-abf3-d7e7dde1b852)   
![image](https://github.com/JJUN1204/BaseBall_number_game/assets/108847513/4dfd820f-fba6-4dbf-9813-5775246c6194)   
****


**게임을 실행하면 컴퓨터는 3개의 난수를 발생하였고 사용자에게 3개의 수를 물어봅니다**   
**아래의 이미지와 같이 숫자의 위치는 다르지만 값이 같을경우에는 ball이 추가됩니다.**   
![image](https://github.com/JJUN1204/BaseBall_number_game/assets/108847513/89d05a18-b7cc-4de4-a850-206793f38e5b)   
****
**이번에는 숫자와 위치가 모두 동일하여 strike의 값이 1이 증가했습니다.**   
![image](https://github.com/JJUN1204/BaseBall_number_game/assets/108847513/636f6ca6-4d76-4444-93c8-4bb8dff60f4c)   
****
**모든 숫자를 맞추어 3strike가 되어 잘했다는 문구와 함께 게임이 종료됩니다.**   
![image](https://github.com/JJUN1204/BaseBall_number_game/assets/108847513/0464481c-c0ce-48a5-b6e1-7c9633de2cd7)   
****
**만약 시도횟수가 11번을 넘을시에도 게임은 종료됩니다.**
![image](https://github.com/JJUN1204/BaseBall_number_game/assets/108847513/39271740-611b-4e86-919a-b2ca1693a998)
****
## [generateRandomNumber 함수를 사용한 또 다른 방식의 코드]
```java
import java.util.*;

public class 숫자야구게임 {
    public static void main(String[] args) {
        // 컴퓨터가 생성한 임의의 3자리 숫자
        int[] comNum = generateRandomNumber();

        System.out.println("숫자 야구 게임을 시작합니다!");

        Scanner scanner = new Scanner(System.in);
        while (true) {
            System.out.print("숫자를 입력하세요 (세 자리 수): ");
            String input = scanner.nextLine();

            // 사용자가 입력한 숫자를 정수 배열로 변환
            int[] userNum = ChangeNumArray(input);

            // 입력한 숫자와 컴퓨터의 숫자 비교
            int strikes = countStrikes(comNum, userNum);
            int balls = countBalls(comNum, userNum);

            System.out.println("결과: " + strikes + " 스트라이크, " + balls + " 볼");

            // 정답을 맞춘 경우 게임 종료
            if (strikes == 3) {
                System.out.println("축하합니다! 정답을 맞추셨습니다.");
                break;
            }
        }

        scanner.close();
    }

    // 임의의 3자리 숫자 생성
    private static int[] generateRandomNumber() {
        List<Integer> digits = new ArrayList<>();
        for (int i = 1; i <= 9; i++) {
            digits.add(i);
        }
        Collections.shuffle(digits); //셔플을 하여 리스트를 섞어줌

        int[] number = new int[3];
        for (int i = 0; i < 3; i++) {
            number[i] = digits.get(i);
        }

        return number;
    }

    // 사용자가 입력한 숫자를 정수 배열로 변환
    private static int[] ChangeNumArray(String input) {
        int[] number = new int[3];
        for (int i = 0; i < 3; i++) {
            number[i] = Character.getNumericValue(input.charAt(i));
        }
        return number;
    }

    // 스트라이크 개수 계산
    private static int countStrikes(int[] comNum, int[] userNum) {
        int strikes = 0;
        for (int i = 0; i < 3; i++) {
            if (comNum[i] == userNum[i]) {
                strikes++;
            }
        }
        return strikes;
    }

    // 볼 개수 계산
    private static int countBalls(int[] comNum, int[] userNum) {
        int balls = 0;
        for (int i = 0; i < 3; i++) {
            if (comNum[i] != userNum[i] && contains(comNum, userNum[i])) {
                balls++;
            }
        }
        return balls;
    }

    // 배열에 특정 값이 포함되어 있는지 확인
    private static boolean contains(int[] array, int value) {
        for (int element : array) {
            if (element == value) {
                return true;
            }
        }
        return false;
    }
}
```
**-이 코드는 generateRandomNumber 함수를 사용하여 컴퓨터가 임의로 3자리 숫자를 생성합니다.   
-사용자는 Scanner를 통해 입력한 숫자로 게임에 참여할 수 있습니다.   
-countStrikes 함수는 스트라이크 개수를 계산하고, countBalls 함수는 볼 개수를 계산합니다.      
-이를 위해 contains 함수를 사용하여 배열 내에 특정 값이 포함되어 있는지 확인합니다.   
-게임은 사용자가 3개의 스트라이크를 얻을 때까지 계속됩니다. 정답을 맞추면 게임이 종료됩니다.**
   

