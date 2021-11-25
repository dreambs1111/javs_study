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
