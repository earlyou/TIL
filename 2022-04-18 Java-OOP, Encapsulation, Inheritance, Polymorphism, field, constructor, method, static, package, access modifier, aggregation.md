# Multicampus Java day08

## 2022-04-18

>[1. 객체 간의 관계](#1-객체-간의-관계)
>
>​	[1.1 관계의 종류](#11-관계의-종류)
>
>[2. 객체 지향 프로그래밍 특징](#2-객체-지향-프로그래밍-특징)
>
>​	[2.1 캡슐화(Encapsulation)](#21-캡슐화encapsulation)
>
>​	[2.2 상속(Inheritance)](#22-상속inheritance)
>
>​	[2.3 다형성(Polymorphism)](#23-다형성polymorphism)
>
>[3. 객체와 클래스](#3-객체와-클래스)
>
>[4. 클래스의 구성 멤버](#4-클래스의-구성-멤버)
>
>​	[4.1 필드(Field)](#41-필드)
>
>​	[4.2 생성자(Constructor)](#42-생성자)
>
>​	[4.3 메소드(Method)](#43-메소드)
>
>​	[4.4 접근 제한자](#44-접근-제한자)
>
>[5. 실습](#5-실습)
>
>​	[5.1 Constructor](#51-constructor)
>
>​	[5.2 Method](#52-method)
>
>​	[5.3 정적 멤버화 static](#53-정적-멤버와-static)
>
>​	[5.4 패키지](#54-패키지)
>
>​	[5.5 접근 제한자](#55-접근-제한자)
>
>​	[5.6 집합 관계](#56-집합-관계)
>
>​	[5.7 상속](#57-상속inheritance)
<br>

### 1. 객체 간의 관계

#### 1.1 관계의 종류

- 집합 관계: 완성품과 부품의 관계
  - Aggregation: 없어도 되는 집합 관계(ex: 컴퓨터 - 프린터)
  - Composition: 꼭 있어야 하는 집합 관계(ex: 컴퓨터 - CPU)
- 사용 관계: 객체가 다른 객체를 사용하는 관계
- 상속 관계: 종류 객체와 구체적인 사물 객체 관계

![image](https://user-images.githubusercontent.com/103157377/170844272-fb898fc5-ae6a-4b65-9878-e167f784c4e3.png)

<br>

### 2. 객체 지향 프로그래밍 특징

#### 2.1 캡슐화(Encapsulation)

![image](https://user-images.githubusercontent.com/103157377/170844329-886ec99d-f917-4f83-b6f2-377f16f854b4.png)

<br>

#### 2.2 상속(Inheritance)

- 상위 객체가 갖고 있는 필드와 메소드를 하위 객체에게 물려주어 하위 객체가 쓸 수 있도록 함

![image](https://user-images.githubusercontent.com/103157377/170844361-f121899f-ae77-43f6-8e2a-e0a1b5be7b55.png)

- 상위 객체를 재사용 → 하위 객체의 쉽고 빠른 설계 가능
- 코드의 중복 감소, 유지 보수 간편화

<br>

#### 2.3 다형성(Polymorphism)

- 같은 타입이지만 실행 결과가 다양한 객체를 이용할 수 있는 성질
- 하나의 타입에 여러 객체를 대입 → 다양한 기능 이용 가능
- 자바는 다형성을 위해 부모 클래스 or 인터페이스의 타입 변환이 가능
- 부모 타입에 모든 자식 객체 대입 가능
- 인터페이스 타입에 모든 구현 객체 대입 가능
- 객체의 부품화 가능

![image](https://user-images.githubusercontent.com/103157377/170844449-0e254749-d19c-4347-ba01-bc775d2231ed.png)

<br>

### 3. 객체와 클래스

- 인스턴스(instance): 클래스로부터 만들어진 객체

![image](https://user-images.githubusercontent.com/103157377/170844490-26439125-f4cd-465c-98ba-edff6bb28293.png)

<br>

### 4. 클래스의 구성 멤버

![image](https://user-images.githubusercontent.com/103157377/170844539-4bd828e9-b056-42d1-8773-99b8fb578c72.png)

#### 4.1 필드

- 객체의 고유 데이터, 부품 객체, 상태 정보 저장하는 곳
- 선언 형태는 변수와 비슷, 하지만 변수 ≠ 필드
- 변수: 생성자와 메소드 내에서만 사용, 생성자와 메소드가 실행 종료되면 자동 소멸
- 필드: 생성자와 메소드 전체에서 사용, 객체가 소멸될 때 까지 존재

<br>

#### 4.2 생성자

- `new` 연산자로 호출되는 특별한 중괄호 `{}`블록
- 객체 생성 시 초기화 역할
- 필드 초기화 or 메소드 호출 → 객체 사용 준비
- 메소드와 비슷한 형태, 생성자 이름 = 클래스 이름, 리턴 타입X

<br>

#### 4.3 메소드

- 객체의 동장에 해당하는 중괄호 `{}`블록
- 메소드 호출 → 해당 메소드를 구성하는 모든 코드 일괄적 실행
- 필드 읽고 수정, 객체의 다양한 기능 수행
- 객체 간의 데이터 전달 수단
- 외부로부터 매개값 받기 가능, 실행 후 어떤 값도 리턴 가능

<br>

#### 4.4 접근 제한자

![image](https://user-images.githubusercontent.com/103157377/170849052-f1cc1e2a-29df-4dbb-bd8a-a0b5a495bac5.png)

<br>

### 5. 실습

#### 5.1 Constructor

##### 5.1.1 Constructor가 없을 때

- project: day08

- package: ch06

- class: Car.java

  ```java
  package ch06;
  
  public class Car {
  	// Field
  	private String name;
  	private String color;
  	private int size;
      
      // toString
  	@Override
  	public String toString() {
  		return "Car [name=" + name + ", color=" + color + ", size=" + size + "]";
  	}
  ```

- 출력

- class: CarApp.java

  ```java
  package ch06;
  
  public class CarApp {
  
  	public static void main(String[] args) {
          Car c = new Car();
          System.out.println(c);
      }
  ```

- 결과

  ```console
  Car [name=null, color=null, size=0]
  ```

- 결과는 default 값이 나온다.

<br>

##### 5.1.2 default Constructor가 없을 때

- class: Car.java

  ```java
  	// Constructor
  //	public Car() {		// Default Constructor
  //  }
  	public Car(String name) {
          this.name = name;
      }
  ```

- 이 상태에서 CarApp.java에서 출력을 시도하면 경고문이 나온다.

- `The constructor Car() is undefined`

<br>

##### 5.1.3 Constructor의 Overloading

- class: Car.java

  ```java
  // Constructor
  	public Car() {		// default Constructor는 반드시 필요하다
  	}
  	public Car(String name) {
  		this(name,"red",1000);
  	}
  	public Car(String name, String color) {
  		this(name,color,1000);
  	}
  	public Car(String name, String color, int size) {		// Constructor의 Overloading
  		this.name = name;
  		this.color = color;
  		this.size = size;
  		this.serial = cnt;
  		cnt++;
  	}
  	public Car(String name, String color, int size, int serial) {
  		this.name = name;
  		this.color = color;
  		this.size = size;
  		this.serial = serial;
  	}
  ```

- class: CarApp.java

  ```java
  package ch06;
  
  public class CarApp {
  
  	public static void main(String[] args) {
          Car c = new Car("k1");
          System.out.println(c);
      }
  ```

- 결과

  ```console
  Car [name=k1, color=red, size=1000]
  ```

- Constructor에서 name만 지정해주면 color=red, size=1000으로 설정되도록 했기 때문에 결과가 위 처럼 나온다.

<br>

#### 5.2 Method

##### 5.2.1 Method의 선언

- ch06/Car.java

  ```java
  // Method
  	public void go() {
  		System.out.println(this.name+": GO !!!!!");
  	}
  ```

- ch06/CarApp.java

  ```java
  Car c = new Car("k1");
  c.go(5);
  ```

- 결과

  ```console
  k1: GO !!!!!
  ```

<br>

##### 5.2.2 Method의 Overloading

- ch06/Car.java

  ```java
  // Method
  	public void go() {
  		System.out.println(this.name+": GO !!!!!");
  	}
  	public void go(int a) {
  		System.out.println(this.name+": GO !!!!! "+a);	// Method의 Overloading
  	}
  	public void go(double b) {
  		System.out.println(this.name+": GO !!!!! "+b);	// Method의 Overloading
  	}
  ```

- `double b`를 `int b`로 하면 Overloading이 아니다.

- argument type이 달라야 overloading이 된다.

<br>

#### 5.3 정적 멤버와 static

##### 5.3.1 클래스의 변수 선언

- ch06/Car.java

- 자주 사용하는 기능은 아니지만, 클래스에 변수를 선언할 수 있다.

  ```java
  	// Field, Variable
  	private String name;
  	private String color;
  	private int size;
  	private int serial;
  	
  	// class의 유일한 변수
  	static int cnt = 1000;
  ```

- 클래스의 유일한 변수로써 객체 개수를 100개를 만들어도 cnt는 1개로 유일하다.

- instance를 만들 때마다 constructor에서 cnt를 하나씩 증가시켜 serial 필드에 넣도록 제어할 수 있다.

  ```java
  	public Car(String name, String color, int size) {
  		this.name = name;
  		this.color = color;
  		this.size = size;
  		this.serial = cnt;
  		cnt++;
  	}
  ```

- ch06/CarApp.java

  ```java
  package ch06;
  
  public class CarApp {
  
  	public static void main(String[] args) {
          Car c1 = new Car("k1");
          Car c2 = new Car("k2");
          Car c2 = new Car("k2");
          System.out.println(c1);
          System.out.println(c2);
          System.out.println(c3);
      }
  ```

- 결과

  ```console
  Car [name=k1, color=red, size=1000, serial=1000]
  Car [name=k2, color=red, size=1000, serial=1001]
  Car [name=k3, color=red, size=1000, serial=1002]
  ```

<br>

##### 5.3.2 static 함수

- ch06/Cal1

  ```java
  package ch06;
  
  public class Cal1 {
      // Field
  	private int a;
  	private int b;
  	
  	// Constructor
  	public Cal1() {
  	}
  	public Cal1(int a, int b) {
  		this.a = a;
  		this.b = b;
  	}
  	
  	// Method
  	public int sum() {
  		return (this.a + this.b);
  	}
  	public int div() {
  		return (this.a/this.b);
  	}
  	public int avg() {
  		return(this.a + this.b)/2;
  	}
  }
  ```

- ch06/Cal2

  ```java
  package ch06;
  
  public class Cal2 {					// class에 method만 정의 가능
  	public static int sum(int a, int b) {
  		return a + b;
  	}
  	public static int div(int a, int b) {
  		return a / b;
  	}
  	public static double sum(double a, double b) {
  		return a + b;
  	}
  	public static double div(double a, double b) {
  		return a / b;
  	}
  }
  ```

- ch06/CalApp

  ```java
  package ch06;
  
  public class CalApp {
  
  	public static void main(String[] args) {
  		Cal1 c1 = new Cal1(10,2);				// 클래스를 정의해서 함수 호출
  		int c1avg = c1.avg();
  		System.out.println(c1avg);	// 6
  		
  		int c2sum = Cal2.sum(10, 2);			// 클래스 정의 없이 함수만 호출
  		System.out.println(c2sum);	// 12
  		
  		double c2sumd = Cal2.sum(10.1, 2.1);
  		System.out.println(c2sumd);	// 12.2
  	}
  }
  ```

- Cal2에서 method를 static으로 정의했기 때문에 Cal2의 method를 instance생성 없이 호출할 수 있다.

- 반면 Cal1은 method를 static으로 정의하지 않았기 때문에 Cal1의 method를 호출하기 위해서는 instance 생성이 필수다.

<br>

#### 5.4 패키지

- 서로 다른 패키지에서 클래스 호출 시에는 import를 쓴다.

- 단, 같은 프로젝트 안에서만 import 가능

- ch066/CarApp

  ```java
  package ch066;
  
  import ch06.Car;	// 다른 패키지 클래스 호출할 때 사용
  
  public class CarApp {
  
  	public static void main(String[] args) {
  		Car c = new Car("K1");
  		c.getName();
  	}
  }
  ```


<br>

#### 5.5 접근 제한자

- default 설정 방법

  ```java
  package ch06;
  public class Car {
      // Field
      String name;
      String color;
      int size;
      int serial;
      
      // Method
      void go() {
          System.out.println(this.name+": GO !!!!!");
      }
      void go(int a) {
          System.out.println(this.name+": GO !!!!!"+a);
      }
      void go(double b) {
          System.out.println(this.name+": GO !!!!!"+b);
      }
  }
  ```

<br>

#### 5.6 집합 관계

##### 5.6.1 Composition

- UML 디자인

  ![image](https://user-images.githubusercontent.com/103157377/170847802-5088ac90-7db9-497e-9ecd-fa3723235831.png)

- bank/Account.java

  ```java
  package bank;
  
  public class Account {
  	// Field
  	private String accNo;			// account number
  	private double balance;			// private를 통해 객체를 Encapsulate
  
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
  
  	// Methods
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
  		if(this.balance < money) {
  			System.out.println("잔액 부족 오류");
  			return;
  		}
  		this.balance -= money;
  	}
  	public double select() {			// return type=double
  		return this.balance;
  	}
  
  	// toString
  	@Override
  	public String toString() {
  		return "Account [accNo=" + accNo + ", balance=" + balance + "]";
  	}
  }
  ```

- bank/Customer.java

  ```java
  package bank;
  
  import java.util.Arrays;
  
  public class Customer {
  	// Field
  	private String name;
  	private Account[] accs;		// 한 명이 여러 계좌를 갖기 위해 배열 생성
  	
  	// Constructor
  	public Customer() {
  	}
  	public Customer(String name) {
  		this.name = name;
  	}
  	public Customer(String name, Account[] accs) {
  		this.name = name;
  		this.accs = accs;
  	}
  	
  	// Getter & Setter
  	public String getName() {
  		return name;
  	}
  	public Account[] getAccs() {
  		return accs;
  	}
  	public void setAccs(Account[] accs) {
  		this.accs = accs;
  	}
  	
  	// Method
  	// 고객 계좌 잔액의 합을 구하는 기능
  	public double getBalanceSum() {
  		double sum = 0.0;
  		for (int i = 0; i < accs.length; i++) {
  			sum += accs[i].getBalance();
  		}
  		return sum;
  	}
  	public void deposit(String accNo, double money) {
  		for (int i = 0; i < accs.length; i++) {
  			if (accs[i].getAccNo().equals(accNo)) {
  				accs[i].deposit(money);
  			}
  		}
  	}
  	// "1111"인 계좌를 리턴한다.
  	public Account getAc(String accNo) {
  		Account acc = null;
  		for (int i = 0; i < accs.length; i++) {
  			if(accs[i].getAccNo() == accNo) {
  				acc = accs[i];
  			}
  		}
  		return acc;
  	}
  	
      // toString
  	@Override
  	public String toString() {
  		return "Customer [name=" + name + ", accs=" + Arrays.toString(accs) + "]";
  	}
  }
  ```

- bank/BankApp.java

  ```java
  package bank;
  
  public class BankApp {
  
  	public static void main(String[] args) {
  		Customer c = new Customer("Kim");
  		System.out.println(c);
  		
  		Account []accs = new Account[3];
  		accs[0] = new Account("1111",10000);
  		accs[1] = new Account("2222",20000);
  		accs[2] = new Account("3333",30000);
  		
  		c.setAccs(accs);
  		System.out.println(c);
  		
  		Account myacc = c.getAc("2222");
  		System.out.println(myacc);
  		
  		c.deposit("2222", 50000);
  		System.out.println(c);
  		
  		double sum = c.getBalanceSum();
  		System.out.println(sum);
  	}
  }
  ```

- 실행 결과

  ```console
  Customer [name=Kim, accs=null]
  Customer [name=Kim, accs=[Account [accNo=1111, balance=10000.0], Account [accNo=2222, balance=20000.0], Account [accNo=3333, balance=30000.0]]]
  Account [accNo=2222, balance=20000.0]
  Customer [name=Kim, accs=[Account [accNo=1111, balance=10000.0], Account [accNo=2222, balance=70000.0], Account [accNo=3333, balance=30000.0]]]
  110000.0
  ```

<br>

#### 5.7 상속(Inheritance)

##### 5.7.1 UML 디자인

![image](https://user-images.githubusercontent.com/103157377/170848272-4e886281-32ed-4e69-a2f1-78bc76fe49f6.png)

- Manager는 id, name, salary, bonus 필드를 갖는다.
- Employee는 id, name, salary 필드를 갖는다.
- 이 때 두 클래스에 공통 필드인 id, name, salary를 양 쪽에 전부 선언하기 보다는 Manager 클래스가 Employee 클래스에서 상속을 받고 추가로 bonus필드를 선언하는 방법이 훨씬 효율적이다.
- Manager가 하위클래스, Employee가 Super Class
- Manager에서 Employee에 Generalization
- "is a"관계라고 표현한다. `Manager is an Employee`

<br>

##### 5.7.2 클래스

- company/Employee.java

  ```java
  package company;
  
  public class Employee {
  	// Field
  	private String id;
  	private String name;
  	protected double salary;
  	
  	// Constructor
  	public Employee() {
  	}
  	public Employee(String id, String name, double salary) {
  		this.id = id;
  		this.name = name;
  		this.salary = salary;
  	}
  	
  	// Getter & Setter
  	public String getId() {
  		return id;
  	}
  	public void setId(String id) {
  		this.id = id;
  	}
  	public String getName() {
  		return name;
  	}
  	public void setName(String name) {
  		this.name = name;
  	}
  	public double getSalary() {
  		return salary;
  	}
  	public void setSalary(double salary) {
  		this.salary = salary;
  	}
  	
  	// Method
  	public double annsalary() {		// 연봉 계산하기
  		return this.salary * 12;
  	}
  	
      // toString
  	@Override
  	public String toString() {
  		return "Employee [id=" + id + ", name=" + name + ", salary=" + salary + "]";
  	}
  }
  ```

- company/Manager.java

  ```java
  package company;
  
  public class Manager extends Employee{
  	// Field
  	private double bonus;
  	
  	// Constructor
  	public Manager() {
  	}
  	public Manager(String id, String name, double salary, double bonus) {
  		super(id, name, salary);
  		this.bonus = bonus;
  	}
  	
  	// Getter & Setter는 bonus만 생성
  	public double getBonus() {
  		return bonus;
  	}
  	public void setBonus(double bonus) {
  		this.bonus = bonus;
  	}
  	
  	//Method
  	// 재정의 - overriding: 상속받은 함수를 다시 정의하는 것
  	@Override
  	public double annsalary() {
  		double sum = 0.0;
  //		sum = salary * 12 + this.bonus;
  		sum = super.annsalary() + this.bonus;
  		return sum;
  	}
  	// 하위 클래스인 Manager만 가지는 고유한 기능, Specialization
  	public double getBonusTax() {		// 보너스에 대한 세금 계산
  		double tax = 0.0;
  		tax = this.bonus * 0.1;			// 세금은 10%
  		return tax;
  	}
  	
  	// toString
  	@Override
  	public String toString() {
  		return "Manager [bonus=" + bonus + ", toString()=" + super.toString() + "]";
  	}
  }
  ```

  - `extends`는 상속을 받는다는 뜻이다.
  - 상속을 받으면 constructor를 제외한 field, method, getter, setter 등을 전부 상속받는다.
  - method를 상속받기 때문에 굳이 method를 새로 선언하지 않아도 호출할 수 있다.
  - 지금 같은 경우는 보너스 요소를 넣기 위해 method를 override하여 정의하였다.
  - override: 상속받은 함수를 다시 정의하는 것

<br>

##### 5.7.3 Application

- company/ComapanyApp.java

  ```java
  package company;
  
  public class CompanyApp {
  
  	public static void main(String[] args) {
  		Employee e = new Employee("100", "James", 300);
  		System.out.println(e);
  		System.out.println(e.annsalary());
  		
  		Manager m = new Manager("101", "lee", 300, 500);
  		System.out.println(m.annsalary());
  		
  		System.out.println(m.getBonusTax());
  	}
  }
  ```

- 결과

  ```console
  Employee [id=100, name=James, salary=300.0]
  3600.0
  4100.0
  50.0
  ```


<br>

- company/CompanyApp2.java

  ```java
  package company;
  
  public class CompanyApp2 {
  
  	public static void main(String[] args) {
  		// heterogeneous collection
  		Employee e[] = new Employee[4];
  		e[0] = new Employee("100", "kim", 1000);
  		e[1] = new Employee("101", "lee", 1000);
  		e[2] = new Manager("102", "hong", 1000, 500);
  		e[3] = new Manager("103", "jin", 1000, 800);
  		
  		for (int i = 0; i < e.length; i++) {
  			System.out.println(e[i]);
  		}
  		for (int i = 0; i < e.length; i++) {
  			System.out.println(e[i].annsalary());
  		}
  		for (int i = 0; i < e.length; i++) {	// 만약 매니저만 연산에 필요하다면?
  			if(e[i] instanceof Manager) {
  				Manager m = (Manager)e[i];
  				System.out.println(m.getBonusTax());
  			}
  		}
  	}
  }
  ```

  - Manager가 Employee에서 상속받았기 때문에 Employee 배열에 Manager를 넣을 수 있다.

- 결과

  ```console
  Employee [id=100, name=kim, salary=1000.0]
  Employee [id=101, name=lee, salary=1000.0]
  
  Manager [bonus=500.0, toString()=Employee [id=102, name=hong, salary=1000.0]]
  Manager [bonus=800.0, toString()=Employee [id=103, name=jin, salary=1000.0]]
  
  12000.0
  12000.0
  12500.0
  12800.0
  
  50.0
  80.0
  ```

  

