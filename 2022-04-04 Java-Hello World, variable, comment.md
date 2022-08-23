# Multicampus Java day01 - 2
## 2022-04-04

> Hello World
>
> 변수 선언, 명명 규칙
>
> 주석 사용하기



- Hello World
  - `System.out.println("Text");`Text 문자 출력하기


```java
package hello;
public class Hello {
	public static void main(String[] args) {
		System.out.println("Start Application");
		System.out.println("Hello World !!");
		System.out.println("End Application");
	}
}
```

```결과
Start Application
Hello World !!
End Application
```



- 변수 선언

  - day01에는 int만 사용하여 변수 선언해보기

  1. ```java
     package ch02;
     public class Variable1 {
     	public static void main(String[] args) {
     		int a = 2000000000;		// 메모리에 기록됨, int의 최대 길이
     		a = 20;			// int, short, byte로 데이터 길이 정할 수 있다.
     		int MaxSpeed = 200;
     //		int for = 100;		예약어 사용 불가
     		System.out.println("a: "+a);
     		System.out.println("MaxSpeed: "+MaxSpeed);
     	}
     }
     ```

     ```결과
     a: 20
     MaxSpeed: 200
     ```

     

  2. ```java
     package ch01;
     public class Ch01 {
     	public static void main(String[] args) {
     		int a = 10;
     		int b = 20;
     		int result = a * b;			// 정수의 곱셈 연산
     		System.out.println(a);
     		System.out.println(b);
     		System.out.println("result: "+result);
     	}
     }
     ```

     ```결과
     10
     20
     result: 200
     ```

     

  3. ```java
     package ch02;
     public class Variable2 {
     	// class variable: class 전체에 선언한 변수
     	int a = 20;
     	
     	public static void main(String[] args) {
     		// local variable: brace문{}안에서만 쓰이는 변수
     		//int a = 10;
     		int a;		// 초기화 하지 않은 상태에서는 변수 사용X
     		a = 10;		// int a = 10과 같다
     		
     		int result;
     		result = a + 100;		// 오른쪽 결과가 왼쪽으로 입력됨
     		
     		System.out.println(result);
     	}
     }
     ```

     ```결과
     110
     ```

     + 주의사항: local variable은 변수 초기화(int a = 0; 등)가 필요하다.



- 주석 사용하기
  - //
  - Ctrl + /
  - 드래그 + Ctrl + /
  - /*  ~~~~  */

```java
package hello;
public class Hello2 {
	public static void main(String[] args) {
		// 2022-04-04
//		Shin Seung Uk			Ctrl + /
		
		/*
		System.out.println("Start app");
		System.out.println("Start app");
		System.out.println("Start app");
		System.out.println("Start app");
		*/
	}
}
```





