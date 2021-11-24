> # Java program grammar 1
- java는 기본적으로 클래스 구조에서 시작
- 클래스는 객체지향 개념에서 객체를 정의하는 틀로 많은 객체지향 언어의 기본 구조

- 클래스의 기본 구성요소는 **변수**와 **메서드**이다

**자바 프로그램의 기본 구조**
```
// 클래스 선언
public class MyClass {
    // 변수 선언
    int num1;
    Message msg;

    // 메서드
    public void printName(String name) {
        ...
    }

    // 메서드
    public Message getMessage() {
        ...
    }

    // 메인 메서드
    public static void main(String[] args) {
        // 클래스 인스턴스 생성
        MyClass mc = new MyClass();
        ...
    }
}
```

> ## Class
- 객체지향 프로그램의 기본 구조로, 모든 프로그램 소스가 클래스 단위로 시작
	- 프로그램 소스는 **.java**파일이고 컴파일 결과는 **.class**가 된다
	- 일반적으로 클래스 이름과 소스파일명은 동일
	- 대부분의 경우 프로그램은 여러 클래스로 구성되며 실행을 위해서는 main() 메서드가 필요

> ## Instance
- 클래스로부터 생성된 객체로 클래스는 객체를 정의한 틀이고 실제 프로그램은 인스턴스를 통해 동작하게된다
	- main() 메서드는 단지 프로그램을 실행하는 진입점이고 실제 클래스를 사용하려면 new()연산을 통해 인스턴스를 생성해야함
	- main() 에서 클래스부에 선언된 변수(멤버)를 접근할 수 없으며 인스턴스를 통해 사용해야함(인스턴스 변수)
	- 인스턴스에서 변수와 메서드 사용은 인스턴스명.변수명, 인스턴스명.메서드명과 같은 형식으로 사용

> ## Variable
- 일반적인 프로그램언어의 변수와 기본 개념은 같다

> ## Method
- 일반적인 프로그램언어의 함수와 유사
- 함수는 단순히 기능을 모듈화 한것이지만 메서드는 객체의 동작(행위)를 정의

> ## Comment
- 대부분의 프로그램언어와 같은 주석을 지원하며 JavaDoc과 같은 특수한 목적의 주석이 존재
```
// 한줄 주석
/*
    여러줄 주석
*/
/**
    JavaDoc 주석
*/
```
- JavsDoc은 클래스의 API문서를 자동으로 생성해주는 주석
- https://docs.oracle.com/en/java/javase/11/docs/api/index.html에서 볼 수 있는 문서 형태가 JavaDoc으로 생성된 주

> ## Identifier (자바 식별자) 규칙
>> 변수, 상수, 메서드, 클래스 등을 선언시 일반적인 이름 규칙
- 첫 문자가 문자나 \_, $의 특수문자로 시작되야 한다, 숫자는 불가
- 첫 문자가 아니라면 가능
- 자바의 예약어는 식별자로 사용할 수 없음
- 자바의 식별자는 대소문자를 구분
- 식별자 길이는 제한없고 공백은 불가능하다

> ## Coding convention (식별자 생성 관례)
>> 문법적인 제한사항은 아니지만 일반적으로 아래와 같이 생성
- 클래스 이름은 대문자의 명사로 시작
- 메서드 이름은 소문자의 동사
- 변수는 소문자의 명사
- 상수는 대문자의 명사

> ## HelloWorld!
```
public class HelloWorld {
	public static void main(String[] args) {
		System.out.println("Hello World!!");
	}
}
```

> # Variable & Method  

> ## Variable
- 변수는 데이터를 저장하기 위한 메모리 공간에 대한 이름
- 저장할 데이터의 크기를 알아야 필요한 공간을 확보 가능 (적절한 자료형 사용)
- 단, 객체지향 언어에서는 클래스타입을 자료형으로 사용할수 있으며 최근 언어들의 경우 메모리 공간의 크기보다 타입을 구분하는 개념으로 접근
- 타입에 대한 추론을 통해 개발자가 타입에 신경쓰지않고 코딩을 할 수 있도록 지원

- 자바의 경우 **원시자료형(Primitive Type)**, **클래스타입(Class Type)**을 모두 지원하며 원지 자료형에 대한 클래스 타입은 **랩퍼클래스 (Wrapper Class)** 라고 한다

### 원시자료형(Primitive Type)
- 원시자료형은 기본적으로 숫자형 데이터 타입. 정수, 실수, 문자, 논리형이 존재
	- byte 	 : 1bite / 가장 작은단위로 8bit로 구성된 1byte
	- char	 : 2bite / 음수를 포함하지않는 unsigned자료형(문자형에 적합)
	- short	 : 2bite / 음수를 포함한 2바이트 크기의 자료형, 작은 데이터처리에 적합
	- int    : 4bite / 정수의 기본자료형
	- long   : 8bite / 충분한 정수형이 필요한 경우
	- float  : 4bite / 실수형의 기본형이 아니므로, 숫자뒤에 **f**를 붙여서 사용
	- double : 8bite / 실수형의 기본 자료형
	- boolean: 1byte / 논리형으로 참, 거짓을 표현

- 자바에서는 유니코드를 기본으로 지원하기 때문에 문자 처리에 2바이트 필요
- 문자 출력은 유니코드번호에 등록된 문자가 출력되므로 실제 촘ㄱ에 저장되는 값은 유니코드 번호로 숫자값임
- JVM에서 피연산자를 4바이트 단위로 처리하기 때문에 int보다 작은 자료형의 값을 연산하는 경우 자동으로 int로 변환되어 처리
- float형을 지정하기 위해서는 실수값 뒤에 F/f를 붙여야함
- long형으로 처리하기 위해서는 뒤에 L/l을 붙여야 함
= 문자열은 원시자료형이 안니 클래스 타입

```
int num1; // 정수형 변수 
char c1 = 'A'; // 문자형 변수를 선언하고 `A`로 초기화.
long num2 = 212355L; // long 정수형 변수를 선언. 
float num3 = 13.4F; // float 실수형 변수를 선언. 
boolean result = true; // 논리형 변수를 선언하고 true 로 초기화.
```

### 자바 변수 유형
프로그램 코드내에서 변수의 위치에 따라 몇가지 유형으로 변수를 구분
- **멤버변수(Member variable)**
	- 클래스부에 선언된 변수들로 객체의 속성에 해당
	- 인스턴스 변수와 클래스 변수로 구분
- **인스턴스변수(Instance variable)**
	- 클래스가 인스턴스될 때 초기화되는 변수
	- 인스턴스를 통해서만 접근 가능
- **매개변수(parameter)**
	- 메서드에 인자로 전달되는 값을 받기 위한 변수
	- 메서드 내에서는 지역변수처럼 사용
- **지역변수(Local variable)**
	- 메서드 내에서 선언된 변수
	- 멤버변수와 동일한 이름을 가질수 있으며 지역변수가 우선
- **클래스변수(Class variable)**
	- static으로 선언된 변수
	- 인스턴스 생성없이 **클래스이름, 변수명**으로 사용 가능
	- main()메서드에서 참조 가능

**변수 기본 예제**
```
Public class Variables {
	//멤버 변수, 인스턴스 변수
	int num1;

	// 멤버 변수, 클래스 변수
	static int num2;

	// 매개변수
	public void printName(String name) {
		//지역변수
		String prtMsg = name + "Hello";
		System.out.println(prtMsg);
	}
	
	public static void main(String[] args) {
		//인스턴스 생성
		Variables mc = new Variables();
		//인스턴스 변수 사용
		mc.num1 = 100;
		//클래스 변수 사용
		Variables.num2 = 50;	// num2=50으로 사용해도 됨.

		//인자로 매개변수에 값을 전달
		mc.printName("홍길동");

		System.out.printf("%d,%d",mc.num1, Variables.num2);
	}
}

```

- main()에서 Variables 의 인스턴스를 생성하고 참조변수인 mc에 대입. 즉, mc 변수의 타입은 Variables가 됨
- mc.num1 과 같이 인스턴스 변수와 메서드를 사용 가능
- main에서 num1이나 msg변수 printName(), getMessage() 메서드를 직접 호출하는 것은 안됨
- main에서 static변수(클래스변수)인 num2는 가능
**실행결과**
```
홍길동 Hello
100, 50
```

> ## Method
매서드는 특정 객체의 동작이나 행위를 정의한 것으로 클래스의 주요 구성요소

**메서드 선언 반법**
```
[접근제어자] 리턴타입 메서드명([인자..]) {

}
```
- 접근제어자 : 메서드의 접근 범위를 지정
- 리턴 타입을 반드시 명시해야 하며 리턴이 없는 경우에도 void를 사용

