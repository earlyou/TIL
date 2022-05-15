# Multicampus Java day05

## 2022-04-12

>[1. for](#1-for)
>
>[2. while](#2-while)
>
>​		[2.1 이중 while문](#21-이중-while문)
>
>​		[2.2 키보드로 while문 제어](#22-키보드로-while문-제어)
>
>[3. 참조 타입(Reference Type)](#3-참조-타입reference-type)
>
>​		[3.1 데이터 타입 분류](#31-데이터-타입-분류)
>
>​		[3.2 String 타입](#32-string-타입)
>
>​		[3.3 배열 타입](#33-배열-타입)
>
>[4. 실습](#4-실습)

### 1. for

- 구구단 출력하기(이중 for문)

  ```java
  public static void main(String[] args) {
      for (int m=2; m<=9; m+) {
      	System.out.printlnC'*** " + m + "단 ***");
          for (int n=1; n<=9; n++) {
              System.out.println(m + " x " + n + " = " + (m치"!));
          }
  	}
  }
  ```

  - for문은 또 다른 for문을 내포할 수 있는데, 이를 중첩된 for문이라고 한다.
  - 바깥쪽 for문이 한 번 실행될 때마다 안쪽 for문은 지정된 횟수만큼 돌다가 다시 바깥쪽 for문으로 돌아간다.

- outter

  ```java
  public static void main(String[] args) {
      outter:
      for(char upper='A'; upper <= 'Z'; upper++) {
          for(char lower='a'; lower <= 'z'; lower++) {
              System.out.println(upper + "-" + lower);
              if(lower == 'g') {
                  break outter;
              }
          }
      }
  }
  ```

  - 만약 반복문이 중첩되어 있을 경우, break문은 가장 가까운 반복문만 종료하고 바깥쪽 반복문은 종료시키지 않는다.

  - 중첩된 반복문에서 바깥쪽 반복문까지 종료시키려면 바깥쪽 반복문에 이름(라벨)을 붙이고, `break 이름;`을 사용하면 된다.

    ![image-20220515112443694](https://user-images.githubusercontent.com/103157377/168468862-7231fb2b-f52f-40df-9089-ad8e958e6fcb.png)

<br/>

### 2. while

#### 2.1 이중 while문

- 좌표 출력하기

  ```java
  public static void main(String[] args) {
      int i = 0;
      while(i < 5) {
          int j = 0;
          while(j < 5) {
              System.out.printf("%d %d\t", i,j);
              j++;
          }
          System.out.println("");
          i++;
      }
  }
  // 결과
  0 0		0 1		0 2		0 3		0 4	
  1 0		1 1		1 2		1 3		1 4	
  2 0		2 1		2 2		2 3		2 4	
  3 0		3 1		3 2		3 3		3 4	
  4 0		4 1		4 2		4 3		4 4	
  ```

<br/>

#### 2.2 키보드로 while문 제어

```java
public static void main(String[] args) throws Exception {
    boolean run = true;
    int speed = 0;
    int keyCode =  0;
    
    while(run) {
        if(keyCode != 13 && keyCode != 10) {
            System.out.println("----------------------");
            System.out.println("1.증속 | 2.감속 | 3.중지");
            System.out.println("----------------------");
            System.out.println("선택: ");
        }
        // 키보드의 키 코드를 읽음
        keyCode = System.in.read();
        
        if(keyCode == 49) {	// 1을 읽었을 경우
            speed++;
            System.out.pirntln("현재 속도 = " + speed);
        }else if(keyCode == 50) {	// 2를 읽었을 경우
            speed--;
            System.out.println("현재 속도 = " + speed);
        }else if(keyCode == 51) {	// 3을 읽었을 경우
            run = false;			// while문을 종료하기 위해 false
        }
    }
}
```

- 예제를 실행하면 키 코드를 입력받기 위해 대기
- Console 뷰에 키드보에서 1, 2를 각각 입력하고 Enter키를 누르면 거기에 맞는 명령 실행
- 실행 후 다시 새로운 키 코드를 입력받기 위해 대기
- 3을 입력하고 Enter를 누르면 `run`이 `false`가 되어 while문이 종료

<br/>

### 3. 참조 타입(Reference Type)

#### 3.1 데이터 타입 분류

![image](https://user-images.githubusercontent.com/103157377/168459321-d03fa9d2-d89f-4913-9693-01afe813ca65.png)

- 자바의 데이터 타입은 크게 기본 타입(primitive type)과 참조 타입(reference type)으로 분류

- 기본 타입: 정수, 실수, 문자, 논리 리터럴을 저장하는 타입

- 참조 타입: 객체의 번지를 참조하는 타입, 배열, 열거, 클래스, 인터페이스 타입

- 참조 타입을 이용해서 선언된 변수는 메모리의 번지를 값으로 갖는다.

  <img src="https://user-images.githubusercontent.com/103157377/168459564-724b963e-b95a-4f80-95fe-ea5d37e7c822.png" alt="image" style="zoom:80%;" />

  ```java
  ［기본 타입 변수］
  int age = 25;
  double price = 100.5;
  
  ［참조 타입 변수］
  String name = "신용권";
  String hobby = "독서";
  ```

  <img src="https://user-images.githubusercontent.com/103157377/168459722-6d3dcaa3-50bc-4fee-8a6c-3a27ea6c6dd4.png" alt="image" style="zoom: 80%;" />

<br/>

#### 3.2 String 타입

- String 변수는 문자열이 직접 변수에 저장되는 것이 아니다.

- 문자열은 String 객체로 생성되고 변수는 String 객체를 참조

  ```java
  String name;
  name = "신용권";
  String hobby = "자바";
  ```

  <img src="https://user-images.githubusercontent.com/103157377/168459904-5fb1a894-3f56-4de3-a152-293a58263a0c.png" alt="image" style="zoom:80%;" />

- indexOf();, substring, trim활용한 예제

  ```java
  // indexOf: 몇 번째 글자인지 알려주는 명령어
  String str = "abcde";
  int c = str.indexOf("c");	// c는 몇 번째 글자?
  System.out.println(c);
  // 결과:2
  
  // substring: 문자열 일부를 추출하는 명령어
  String str2 = str.substring(1, 3);	// 1 ~ 2번째 글자 추출
  System.out.println(str2);
  // 결과:bc
  
  // 메일 id와 domain 추출하기
  String mail = "java@eclipse.com";
  String id = mail.substring(0, mail.indexOf("@"));	// 0번째 글자인 j부터 @ 전까지 추출
  String domain = mail.substring(mail.indexOf("@")+1, mail.indexOf("."));		// @ 이후 부터 .이전 까지 추출
  System.out.printf("%s %s\n", id, domain);
  // 결과:java eclipse
  
  // trim: 공백 없애는 명령어
  String ss = "   abc   ";
  System.out.println(ss.trim());
  // 결과:abc
  ```

<br/>

#### 3.3 배열 타입

##### 3.3.1 배열이란?

- 같은 타입의 데이터를 연속된 공간에 나열하고, 각 데이터에 index를 부여해 놓은 자료구조
- 배열은 선언과 동시에 저장할 수 있는 데이터 타입이 결정
- 다른 타입의 값을 저장하려고 하면 타입 불일치(Type mismatch) 컴파일 오류 발생

<br/>

##### 3.3.2 배열 선언

- 배열 선언의 두 가지 형태

  ```java
  타입[ ] 변수;
  타입 변수[ ];
  ```

- 각 타입별 배열 선언 예시

  ```java
  int[] Array;
  int Array[];
  
  double[] Array;
  double Array[];
  
  String[] Array;
  String Array[];
  ```

- 배열 변수는 힘 영역의 배열 객체를 참조.  참조할 배열 객체가 없다면 null로 초기화 가능

  ```java
  타입[] 변수 = null;
  ```

  - 배열 변수가 null인 상태에서 인덱스로 값을 읽거나 저장하면 NullPointerException 발생

- 예제

  ```java
  public static void main(String[] args) {
      int ar[] = new int[4];
      ar[0] = 10;
      ar[1] = 11;
      ar[2] = 12;
      ar[3] = 13;
      
      // 출력하는 방법
      System.out.println(ar);		// 배열 값이 아닌 인덱스가 출력
      System.out.println(Arrays.toString(ar));	// 배열 값이 String으로 출력
      for(int i = 0; i < ar.length; i++) {
          System.out.println(ar[i]);
      }
  }
  // 결과
  [I@626b2d4a
  [10, 11, 12, 13]
  10
  11
  12
  13
  ```

<br/>

##### 3.3.3 값 목록으로 배열 생성

- 배열 항목에 저장될 값의 목록이 있다면, 간단하게 배열 객체를 만들 수 있다.

  ```java
  데이터타입[] 변수 = {값0, 값1, 값2, 값3, ...};
  ```

  ![image-20220515155732597](https://user-images.githubusercontent.com/103157377/168468851-37dc82f4-0a29-45fb-8191-c45c3d28fcd4.png)

- 중괄호 { }는 주어진 값들을 항목으로 가지는 배열 객체를 힙에 생성하고, 배열 객체의 번지를 리턴

- 예제

  ```java
  public static void main(String[] args) {
      int ar[] = {1,2,3,4,5,6,7,8,9};
     	double sum = 0.0;
      int count = 0;
      
      // 배열의 홀수 번째 값들의 합과 평균
      for(int i = 0; i < ar.length; i++) {
          if(i%2 == 1) {
              sum += ar[i];
              count++;
          }
      }
      System.out.println(sum);
      System.out.println(sum/count);
  }
  // 결과
  20.0
  5.0
  ```

- 주의점

  - 배열 변수를 미리 선언한 후에 다른 실행문에서 중괄호를 사용한 배열 생성은 허용되지 않는다.

    ```java
    int[] ar;
    ar = {0,1,2,3, ...};	// 컴파일 에러
    ```

  - 배열 변수를 미리 선언했다면 다음과 같이 new 연산자를 사용해서 값 목록을 지정

    ```java
    int[] ar = null;
    ar = new int[] {0,1,2,3, ...};
    ```

  - 메소드의 개개값이 배열일 경우에도 마찬가지

    ```java
    int add(int[] scores) {⋯⋯}
    
    int result = add({95, 85, 90});	// 컴파일 에러
    int result = add(new int[] {95, 85, 90});
    ```

<br/>

##### 3.3.4 new 연산자로 배열 생성

- 값의 목록을 가지고 있지 않지만, 향후 값들을 저장할 배열을 미리 만들고 싶을 때, new 연산자로 다음과 같이 배열 객체 생성 가능

- new 연산자로 배열을 생성할 경우에는 이미 배열 변수가 선언된 이후에도 가능

  ```java
  int[] Array = new int[5];
  
  String[] str = null;
  str = new String[5];
  ```

- 타입별 배열의 초기값

| 분류            | 데이터 타입                                             | 초기값                            |
| :-------------- | :------------------------------------------------------ | :-------------------------------- |
| 기본 타입(정수) | byte[ ]<br/>char[ ]<br/>short[ ]<br/>int[ ]<br/>long[ ] | 0<br/>'\u0000'<br/>0<br/>0<br/>0L |
| 기본 타입(실수) | float[ ]<br/>double[ ]                                  | 0.0F<br/>0.0                      |
| 기본 타입(논리) | boolean[ ]                                              | false                             |
| 참조 타입       | 클래스[ ]<br/>인터페이스[ ]                             | null<br/>null                     |

<br/>

##### 3.3.5 다차원 배열

- 행과 열로 구성된 배열을 2차원 배열이라고 한다.

- 자바는 2차원 배열을 중첩 배열 방식으로 구현한다. 예를 들어 2×3 행렬을 만들기 위해 다음과 같은 코드 사용

  ```java
  int[][] scores = new int[2][3];
  ```

  <img src="https://user-images.githubusercontent.com/103157377/168463001-608c1d35-d68b-47f9-983c-e42c5677703e.png" alt="image"  />

  <img src="https://user-images.githubusercontent.com/103157377/168463024-db6a8636-649e-453b-bb07-722260ea4e61.png" alt="image"  />

  ```java
  scores.length		// 2
  scores[0].length	// 3
  scores[1].length	// 3
  ```

- 다차원 배열은 다음과 같이 중괄호 안에 다시 중괄호를 사용해서 값 목록을 나열하면 된다.

  ```java
  int[][] scores = {{95,80},{92,96}};
  ```

<br/>

##### 3.3.6 객체 참조 배열

- 기본 타입 배열은 각 항목에 직접 값을 갖지만, 참조 타입 배열은 각 항목에 객체의 번지를 갖는다.

- 예를 들어 String은 클래스 타입이므로, `String[]`배열은 String 객체의 주소를 갖고있다.

  ```java
  String[] strArray = new String[3];
  strArray[0] = "Java”;
  strArray [1] = "C++"；
  strArray [2] = "C#";
  ```

  ![image](https://user-images.githubusercontent.com/103157377/168468626-79006de0-75ac-4cda-9745-a5704191091f.png)

- `String[]`배열의 항목도 String 변수와 동일 취급

- `String[]`배열 항목 간 문자열 비교 위해서는 `==` 대신 `equals()` 사용

- `==`는 문자열이 아닌 객체 번지를 비교

  ```java
  String[] strArray = new String[3];
  strArray[0] = "Java";
  strArray[1] = "Java";
  strArray[2] = new String("Java");
  
  strArray[0] == strArray[1]	// true(같은 객체)
  strArray[0] == strArray[2]	// false(다른 객체)
  strArray[0].equals(strArray[2])	// true(같은 문자열)
  ```

  ![image](https://user-images.githubusercontent.com/103157377/168468832-acf85d45-d14f-4e96-97fa-73e062cbab5e.png)

<br/>

#### 4. 실습

- `double`형 배열 사이즈 5인 배열을 만들고, 0.0 ~ 10.0 사이의 랜덤 값을 넣고, 값을 출력

  ```java
  public static void main(String[] srgs) {
      double ar[] = new double[5];
      Random r = new Random();
      
      for (int i = 0; i < ar.length; i++) {
          ar[i] = r.nextDouble()*10;
          System.out.println("%.1f|", ar[i]);
      }
  }
  
  // 결과
  1.5|3.8|0.6|7.1|3.6|
  ```

- int형 배열 사이즈 10인 배열을 만들고 1 ~ 99까지 랜덤한 숫자를 입력. 배열의 값이 홀수의 값들만의 합과 평균 출력

  ```java
  public static void main(String[] args) {
      // 1 ~ 99 까지의 랜덤 숫자를 배열에 입력
      for (int i = 0; i < ar.length; i++) {
          ar[i] = r.nextInt(99)+1;
      }
      
      // 배열의 값이 홀수인 값들만 합과 평균
      double sum = 0.0;
      int cnt = 0;
      for (int i = 0; i < ar.length; i++) {
          if(ar[i]%2 == 1) {
              sum += ar[i];
              cnt++;
          }
      }
      
      // 출력
      System.out.println(Arrays.toString(ar));
      System.out.println("sum: %.0f\n", sum);
      System.out.println("avg: %.2f", sum/cnt);
  }
  
  // 결과
  [26, 29, 46, 2, 67, 13, 24, 89, 62, 43]
  sum: 241
  avg: 48.20
  ```

- int형 배열, 사이즈 6인 배열을 만들고 1 ~ 6까지 값을 중복 되지 않게 입력. 배열을 출력

  ```java
  public static void main(String[] args) {
      int ar[] = new int[6];
      Random r = new Random();
      
      for (int i = 0; i < ar.length; i++) {
          ar[i] = r.nextInt(6)+1;
          for (int j = 0; j < i; j++) {
              if(ar[i] == ar[j]) {
                  i--;
                  continue;
              }
          }
      }
      System.out.println(Arrays.toString(ar));
  }
  ```

- 2차원 배열에 3명의 학생들 점수입력, 학생 별 점수를 출력, 전체 점수의 합과 평균 출력

  ```java
  public static void main(String[] args) {
      int ar[][] = {{100,99,80,70},
                    {98,91,83,72},
                    {89,96,82,75}};
      // 학생 별 점수 출력
      for (int i = 0; i < ar.length; i++) {
          System.out,printf("\n%d번 학생 점수: |", i+1);
          for (int j = 0; j < ar[i].length; j++) {
              sum += ar[i][j];
          }
      }
      
      // 전체 점수의 합과 평균
      double sum = 0.0;
      for (int i = 0; i < ar.length; i++) {
          for (int j = 0; j < ar[i].length; j++) {
              sum += ar[i][j];
          }
      }
      System.out.printf("\nsum: %.0f\n", sum);
      System.out.printf("avg: %.2f\n", sum/(ar.length*ar[0].length));
  // 결과
  1번 학생 점수: │100│ 99│ 80│ 70│
  2번 학생 점수: │ 98│ 91│ 83│ 72│
  3번 학생 점수: │ 89│ 96│ 82│ 75│
  sum: 1035
  avg: 86.25
      
      // Option: 학생별 평균을 새로운 배열을 만들어 넣고 출력하시오.
      doublr arr[] = new double[ar.length];
      for (int i = 0; i < arr.length; i++) {
          for (int j = 0; j < ar[0].length; j++) {
              arr[i] = (double) ar[i][j]/(double) ar[0].length;
          }
      }
      System.out.println(Arrays.toString(arr));
  // 결과
  [87.25, 86.0, 85.5]
  }
  ```

  

