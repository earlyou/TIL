# Multicampus Java day02
## 2022-04-05

> 변수 타입
>
> 연산자, 연산식, 단항/이항/삼항 연산자
>
> 

<br/>

<br/>

- 변수의 타입, 크기, 범위

| 값의 종류 | 기본 타입 | 메모리 사용 크기 |               저장되는 값의 범위               |
| :-------: | :-------: | :--------------: | :--------------------------------------------: |
|   정수    |   byte    |      1 byte      |        -2<sup>7</sup> ~ 2<sup>7</sup>-1        |
|   정수    |   char    |      2 byte      |              0 ~ 2<sup>16</sup>-1              |
|   정수    |   short   |      2 byte      |      -2<sup>15</sup> ~ -2<sup>-15</sup>-1      |
|   정수    |    int    |      4 byte      |       -2<sup>31</sup> ~ 2<sup>31</sup>-1       |
|   정수    |   long    |      8 byte      |       -2<sup>63</sup> ~ 2<sup>63</sup>-1       |
|   실수    |   float   |      4 byte      |  ±1.4×10<sup>-45</sup> ~ ±3.4×10<sup>38</sup>  |
|   실수    |  double   |      8 byte      | ±4.9×10<sup>-324</sup> ~ ±1.7×10<sup>308</sup> |
|   논리    |  boolean  |      1 byte      |                  true, false                   |

<br/>

- 리터럴(Literal)

   ```java
    int a = 100;
   ```

  - 100이 리터럴이다.

  <br/>
  
- 각 변수들의 선언방법

  - byte
  
  ```java
  byte b1 = 127;		// byte 변수 타입은 -128 ~ 127까지이다.
  ```
  
  <br/>
  
  - char
  
  ```java
  char c1 = 'A';			// char는 문자 1개만 변수로 인정, ''로 문자 지정
  char c1 = 65;			// 'A'를 10진수 유니코드로 표현하면 65
  char c1 = '\u0041';		// 'A'를 16진수 유니코드로 표현하면 '\u004'
  ```
  
  ```java
  char c2 = '\uAC00';		//'가'의 16진수 유니코드
  char c2 = 44032;		//'가'의 10진수 유니코드
  ```
  
  <br/>
  
  - short
  
  ```java
  short s1 = 10000;		// short의 범위는 -32,768 ~ 32,767
  ```
  
  <br/>
  
  - int
  
  ```java
  int i1 = 10;			// 10진수
  int i2 = 012;			// 0이 앞에 있으면 8진수라는 뜻
  int i3 = 0x000A;		// ox가 앞에 있으면 16진수라는 뜻
  ```
  
  <br/>
  
  - long
  
  ```java
  long l1 = 15000000000L;// int 범위를 넘는 숫자를 long으로 선언 할 때 끝에 L을 넣어야 한다.
  ```
  
  <br/>
  
  - float
  
  ```java
  float f1 = 2.5f;		// float에서는 부동소수점 표현을 위해 숫자 끝에 f를 넣는다.
  ```
  
  <br/>
  
  - double
  
  ```java
  double d1 = 2.5;		// double의 부동소수점 선언에는 f가 필요 없다.
  ```
  
  <br/>
  
  - bolean
  
  ```java
  boolean b1 = true;
  boolean b2 = false;			// 조건문에서 많이 쓰인다.
  ```
  
  <br/>
  
  <br/>
  
- 연산자와 연산식

  - 연산자(Operation): 연산에 사용되는 표시나 기호
  - 피연산자(Operand): 연산 대상이 되는 데이터(리터럴, 변수)

| 연산자 종류 |                       연산자                       | 피연산자 수 |  산술값 타입  |          기능 설명           |
| :---------: | :------------------------------------------------: | :---------: | :-----------: | :--------------------------: |
|    산술     |                   +, -, *, /, %                    |    이항     |     숫자      |   사칙연산 및 나머지 계산    |
|    부호     |                        +, -                        |    단항     |     숫자      |      음수와 양수의 부호      |
|   문자열    |                         +                          |    이항     |    문자열     |        두 문자열 연결        |
|    대입     | =, +=, -=, *=, /=, %=, &=, ^=, \|=, <<=, >>=, >>>= |    이항     |     다양      | 우변 값을 좌변의 변수에 대입 |
|    증감     |                       ++, --                       |    단항     |     숫자      |       1만큼 증가/감소        |
|    비교     |         ==, !=, >, <, >=, <=, instance of          |    이항     |    boolean    |        값의 크기 비교        |
|    논리     |                 !, &, \|, &&, \|\|                 | 단항  이항  |    boolean    |   논리적 NOT, AND, OR 연산   |
|    조건     |                  (조건식) ? A : B                  |    삼항     |     다양      |  조건시겡 따라 A or B 선택   |
|    비트     |                    ~, &, \|, ^                     | 단항  이항  | 숫자  boolean | 비트 NOT, AND, OR, XOR 연산  |
|   쉬프트    |                    >>, <<, >>>                     |    이항     |     숫자      |  비트를 좌/우로 밀어서 이동  |

<br/>

  <br/>

- 변수들의 간단한 연산 규칙

  - 소수점이 없는 정수의 연산결과의 변수타입은 항상 `int`이다.

  ```java
  byte b1 = 100;
  byte bb = b1 + b1;			// 오류 발생
  ```
  
  <br/>

  변수 `bb`의 타입을 `byte`로 선언했지만 `b1 + b1`의 변수타입은 `int`이기 때문에 서로 변수타입이 맞지 않아서 오류가 발생한다.
  
  <br/>

  그렇다면 `b1+b1`을 `byte`로 선언하면 어떻게 될까?
  
  ```java
  byte b1 = 100;
  byte bb = (byte)(b1 + b1);		// 결과는 200이 아닌 -56이 나온다
  ```

    <br/>

  우선 `b1 + b1`은 변수타입이 `int`이기 때문에 4 byte로 200이 기록된다.
  
  | <u>0</u> | <u>0</u> | <u>0</u> | <u>0</u> | <u>0</u> | <u>0</u> | <u>0</u> | <u>0</u> | <u>0</u> | <u>0</u> | <u>0</u> | <u>0</u> |  1   | 1    |  0   |  0   |  1   |  0   |  0   |  0   |
  | :------: | :------: | :------: | -------- | :------: | :------: | :------: | :------: | :------: | :------: | :------: | :------: | :--: | ---- | :--: | :--: | :--: | :--: | :--: | :--: |
  
  <br/>
  
  이를 `byte(b1 + b2)`로 변수타입을 `byte`로 바꾸면, `byte`는 1 byte의 크기를 갖기 때문에 4 byte로 기록된 200 중 밑줄친 부분을 삭제하고 1 byte로 줄여버린다.

  |  1   |  1   |  0   |  0   |  1   |  0   |  0   |  0   |
  | :--: | :--: | :--: | :--: | :--: | :--: | :--: | :--: |
  
  <br/>
  
  위 처럼 바뀐 2진수를 10진수로 바꾸면 -56이 되기 때문에 결과는 -56이 나온다!
  
    <br/>
  
  그렇다면 위 식은 어떻게 바꾸는게 좋을까?
  
  <br/>
  
  애초에 `b1 + b1`은 `byte`의 변수 범위를 넘어가기 때문에 `bb`의 변수 선언을 다른 타입으로 해야 한다.

  ```java
  byte b1 = 100;
  int bb = b1 + b1;			// 결과는 200이 나온다.
  ```
  
  <br/>
  
  `b1 + b1`의 결과는 어차피 int로 선언되기 때문에 따로 변수 선언을 하지 않아도 된다.
  
  <br/>
  
  또 `bb`의 변수타입을 `short`나 `long`으로 해도되지만 그렇게 한다면 `(short)(b1 + b2)`로 표현하거나 `(long)(b1 + b2)`로 표현해야 한다. 이렇게 한다면 코딩이 복잡해지고 라인도 길어지기 때문에 **특별한 상황이 아니라면 정수의 변수 선언은 `int`로 선언하는 것이 원칙이다.**
  
  <br/>
  
    <br/>
  
  - 소수점이 있는 실수의 연산결과는 `double`로 선언된다.
  
  ```java
  float dd = 5 + 2.5;				// 오류 발생
  float ff = 5 + 2.5f;			// 결과는 7.5
  double aa = 5 + 2.5;			// 결과는 7.5
  ```
  
  <br/>
  
  실수 끝에 f를 붙히지 않으면 연산 결과는 `double`로 선언되는데 `dd`의 변수타입은 `float`로 선언했기 때문에 오류가 발생한다.
  
    <br/>
  
  실수 끝에 `f`를 넣으면 `float`로 선언되기 때문에 변수 `ff`를 float로 선언해도 오류가 발생하지 않는다.
  
  <br/>
  
  하지만 매번 실수 끝에 `f`를 넣는 것 보다는 변수를 `double`로 선언하는 쪽이 더 용이하기 때문에 **특별한 상황이 아니라면 실수의 변수 선언은 `double`로 하는 것이 원칙이다.**
  
  <br/>

    <br/>
  
  - `int`의 한계를 극복하기 위해 `double` 쓰기

  `int`의 값의 범위가 -2<sup>31</sup> ~ 2<sup>31</sup>-1이기 때문에 이 범위를 넘어가는 매우 큰 정수를 다루기 위해서는 `double`을 써야한다.

  ```java
  double dd = 50000000000000000000000000000000000000.0 + 2.5;
  System.out.println(dd);			// 결과는 5.0E37
  ```
  
  <br/>

  매우 큰 정수 뒤에 .0을 붙히지 않는다면 `int`로 선언되고 값의 범위를 넘어가기 때문에 오류가 발생한다. 하지만 .0을 붙혀준다면 `double`로 선언되기 때문에 매우 큰 정수도 표현이 가능하다.

    <br/>

  정수의 범위가 `int`를 넘지 않는다면 정수 끝에 .0을 붙히지 않아도 연산이 가능하다.
  
  ```java
  double dd = 500 + 2;			
  System.out.println(dd);			// 결과는 502.0
  ```
  
  
  
  
  
  - 

