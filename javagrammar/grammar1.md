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

**메서드 선언 방법**
```
[접근제어자] 리턴타입 메서드명([인자..]) {

}
```
- 접근제어자 : 메서드의 접근 범위를 지정
- 리턴 타입을 반드시 명시해야 하며 리턴이 없는 경우에도 void를 사용

**메서드 오버로딩(Overloading)**
- 리턴값이나 인자가 다른 여러 메서드를 동일한 이름으로 선언하는것

**가변 인자(Variable argumrnts)**
- 인자의 수가 유동적인 메서드
- **String... msg**와 같이 가변인자를 사용

**생성자 메서드(Constructor method)**
- 클래스가 인스턴스될 때 호출되는 메서드
- 클래스 실행시 초기화 작업을 수행
- 메서드 오버로딩에 의해 여러 생성자가 있을 수 있음

**메서드 기본 예제**
```
public class Methods {
    String name;

    // 생성자 메서드
    Methods() {
        name = "홍길동";
        System.out.printf("#생성자: %s\n",name);
    }

    // 인자가 없는 메서드
    void printName() {
        System.out.printf("#printName(): %s\n",name);
    }

    // 인자가 하나인 메서드(메서드 오버로딩), 인자 값이 출력됨.
    void printName(String name) {
        System.out.printf("#printName(String name): %s\n", name);
    }

    // 가변인자를 사용한 메서드
    void printNames(String...name) {
    	System.out.println("#printNames(String...name)");
        for(String s : name) {
            System.out.println(s);
        }
    }

    // 인자가 두개인 메서드
    int calc(int num1, int num2){
        return num1+num2;
    }
    
    public static void main(String[] args) {
    	Methods m = new Methods();
    	m.printName();
    	m.printName("김길동");
    	m.printNames("아무개","홍길동","김사랑");
    	System.out.printf("#calc(int num1, int num2): %d ", m.calc(20,50));
    }
}
```
- 생성자 메서드는 객체가 생성될 때 자동으로 호출
- 동일한 이름의 메서드는 인자에 따라 해당 메서드가 호출됨
- 가변인자를 통해 그때 그때 필요한 인자를 전달 가능
- 리턴이 있는 메서드는 리턴갑을 받아 사용
**실행결과**
```
#생성자: 홍길동
#printName(): 홍길동
#printName(String name): 김길동
#printNames(String...name)
아무개
홍길동
김사랑
#calc(int num1, int num2): 70 
```

> ## Operator
- 다른언어와 같으므로 PASS

> ## 자바 메모리 관리
**JVM**은 시스템(운영체제)로부터 프로그램을 실행하는데 필요한 메모리를 할당받고 JVM은 할당받은 메모리를 용도에 따라 세 영역으로 나누어 관리한다

자바는 C언어와 같이 직접적인 메모리 주소에 접근할 수 없으며 개발자와 메모리를 할당받거나 반환하지 않아도 되는 구조이기 때문에 일반적인 응용 프로그래머의 경우 구체적인 메모리 관리에 대해서는 자세히 알 필요가 없다

다만 프로그램의 동작구조를 보다 정확하게 이해하기 위해서는 다음에 나오는 내용은 알아둘 필요가 있다

### 메서드 영역 (method area)
프로그램 실행 중 특정 클래스가 사용되면, JVM은 해당 클래스의 클래스파일(.class)을 읽어서 분석한 다음 클래스에 대한 정보를 이곳에 저장한다. 이때 **클래스변수**나 **메서드(static)**도 이 영역에 함께 생성

**main()**에서 클래스에 선언된 변수에 접근할 수 없는 것도 이러한 이유로 main()은 staric으로 선언되어 있기 때문에 클래스에 선언된 멤버변수(인스턴스변수)를 사용할 수 없으며 인스턴스의 변수들은 힙 영역에 생성되기 때문에 인스턴스를 통해서만 접근이 가능한 것이다

### 힙 영역 (heap area)
프로그램 실행 중 생성되는 인스턴스는 모두 이곳에 생성된다. 즉, 인스턴스 변수들이 생성되는 공간으로 대부분의 메모리 공간은 힙 영역이 된다.

서버 시스템이나 메모리 사용이 많은 프로그램을 개발하거나 실행시 힙 메모리 부족으로 문제가 발생할 수 있으며 **JVM 메모리 옵션**을 조정해 주어야 한다

### 호출 스택 (call stack or execution stack)
호출 스택은 **메서드 실행**에 필요한 메모리 공간. 메서드 호출시 호출스택에는 호출된 메서드를 위한 메모리가 할당되며 이 메모리는 메서드가 작업을 수행하는 동안 **지역변수 및 매개변수**들의 연산 중간결과 등을 저장하는데 사용된다. 메서드가 작업을 마치면 할당되었던 메모리 공간은 반환되어 정리된다

지역변수들의 경우 멤머변수나 다른 함수에서 사용된 변수들과 이름이 같아도 문제가 없는 이유

### 가비지 컬렉션 (garbage collection)
줄여서 **GC**라고도 한다. 쉽게 말하면 자바에서 사용되지 않는 메모리를 정리해주는 작업.

규모가 크지 않거나 특히 컨테이너기반에서 동작하는 프로그램들의 경우 일반 개발자들이 신경쓸 일이 많지 않고 개발자가 직접 System.gc()를 이용해 가비지 컬렉션을 동작시키는 것은 권장되지 않는다.
