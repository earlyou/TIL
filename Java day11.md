# Multicampus Java day11

## 2022-04-21

>

<br>

### 1. 다중 인터페이스 구현 클래스

![image](https://user-images.githubusercontent.com/103157377/172505787-cd7c73ab-8089-4114-a03c-f239448916c9.png)

- 인터페이스 2개가 객체의 메소드 호출을 하기 위해서는 두 인터페이스 모두 구현 필요

```java
public class 구현클래스명 implements 인터페이스A, 인터페이스B {
    // 인터페이스 A에 선언된 추상 메소드의 실체 메소드 선언
    // 인터페이스 B에 선언된 추상 메소드의 실체 메소드 선언
}
```



### 2. 예외 처리

#### 2.1 예외와 예외 클래스

- 에러: 컴퓨터 하드웨어의 오동작 또는 고장으로 인한 오류
- 예외: 사용자의 잘못된 조작, 또는 개발자의 잘못된 코딩으로 발생하는 오류
- 보통 에러나 예외가 발생되면 프로그램은 곧바로 종료
- 하지만 예외는 예외 처리(Exception Handling)을 통해 정상 실행 상태 유지 가능
- JVM은 예외가 발생하면 해당 예외 클래스로 객체 생성
- 모든 예외 클래스들은` Java.lang.Exception` 클래스 상속

![image](https://user-images.githubusercontent.com/103157377/172506884-8747c264-c0c3-4648-b473-7011c13c9cbc.png)

![image](https://user-images.githubusercontent.com/103157377/172506942-fccf9537-5902-44f2-b2ce-2363e45de5d5.png)

<br>

#### 2.2 예외 처리 코드

- 예외가 발생했을 때, 프로그램 종료를 막고 정상 실행을 유지할 수 있도록 처리 가능
- 일반 예외는 자바가 컴파일 과정에서 예외 처리 코드 작성을 유도
- 실행 예외는 개발자의 경험으로 예외 처리 코드 작성 필요
- 예외 처리 코드는 `try-catch-finally`블록을 이용

![image](https://user-images.githubusercontent.com/103157377/172507430-f6fd04a5-8a3f-4f0e-b3ab-4fc0f3dd061f.png)

- `try` 블록에서 예외 발생하면 즉시 `catch`블록으로 이동
- `try`블록에서 예외 발생이 없으면 `catch`블록은 생략
- 예외 발생 여부와 상관 없이, `return`문이 있어도  `finally`블록은 항상 실행
- `finally`블록은 생략 가능

<br>

#### 2.3 예외 종류에 따른 처리 코드

##### 2.3.1 다중 `catch`

![image](https://user-images.githubusercontent.com/103157377/172954566-7aac5589-6c34-4a2f-a1e1-ee8f2f839d4f.png)

- `catch`블록이 여러 개 있어도 단 하나의 `catch`블록만 실행
- `try`블록에서 `Exception`이 발생하면 즉시 `catch`블록으로 이동하기 때문

<br>

##### 2.3.2 `catch` 순서

- `catch`블록은 상위 클래스가 하위 클래스보다 아래에 위치할 필요

- 잘못된 예시

  ![image](https://user-images.githubusercontent.com/103157377/172955529-bfd10de1-f148-4ce9-b55b-90dc399f7625.png)

- 옳은 예시

  ![image](https://user-images.githubusercontent.com/103157377/172956803-41f39f1e-90e2-4e30-b352-aa95cd6fd0a8.png)

<br>

##### 2.3.3 멀티 `catch`

- 하나의 `catch`블록에서 여러 `Exception` 처리 가능

![image](https://user-images.githubusercontent.com/103157377/172956734-b2954764-4778-455a-af44-977fbe6c17fa.png)

<br>

#### 2.4 예외 떠넘기기

- `try-catch`블록으로 예외 처리하지 않고, 메소드를 호출한 곳으로 예외 떠넘기기 가능
- `throws`키워드로 예외 떠넘기기

```java
리턴타입 메소드명(매개변수,⋯) throws 예외클래스1, 예외클래스2, ⋯ {
    
}
```

- 발생할 수 있는 Exception 종류별로 `throws`할 수 있지만, `throws Exception`만으로 모든 예외 떠넘기기 가능

```java
리턴타입 메소드명(매개변수,⋯) throws Exception {
    
}
```

