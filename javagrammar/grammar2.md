> # Java program grammar 2
---
- 1. 조건문
- 2. 반복문
- 3. 배열
- 4. 키보드 입력과 로깅
---

> ## 조건문
- if, switch 문이 대표적
#### **if**
```
if(조건식) {
    실행 코드 블럭
}
```
- 수행 조건은 관계연산과 논리연산의 조합으로 설정 가능
- 조건에 따라 처리를 다르게 하기 위해서는 if ~else if 문을 사용

#### **switch**
```
switch(입력 변수) {
    case 조건값: 실행 구문;break;
    ..
    drfault: 기본 실행 구문;
}
```
- 입력 변수는 정수형, 문자 혹은 문자열
- 실행 구문은 별도의 {}없이 구문 나열
- 실행 구문의 마지막에는 반드시 break;을 넣어야 이후 조건의 구문들이 실행되지 않음
- 입력 변수의 값과 매칭되는 경우 수행하는 코드를 지정하는 것으로 복잡한 조건 체크는 한계가 있음

#### **3항연산**
- 간단하게 구현할 수 있는 조건문으로 비교적 간단한 if ~else 구문 처리에 적합
```
조건? true인 경우 수행문장 : false인 경우 수행문장;
String result = (login)? "로그인성공":"로그인실패";
```
- 조건이 true인 경우? 다음에 오는 문장
- 조건이 false인 겅우 오른쪽 문장

**조건문 실습**
```
import java.util.Scanner;

    public class Conditional {
        void login() {
            Scanner scan = new Scanner(System.in);

            System.out.print("## 아이디를 입력하세요: ");		
            String uname = scan.next();

            System.out.print("# 비밀번호를 입력하세요: ");
            String pwd = scan.next();

            if(uname.equals("hong") && pwd.equals("1234")) {
            System.out.println("인증 확인!! -> 로그인 성공");
            }
            else {
            System.out.println("아이디나 비밀번호가 틀렸습니다.!!");
            }
        }

    void check() {
        int cnt = 10;
        String msg = cnt > 0? "새로운 쪽지가 있습니다.!!" : "새로운 쪽지가 없습니다.!!";
        System.out.println(msg);
    }

    public static void main(String[] args) {
        Conditional con = new Conditional();

        while(true) {
            System.out.printf("# 메뉴를 선택하세요 (1:로그인, 2:쪽지확인, x:종료) ==> ");
            Scanner scan = new Scanner(System.in);
            String sel = scan.next();

            switch(sel) {
            case "1": con.login();break;
            case "2": con.check();break;
            case "x": System.exit(0);
            default : System.out.println("잘못된 입력 입니다.!!");
            }	
        }
    }
}

```
- 로그인 메뉴는 아이디와 비밀번호를 입력받고 if 문을 이용해 주어진 값과 맞는지 확인
- 쪽지 확인의 경우 cnt 변수값에 따라 3항연산을 이용해 출력할 메시지를 결정
- x는 프로그램 종료, 이외 값 입력시 잘못된 입력 이라고 출력함
__실행결과__
```
# 메뉴를 선택하세요 (1:로그인, 2:쪽지확인, x:종료) ==> 1
## 아이디를 입력하세요: hong
# 비밀번호를 입력하세요: 23454
아이디나 비밀번호가 틀렸습니다.!!
# 메뉴를 선택하세요 (1:로그인, 2:쪽지확인, x:종료) ==> 1
## 아이디를 입력하세요: hong
# 비밀번호를 입력하세요: 1234
인증 확인!! -> 로그인 성공
# 메뉴를 선택하세요 (1:로그인, 2:쪽지확인, x:종료) ==> 2
새로운 쪽지가 있습니다.!!
# 메뉴를 선택하세요 (1:로그인, 2:쪽지확인, x:종료) ==> x
```

> ## 반복문(Loop statement)
- 특정 코드블럭을 반복하기 위해 사용. for, while이 대표
- 특정 조건에 따라 동일한 작업을 반복해서 수행하기 위한 구문
- 무한루프에 주의하라!

__for기본형__
```
for(초깃값 ; 조건식 ; 증감식) {
    ...
}
```
- 가장 기본적이고 전통적인 형태
- for문의 초깃값, 조건식, 증감식은 생략 가능
- 단, 세미콜론은 있어야 하며 for(;;)는 무한루프가 됨

__for변형__
```
for(변수 : 집합형데이터) {
    ...
}
```
- for-each, 혹은 for-in 형식의 구문
- 배열,Collection과 같은 집합형 데이터 처리에 적합
- 집합형데이터 크기만큼 루프가 돌면서 원소를 변수로 받아 처리

__while기본형__
```
while(조건식) {
    ...
}
```
- 조건식이 참인 경우 반복
- 주로 무한루프에 사용

__do-while__
```
do {
    ...
} while(조건식);
```
- do 코드 블럭이 반드시 한번은 수행되는 구조
- do~while은 잘 사용되지 않음

__반복문 기본 예제__
```
public class Loop {
    public static void main(String[] args) {
        int power = 13; 
        String members[] = {"홍길동","김길동","김사랑","아무개"}; 
        
        // 0 ~ 9 까지 즉 10회 반복 
        for(int i=0;i<10;i++) { 
            System.out.println(i); 
        } 
        
        // 배열의 인덱스를 이용해 데이터 출력 
        for(int i=0;i<10;i++) { 
            System.out.println(members[i]); 
        } // 배열 데이터 크기만큼 반복하면서 String 타입 데이터를 가지고 옴. 
        
        for(String name : members) {
            System.out.println(name);
        } // power > 10 보다 큰 경우에는 go() 함수를 호출해 동작시키고 power를 1감소 
            
        while(power > 10) {
            System.out.println("go"); power--;
        } 
        System.out.println("stop");
    }    
}
```
- for문에 의해 0~9까지 값 출력
- 문자열 배열값을 for-each 형태로 출력
- while 조건값 변경으로 3번 출력후 종료
__실행결과__
```
0 
1 
2
3
..9(생략됨) 
홍길동
김길동
김사랑 
아무개 
go 
go 
go 
stop
```

> ## 배열(Array)
- 특징
    - 가장 __대표적인 자료구조__
    - 순차적으로 저장해 0부터 시작하는 인덱스를 통해 접근 가능
    
- 일반적으로 배열은 선언시 크기가 고정
- 데이터를 순차적으로만 접근할 수 있어 위치를 모르는 경우 효율이 떨어짐
- 배열에 들어가는 데이터는 모두 동일한 자료형이어야 함
- 배열 중간에 값을 추가하려면 기존 데이터를 모두 이동시켜야 함

__배열 선언 및 데이터 사용__
```
int scores[] = {95,100,87,91};
int[] scores = {95,100,87,91};
int[] scores = new int[4];
scores[2] = 90; //3번째 요소(87)을 90으로 변경

System.out.println(scores[0]);
```
- 자바에서 배열선언시 타입[]변수명, 타입 변수명[] 모두 사용 가능
- 배열 선언시 크기를 지정하거나 초기 데이터로 크기가 고정
- 배열원소에 접근은 배열명[인덱스]형식으로 사용
- 인덱스는 0부터
- __배열.length__ 를 통해 배열의 크기를 구할 수 있음

### 배열의 주요 메서드
- 자바에서 배열을 다루기 위한 메서드는 Arrays 클래스에 정의되어 있음
- 따라서 배열관련 처리를 위해서는 Arrays클래스의 메서드를 활용
    - 배열은 크기가 고정되어있고 다루기 불편함
    - 따라서 List등으로 변경해서 처리할 필요가 있음
    - Arrays 클래스의 모든 메서드는 static이므로 인스턴스 생성 없이 사용 가능
    - java.util 패키지 import가 필요
    
##### asList()
- 배열을 ArrayList로 반환해 자바 컬렉션 API를 사용할 수 있다
- 다만 반환되는 ArrayList는 크기가 고정된 타입으로 새롭게 값을 추가할 수 없다
```
String[] cars = {"hyundai", "bmw", "benz", "toyota"};
ArrayList car_list = Arrays.asList(cars);
```

##### toString()
- 

















































