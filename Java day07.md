# Multicampus Java day07

## 2022-04-15

>



### 1. 객체 지향 프로그래밍

- OOAD(Object Oriented Analysis and Design)
  - 1995년 Java 등장 전 까지는 객체지향 개념과 이론만 존재
- OOP(Object Oriented Programming)
  - Java 등장 이후 객체지향 프로그래밍 가능
  - 2000년대 이후 급성장
  - Java Design Pattern 책 추전
    - 헤드퍼스트 디자인 패턴 - 한빛미디어
  - OOP 특징
    - Encapsulation
    - Inheritance
    - Polymorphosm
    - Abstraction

<br>

#### 1.1 객체란?

- 물리적으로 존재하는 것

- 추상적인 것 중에서 자신의 **속성**과 **동작**을 가지는 모든 것

- 객체는 필드(속성)와 메소드(동작)으로 구성

  ![image](https://user-images.githubusercontent.com/103157377/170655464-adeb896e-9bb4-45a3-88eb-49f36719745f.png)

- 객체 모델링(Object Modeling): 현실 객체를 소프트웨ㅐ어 객체로 설계하는 것

<br>

#### 1.2 객체의 상호작용

- 객체들은 독립적으로 존재

- 다른 객체와 상호작용 하면서 동작

- 한 객체가 다른 객체의 기능을 이용하는 것이 **메소드 호출**

  ![image](https://user-images.githubusercontent.com/103157377/170656263-85c49179-72f9-44f7-9923-5e0f6ee77a3f.png)

<br>

#### 1.3 객체 간의 관계

- 대부분의 객체는 다른 객체와 관계를 맺는다.

- 관계의 종류: 집합 관계, 사용 관계, 상속 관계

  ![image](https://user-images.githubusercontent.com/103157377/170656709-0adc2855-7c1a-4b84-9995-a62ee73b8ee8.png)

- 사용 관계: 객체 간의 상호작용. 다른 객체의 메소드 호출하여 원하는 결과 획득

- 상속 관계: 상위 객체를 기반으로 하위 객체를 생성하는 관계

- 집합 관계: 부품 객체

<br>

### 2. 실습

#### 2.1 자동차 객체 생성해보기

##### 2.1.1 Car.java

- project: day07

- package: ch06

- Class: Car.java

  ```java
  package ch06;
  
  public class Car {		// class 만들기
  	// Fields
  	String name;		// Car라는 class의 속성들
  	String color;
  	int size;			// 차 배기량
  	int fsize;			// 기름통 용량
  	int cfsize;			// 현재 기름 양
  	
  	// Constructor, 생성자, 생성자는 반드시 class와 이름이 같아야 한다.
  	public Car() {			// Argument가 다르면 Constructor name은 Car로 같아도 된다.
  		
  	}
  	public Car(String name, String color, int size, int fsize, int cfsize) {
  		this.name = name;
  		this.color = color;
  		this.size = size;
  		this.fsize = fsize;		// fuel size
  		this.cfsize = cfsize;	// current fuel size
  	}
  
  
  	// Methods, 행위, 함수
  	public void go() {	// Car라는 class의 행위, 함수
  		System.out.println("Go!");
  	}
  	public void stop() {
  		System.out.println("Stop!");
  	}
  	public void addFuels(int f) {
  		cfsize += f;
  	}
      
      // toString
  	@Override
  	public String toString() {
  		return "Car [name=" + this.name + ", color=" + color + ", size=" + size + ", fsize=" + this.fsize + ", cfsize=" + this.cfsize
  				+ "]";		// this.name과 name은 같으므로 this가 없어도된다.
  	}
  }
  ```

<br>

##### 2.1.2 App.java

- project: day07

- package: ch06

- Class: App.java

  ```java
  package ch06;
  
  public class App {		// 앱을 위한 프로그래밍에서는 class가 의미가 없다
  
  	public static void main(String[] args) {	// 여기가 애플리케이션 실행 구간
  		Car c1 = new Car();		// 자동차 객체 c1을 하나 만든다
  		String result1 = c1.toString();
  		System.out.println(result1);
  		Car c2 = new Car();
  		System.out.println(c2);
  	}
  }
  ```

- 실행 결과

  ```shell
  Car [name=null, color=null, size=0, fsize=0, cfsize=0]
  Car [name=null, color=null, size=0, fsize=0, cfsize=0]
  ```

  - 객체를 생성만 했기 때문에 속성이 전부 `null`인 것을 알 수 있다.

<br>

##### 2.1.3 App2.java

- project: day07

- package: ch06

- Class: App2.java

  ```java
  package ch06;
  
  public class App2 {
  
  	public static void main(String[] args) {
  		Car c1 = new Car();
  		System.out.println(c1.toString());
  		
  		Car c2 = new Car("K1","red",1000,50,0);
  		System.out.println(c2);
  	}
  }
  ```

- Result

  ```shell
  Car [name=null, color=null, size=0, fsize=0, cfsize=0]
  Car [name=K1, color=red, size=1000, fsize=50, cfsize=0]
  ```

  - c2에는 속성도 지정했기 때문에 속성값이 출력됨을 볼 수 있다.

<br>

#### 2.2 계좌 객체 만들기

##### 2.2.1 UML로 디자인하기

![image](https://user-images.githubusercontent.com/103157377/170664239-b7ba6178-4700-4ea0-a957-85fd4d47fac7.png)