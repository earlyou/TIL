# Multicampus Java day07

## 2022-04-15

>[1. 객체 지향 프로그래밍](#1-객체-지향-프로그래밍)
>
>​	[1.1 객체란?](#11-객체란)
>
>​	[1.2 객체의 상호작용](#12-객체의-상호작용)
>
>​	[1.3 객체 간의 관계](#13-객체-간의-관계)
>
>[2. 객체 지향 프로그래밍의 특징](#2-객체-지향-프로그래밍의-특징)
>
>​	[2.1 캡슐화(Encapsulation)](#21-캡슐화encapsulation)
>
>[3. 실습](#3-실습)
>
>​	[3.1 자동차 객체 생성](#31-자동차-객체-생성)
>
>​	[3.2 계좌 객체의 Encapsulation](#32-계좌-객체의-encapsulation)
>
>​	[3.3 움직이는 자동차 객체](#33-움직이는-자동차-객체)



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

### 2. 객체 지향 프로그래밍의 특징

#### 2.1 캡슐화(Encapsulation)

- 객체의 필드, 메소드를 하나로 묶고, 실제 구현 내용을 감추는 것

- 외부 객체가 객체 내부의 구조를 알지 못하게 하는 것

  ![image](https://user-images.githubusercontent.com/103157377/170705436-277b30f5-b8a7-44bf-818a-e02326103f68.png)

- 외부의 잘못된 사용으로 객체가 손상되지 않도록 하기 위해 사용

- 캡슐화를 위해 접근 제한자(Access Modifier)를 사용

<br>

### 3. 실습

#### 3.1 자동차 객체 생성

##### 3.1.1 Car.java

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

##### 3.1.2 App.java

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

##### 3.1.3 App2.java

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

#### 3.2 계좌 객체의 Encapsulation

##### 3.2.1 UML로 디자인하기

![image](https://user-images.githubusercontent.com/103157377/170705807-05c45263-9b8e-4d2b-9a46-394090570f85.png)

##### 3.2.2 Account.java

- project: day07

- package: ch06

- Class: Account.java

  ```java
  package ch06;
  
  public class Account {
  	// Attribution
  	private String accNo;			// Attribution에 대해서 자유로운 접근을 막아야 한다
  	private double balance;			// private를 통해 객체를 Encapsulation
  	
  	// Constructor
  	public Account() {
  	}
  	public Account(String accNo) {
  		this.accNo = accNo;
  	}
  	public Account(String accNo, double balance) {
  		this.accNo = accNo;
  		this.balance = balance;
  	}
  	public String getAccNo() {
  		return accNo;
  	}
  	public double getBalance() {
  		return balance;
  	}
  
  	// Operation
  	// 출금 금액이 1보다 작으면 안된다.
  	// 출금 금액이 잔액보다 많으면 안된다.
  	public void deposit(double money) {
  		if(money < 1) {
  			System.out.println("입금 금액 오류");
  			return;
  		}
  		this.balance += money;
  	}
  	public void withdraw(double money) {
  		if(money < 1) {
  			System.out.println("출금 금액 오류");
  			return;
  		}
  		if(this.balance < money) {				// this.balance말고 balance로 해도됨
  			System.out.println("잔액 부족 오류");
  			return;
  		}
  		this.balance -= money;
  	}
  	public double select() {					// return type = double
  		return this.balance;
  	}
  
  	// toString
  	@Override
  	public String toString() {
  		return "Account [accNo=" + accNo + ", balance=" + balance + "]";
  	}
  }
  
  ```

<br>

##### 3.2.3 BankApp.java

- project: day07

- package: ch06

- Class: BankApp.java

  ```java
  package ch06;
  
  public class BankApp {
  
  	public static void main(String[] args) {
  		Account acc1 = new Account("1111-2222");	// Constructor
  		System.out.println(acc1.toString());
  		
  		acc1.deposit(10000);						// acc1주소의 deposit에 10000원을 넣어라
  		System.out.println(acc1.toString());		// deposit은 void형 함수이기 때문에 계산만 한다
  		
  //		acc1.balance = 500000000000.0;				// Encapsulation을 통해 Attribution변경을 못하게 막음
  
  		acc1.withdraw(500);
  		System.out.println(acc1);
  		
  		String accNo = acc1.getAccNo();
  		double balance = acc1.getBalance();
  		System.out.printf("계좌정보: %s %.2f\n",accNo.toString(),balance);
  		acc1.select();
  	}
  }
  ```

- Result

  ```shell
  Account [accNo=1111-2222, balance=0.0]
  Account [accNo=1111-2222, balance=10000.0]
  Account [accNo=1111-2222, balance=9500.0]
  계좌정보: 1111-2222 9500.00
  ```

<br>

#### 3.3 움직이는 자동차 객체

##### 3.3.1 UML로 디자인하기

![image](https://user-images.githubusercontent.com/103157377/170708032-278ca81b-40ec-473f-9288-9932fccb02d8.png)

<br>

##### 3.3.2 Car.java

- project: day07

- package: car

- Class: Car.java

  ```java
  package car;
  
  public class Car {
      // Fields
  	private String name;
  	private double fsize;	// fuel size
  	private double cfsize;	// current fuel size
  	private String status;	// Go or Stop
  	private double fe;		// fuel efficiency
  	
      // Constructors
  	public Car() {
  	}
  	public Car(String name, double fsize, double fe) {
  		this.name = name;
  		this.fsize = fsize;
  		this.fe = fe;
  		this.status = "STOP";		// argument가 아니더라도 constructor에 적어서 넣을 수 있다.
  	}
  	public Car(String name, double fsize, double cfsize, String status, double fe) {
  		this.name = name;
  		this.fsize = fsize;
  		this.cfsize = cfsize;
  		this.status = status;
  		this.fe = fe;
  	}
  
      // Getter & Setter
  	public double getCfsize() {
  		return cfsize;
  	}
  	public void setCfsize(double cfsize) {
  		this.cfsize = cfsize;
  	}
  	public String getStatus() {
  		return status;
  	}
  	public void setStatus(String status) {
  		this.status = status;
  	}
  	public double getFe() {
  		return fe;
  	}
  	public void setFe(double fe) {
  		this.fe = fe;
  	}
  	public String getName() {
  		return name;
  	}
  	public double getFsize() {
  		return fsize;
  	}
  
      // toString
  	@Override
  	public String toString() {
  		return "Car [name=" + name + ", fsize=" + fsize + ", cfsize=" + cfsize + ", status=" + status + ", fe=" + fe
  				+ "]";
  	}
  	
      // Methods
  	public void go(double km) {
  		if(this.cfsize == 0) {
  			System.out.println("기름이 없습니다.");
  			return;
  		}
  		System.out.println(this.name+" : Go");
  		this.status = "GO";						// 객체 상태 GO로 바꾼다
  		this.cfsize -= (km/this.fe);
  	}
  	public void stop() {
  		System.out.println(this.name+" : STOP");
  		this.status = "STOP";					// 객체 상태 STOP으로 바꾼다
  	}
  }
  ```

<br>

##### 3.3.3 CarApp.java

- project: day07

- package: car

- Class: CarApp.java

  ```java
  package car;
  
  import java.util.Scanner;
  
  public class CarApp {
  
  	public static void main(String[] args) {
  		System.out.println("Start ...");
  		Scanner sc = new Scanner(System.in);
  		Car car = null;						// reference type의 초기화는 null로 하면 된다.
  		
  		while(true) {								
  			System.out.println("Input cmd(c,a,s,g,t,q) ...");	// create, add, stop, go, stop, quit
  			String cmd = sc.next();
  			
  			if(cmd.equals("q")) {			// q를 누르면 반복문 종료
  				System.out.println("Bye");
  				break;
  				
  			}else if(cmd.equals("a")) {		// add
  				System.out.println("Input Fuel Size ..");
  				double fs = Double.parseDouble(sc.next());
  				car.setCfsize(fs);						// current fuel size에 fs를 넣는다
  				
  			}else if(cmd.equals("c")) {		// create
  				System.out.println("Input name ..");	// 이름
  				String name = sc.next();
  				System.out.println("Input fsize ..");	// 기름통 사이즈
  				double fsize = Double.parseDouble(sc.next());
  				System.out.println("Input fe");			// 연비
  				double fe = Double.parseDouble(sc.next());
  				
  				car = new Car(name, fsize, fe);
  				System.out.println(car);
  				
  			}else if(cmd.equals("g")) {		// go
  				System.out.println("Input km ..");
  				double km = Double.parseDouble(sc.next());
  				car.go(km);
  				
  			}else if(cmd.equals("t")) {		// stop
  				car.stop();
  				
  			}else if(cmd.equals("s")) {		// 상태 조회
  //				String name = car.getName();			// 원하는 상태를 출력하기 위한 라인
  //				String status = car.getStatus();
  				System.out.println(car);				// 이렇게 하면 원하는 상태 출력 안돼
  			}
  		}
  		sc.close();
  		System.out.println("End ...");
  	}
  }
  ```

  - Scanner 객체를 통해 c, a, s, g, t, q를 입력받아서 객체 생성(create), 기름 넣기(add), 출력(select), 출발(go), 정지(stop), 종료(quit)을 제어할 수 있다.