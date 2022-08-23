# Multicampus Java day09

## 2022-04-19

>[1. final 클래스와 final 메소드](#1-final-클래스와-final-메소드)
>
>​	[1.1 final class](#11-final-class)
>
>​	[1.2 final method](#12-final-method)
>
>[2. 접근 제한자](#2-접근-제한자)
>
>[3. 자동 타입 변환(Promotion)](#3-자동-타입-변환promotion)
>
>[4. 추상 클래스](#4-추상-클래스)
>
>[5. 실습](#5-실습)
>
>​	[5.1 Abstract Class](#51-abstract-class)

<br>

### 1. final 클래스와 final 메소드

- 클래스, 필드, 메소드 선언 시 사용 가능
- 해당 선언이 최종상태, 결코 수정될 수 없음을 뜻한다.

<br>

#### 1.1 final class

- 클래스 선언할 때, `class`앞에 `final`을 붙이면 상속할 수 없는 클래스가 된다.

- ch07/P288

  ```java
  package ch07;
  
  public final class P288 extends Object {
  
  }
  ```

  - 자바의 모든 클래스는 `Object`클래스를 상속 받고 있음을 표현함

- 이렇게 선언하면 P288 class는 누구도 상속받을 수 없다.

<br>

#### 1.2 final method

- 메소드를 선언할 때, `final`키워드를 붙이면 오버라이딩이 불가능한 메소드가 된다.

- 상속받은 자식 클래스에서 재정의할 수 없는 메소드가 된다.

  ```java
  public final void stop() {
      System.out.println("Stop ...");
  }
  ```

<br>

### 2. 접근 제한자

![image](https://user-images.githubusercontent.com/103157377/170851238-f3917907-5641-4a08-a153-a7e7c368d22a.png)

<br>

### 3. 자동 타입 변환(Promotion)

- 프로그램 실행 도중에 자동으로 타입 변환이 일어나는 것

  ![image](https://user-images.githubusercontent.com/103157377/170851284-51491728-ef4b-474e-a77c-2ff57d27adf7.png)

- 위와 같은 조건을 만족해야 promotion이 일어난다.

  ![image](https://user-images.githubusercontent.com/103157377/170851319-3e74732a-e7d2-455f-913b-279d7e4289e6.png)

  ```java
  Cat cat = new Cat();
  Animal animal = cat:
  Animal animal = new Cat();
  ```

- cat과 animal 변수는 타입만 다를 뿐, 동일한 Cat 객체를 참조

  ![image](https://user-images.githubusercontent.com/103157377/170851386-36d87fe8-dced-4760-a52f-9a37b54ee9b7.png)

- 이 외에도 아래는 promotion이 가능한 예시이다.

  ![image](https://user-images.githubusercontent.com/103157377/170892518-d8b9e7b2-a0e9-4455-a478-e6ac5581d52a.png)

<br>

### 4. 추상 클래스

- 클래스들의 공통적인 특성을 추출해서 선언한 클래스

- 추상 클래스와 실체 클래스는 상속 관계

- 추상 클래스가 상위 클래스

  ![image](https://user-images.githubusercontent.com/103157377/170851566-42e679c3-6f11-4fa3-a3b9-735b95ebff6e.png)

- 추상 클래스는 실체 클래스들의 공통된 field와 method만을 추출해서 만들었기 때문에 객체를 직접 생성하지 못한다.

<br>

### 5. 실습

#### 5.1 Abstract Class

##### 5.1.1 UML 디자인

![image](https://user-images.githubusercontent.com/103157377/170851843-4acaa0e2-1cc9-4090-8eef-0c553486aee8.png)

##### 5.1.2 추상 클래스

- graphic/Shape.java

  ```java
  package graphic;
  
  public abstract class Shape {
  	// Field
  	protected int x;
  	protected int y;
  	
  	// Constructor
  	public Shape() {
  	}
  	public Shape(int x, int y) {
  		this.x = x;
  		this.y = y;
  	}
  	
  	// Getter & Setter
  	public int getX() {
  		return x;
  	}
  	public void setX(int x) {
  		this.x = x;
  	}
  	public int getY() {
  		return y;
  	}
  	public void setY(int y) {
  		this.y = y;
  	}
  	
      // toString
  	@Override
  	public String toString() {
  		return "Shape [x=" + x + ", y=" + y + "]";
  	}
  	
  	// Abstract method
  	public abstract double getArea();		// Shape.java가 가진 정보로는 넓이나 둘레를 구할 수 없다
  	public abstract double getCircum();		// 따라서 추상 함수로 정의한다.
  }
  
  ```

<br>

##### 5.1.3 하위 클래스

- graphic/Rectangle.java

  ```java
  package graphic;
  
  public class Rectangle extends Shape {
  	// Field
  	private int width;
  	private int height;
  	
  	// Constructor
  	public Rectangle() {
  	}
  	public Rectangle(int x, int y) {
  		super(x, y);
  	}
  	public Rectangle(int x, int y, int width, int height) {
  		super(x, y);
  		this.width = width;
  		this.height = height;
  	}
  
  	// Getter & Setter
  	public int getWidth() {
  		return width;
  	}
  	public void setWidth(int width) {
  		this.width = width;
  	}
  	public int getHeight() {
  		return height;
  	}
  	public void setHeight(int height) {
  		this.height = height;
  	}
  
  	// toString
  	@Override
  	public String toString() {
  		return "Rectangle [width=" + width + ", height=" + height + ", x=" + x + ", y=" + y + "]";
  	}
  	
  	// Method
  	@Override
  	public double getArea() {
  		return width * height;
  	}
  	@Override
  	public double getCircum() {
  		return (width+height)*2;
  	}
  }
  ```

- graphic/Circle.java

  ```java
  package graphic;
  
  public class Circle extends Shape {
  	// Field
  	private int radius;
  
  	// Constructor
  	public Circle() {
  	}
  	public Circle(int x, int y) {
  		super(x, y);
  	}
  	public Circle(int x, int y, int radius) {
  		super(x, y);
  		this.radius = radius;
  	}
  	
  	// Getter & Setter
  	public int getRadius() {
  		return radius;
  	}
  	public void setRadius(int radius) {
  		this.radius = radius;
  	}
  	
      // toString
  	@Override
  	public String toString() {
  		return "Circle [radius=" + radius + ", x=" + x + ", y=" + y + "]";
  	}
  
  	// Method
  	@Override
  	public double getArea() {
  		return radius * radius * Math.PI;
  	}
  	@Override
  	public double getCircum() {
  		return 2 * radius * Math.PI;
  	}
  	public void setColor(String color) {		// 원에만 색깔을 지정
  		System.out.println(color);
  	}
  }
  ```

- graphic/Triangle.java

  ```java
  package graphic;
  
  public class Triangle extends Shape {
  	// Field
  	private int width;
  	private int height;
  	
  	// Constructor
  	public Triangle() {
  	}
  	public Triangle(int x, int y) {
  		super(x, y);
  	}
  	public Triangle(int x, int y, int width, int height) {
  		super(x, y);
  		this.width = width;
  		this.height = height;
  	}
  
  	// Getter & Setter
  	public int getWidth() {
  		return width;
  	}
  	public void setWidth(int width) {
  		this.width = width;
  	}
  	public int getHeight() {
  		return height;
  	}
  	public void setHeight(int height) {
  		this.height = height;
  	}
  	
  	// toString
  	@Override
  	public String toString() {
  		return "Triangle [width=" + width + ", height=" + height + ", x=" + x + ", y=" + y + "]";
  	}
  	
  	// Method
  	@Override
  	public double getArea() {
  		return (width * height)/2;
  	}
  	@Override
  	public double getCircum() {
  		return width + height + Math.hypot(width, height);
  	}
  }
  ```

<br>

##### 5.1.4 Application

- graphic/DrawPanel.java

  ```java
  package graphic;
  
  public class DrawPanel {
  	// Polymorphism
  	public void draw(Shape shape) {		// Polymorphism이 안된다면 도형마다 draw함수를 만들어야 함
  		System.out.println(shape.toString());
  		if(shape instanceof Circle) {
  			Circle c = (Circle)shape;	// type casting
  			c.setColor("red");
  		}
  	}
  }
  ```

  - 다형성을 이용해 일일히 도형마다 draw함수를 만들지 않는다.
  - Circle 객체만 빨간색으로 만들드록 제어

- graphic/App.java

  ```java
  package graphic;
  
  public class App {
  
  	public static void main(String[] args) {
  		DrawPanel dw = new DrawPanel();
  		Shape s1 = new Rectangle(5, 5, 10, 10);
  		dw.draw(s1);
  		Shape s2 = new Circle(4, 4, 10);
  		dw.draw(s2);
  	}
  }
  ```

- 결과

  ```console
  Rectangle [width=10, height=10, x=5, y=5]
  Circle [radius=10, x=4, y=4]
  red
  ```

<br>

##### 5.1.5 setColor()의 override

- 위 코드를 보면 setColor 메소드가 Circle.java에만 정의되어 있는 상태이다.

- 만약 Shape.java에 setColor를 abstract method로 넣고 싶다면

- Circle.java에서만 override를 하고 나머지 Rectangle.java, Triange.java 에서는 빈 코드로 남겨두면 된다.

- graphic2 package 참조

  ![image](https://user-images.githubusercontent.com/103157377/170852362-c7b9d807-9f6b-4c74-b93c-52f12d45b95c.png)

  
