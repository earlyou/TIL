# Multicampus Java day04

## 2022-04-11

> [1. switch, case, break, default](#1-switch-case-break-default)
>
> [2. for](#2-for)
>
> [3. while](#3-while)

### 1. switch, case, break, default

- switch문은 if문과 마찬가지로 조건 제어문
- if문과 달리 변수가 어떤 값을 갖느냐에 따라 실행문이 결정되기 때문에 코드가 간결하다.

![image](https://user-images.githubusercontent.com/103157377/168415103-2c16f72d-3bdd-47b1-b6f5-bb6ac502348f.png)

- switch문은 괄호 안의 값과 동일한 값을 갖는 case로 가서 실행문을 실행시킨다.

- 만약 동일한 값을 갖는 case가 없으면 default로 가서 실행문을 실행시킨다.
- default는 생략 가능

- switch문 예제

  ```java
  public static void main(String[] args) {
  		int a = 10;
  		switch (a) {
  		case 10:			// 조건은 들어갈 수 없다. ex) 'a > 10'
  			System.out.println("큰수");
  			break;
  		case 5:
  			System.out.println("중간수");
  			break;
  		case 1:
  			System.out.println("작은수");
  			break;
  		default:
  			System.out.println("입력오류");
  			break;
  		}
  		System.out.println("End .....");
  	}
  // 결과
  큰수
  End .....
  ```

  - case 끝에 break가 있는 이유는 다음 case를 실행하지 말고 switch문을 빠져나가기 위해서다.
  - break가 없으면 다음 case가 연달아 실행되는데, 이 때는 case값과 상관없이 실행된다.

- break문이 없는 case 예제

  ```java
  public static void main(String[] args) {
  		Random r = new Random();	// 난수 발생
  		int n = r.nextInt(3) + 1;	// 0 ~ 2까지 난수 발생 후 + 1
  		System.out.println(n);
  		
  		switch (n) {
  		case 1:
  			System.out.println("냉장고");
  		case 2:
  			System.out.println("세탁기");	// case 사이에 break; 없애버린다면
  		case 3:							// 1등은 냉장고, 세탁기, 핸드폰을 받는다.
  			System.out.println("핸드폰");	// 각각 관리자에게 권한 부여할 때
  			break;						// switch문을 쓴다면 매우 편리하다.
  		default:
  			break;
  		}
  	}
  // 결과
  1		2		3
  냉장고	세탁기	핸드폰
  세탁기	핸드폰
  핸드폰
  ```

- 자바6 까지는 switch문의 괄호에는 (byte, char, short, int, long)변수나 정수값을 산출하는 연산식만 올 수 있었지만, 자바7 부터는 String 타입의 변수도 올 수 있다.

<br/>

### 2. for

- for문은 반복 횟수를 알고 있을 때 주로 사용

![출처: 이것이 자바다](https://user-images.githubusercontent.com/103157377/168414042-a2e1bd01-119a-4a79-814f-6c1496052816.png)

- for문 예제

  ```java
  for (int i = 1; i < 11; i++) {		// i값이 1부터 10까지 1씩 증가할 때 까지 {}안에 있는 명령 반복
  			System.out.println("For ...." + i);	// "For ...." 10번 프린트됨
  		}	// end for
  
  // 결과
  For ....1		For ....6
  For ....2		For ....7
  For ....3		For ....8
  For ....4		For ....9
  For ....5		For ....10
  ```

  - 반복문은 한 번 작성된 실행문을 여러 번 반복 실행해주기 때문에 코드를 절감하고 간결하게 만든다. 

- 반복문에 대한 제어(for) 예제

  ```java
  for (int i = 1; i <= 10; i++) {
      System.out.println("For Loop: "+i);
      if(i == 7) {
          break;
      }
  }
  // 결과
  For Loop: 1		For Loop: 5
  For Loop: 2		For Loop: 6
  For Loop: 3		For Loop: 7
  For Loop: 4
  ```

  - if문을 이용해 for문을 도중에 멈추게 할 수도 있다.

<br/>

### 3. while

- while 문은 조건에 따라 반복할 때 주로 사용
- 조건식이 true일 경우에 계속 반복, false가 되면 반복 멈추고 while문 종료

![출처: 이것이 자바다](https://user-images.githubusercontent.com/103157377/168414659-83553538-4094-47b1-92f7-55666c42509a.png)

- while 예제

  ```java
  int s = 1;
  while(s <= 10) {
      System.out.println("While ...." + s);		// println이 s++의 앞에 있는지 뒤에 있는지에 따라 결과가 다르다
      s++;
  }
  // 결과
  While ....1		While ....6
  While ....2		While ....7
  While ....3		While ....8
  While ....4		While ....9
  While ....5		While ....10
  ```

  - s가 10이하일 때는 while문이 true이기 때문에 s++가 계속 실행된다.
  - s가 10을 초과하면 false가 되어 whie문을 탈출한다.



