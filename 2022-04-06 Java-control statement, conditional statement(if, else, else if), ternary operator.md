# Multicampus Java day03
## 2022-04-06

> 제어문
> 조건문: if, else, else if, 삼항연산자

### 1. if, else, else if, 삼항연산자

```java
public static void main(String[] args) {
    System.out.println("Start ...");
    Scanner sc = new Scanner(System.in);
    System.out.println("Input Number: ");
	String num = sc.next();
    int nm = Integer.parseInt(num);
    
    // if문
    if(nm == 0 || (nm > 10 || nm < 1)) {
		System.out.println("Bye");
		sc.close();
		return;
	}
    
    // if, else문
    if(nm%2 == 0) {
		System.out.printf("입력한 값 %d 는 짝수 입니다. \n", nm);
	}else {
		System.out.printf("입력한 값 %d 는 홀수 입니다. \n", nm);
	}
    
    // if, else if, else문
    if(nm >= 7) {
		System.out.println("대");
	}else if(nm >= 3) {
		System.out.println("중");
	}else {
		System.out.println("소");
	}
    
    // 삼항연산자
    String level = "";
	level = (nm >= 7) ? "대" : ((nm >= 3) ? "중" : "소");
	System.out.println(level);
		
	sc.close();
	System.out.println("End ...");
}
```

응용을 위해 Scanner를 써서 정수를 입력받아 조건문을 활용했다.

위 코드들을 조건문 단위로 잘라서 분석해보자.

<br/>

<br/>

#### 1.1 if

```java
if(nm == 0 || (nm > 10 || nm < 1)) {
    System.out.println("Bye");
    sc.close();
    return;
}
```

`if(  )` 괄호 안에는 조건이 들어가 조건이 True라면 {  }대괄호 안의 명령어가 실행된다. if문 안의 조건이 False면 대괄호 안 명령어가 실행되지 않고 스킵된다.

지금 같은 경우는 입력받은 (nm의 값이 0이거나, 10보다 크거나, 1보다 작으면) {Scanner를 닫고 프로그램을 종료한다.} 라는 뜻이다.

<br/>

<br/>

### 1.2 else

``` java
if(nm%2 == 0) {
    System.out.printf("입력한 값 %d 는 짝수 입니다. \n", nm);
}else {
    System.out.printf("입력한 값 %d 는 홀수 입니다. \n", nm);
}
```

만약 `if(  )`안의 조건이 False일 때, else문이 있다면, else문 안에 있는 명령어가 실행된다. 위 코드의 의미를 풀이하자면

(입력받은 nm의 값을 2로 나눈 나머지가 0이 참이라면)

{"짝수 입니다"를 출력한다.}

거짓이라면, {"홀수 입니다"를 출력한다.}

<br/>

<br/>

### 1.3 else if

```java
if(nm >= 7) {
    System.out.println("대");
}else if(nm >= 3) {
    System.out.println("중");
}else {
    System.out.println("소");
}
```

만약 조건이 1개 이상이 있을 때는 else if문을 써야 한다. 위 코드를 풀이하자면

(nm>=7이라면){"대"출력}(nm>=3이라면){"중"출력}앞 조건이 모두 False라면 {"소"출력}

<br/>

<br/>

### 1.4 삼항연산자

```java
level = (nm >= 7) ? "대" : ((nm >= 3) ? "중" : "소");
```

삼항연산자는 if, else if, else를 대신해서 쓸 수 있는 연산자로, 형식은 다음과 같다.

1. 조건이 1개일 때
`(조건)? 함수1 : 함수2`

​		뜻: 조건이 True일 때는 함수1 실행, False라면 함수 2 실행

1. 조건이 2개일 때
  `(조건1)? 함수1 : ((조건2)? 함수2 : 함수3)`

  뜻: 조건1이 True일 때 함수1 실행, False라면 (조건2가 True일 때 함수2 실행, False일 때 함수3 실행)

2. 조건이 3개일 때
  `(조건1)? 함수1 : ((조건2)? 함수2 : ((조건3)? 함수3 : 함수4))`

<br/>

삼항연산자는 if, else if, else문을 대체할 수 있으며, 코드의 라인을 줄일 수 있다.

하지만 삼항연산자는 제 3자가 봤을 때 if, else if, else문보다 보기 불편하고 복잡하므로

보편적으로 if, else if, else문을 많이 쓴다고 한다.
