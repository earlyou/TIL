# Multicampus Java day09

## 2022-04-20

[TOC]

<br>

### 1. 인터페이스

#### 1.1 인터페이스의 역할

- interface: 객체의 사용 방법을 정의한 타입
- 객체의 교환성↑ ⇒ 다형성 구현하는 매우 중요한 역할
- 개발 코드와 객체가 서로 통신하는 접점 역할
- 개발 코드가 인터페이스의 메소드 호출하면 인터페이스는 객체의 메소드 호출
- 개발 코드는 인터페이스의 메소드만 알고 있으면 된다.

![image](https://user-images.githubusercontent.com/103157377/170892839-961eb773-8ca9-4e95-95cf-dc3a044411cb.png)

- 중간에 굳이 인터페이스를 두는 이유는 개발 코드 변환 없이 객체를 변경할 수 있도록 하기 위해서다.

![image](https://user-images.githubusercontent.com/103157377/170892883-44272caf-17f9-4f98-89a9-04d5ee998a9b.png)

<br>

#### 1.2 인터페이스 선언

##### 1.2.1 인터페이스 구성 멤버

![image](https://user-images.githubusercontent.com/103157377/170893280-a01ad8e2-c259-469b-a0c5-6ab9f198ed66.png)

- 상수 필드(Constant Field)
- 추상 메소드(Abstract Method)
- 디폴트 메소드(Default Method)
- 정적 메소드(Static Method)

<br>

##### 1.2.2 상수 필드 선언

- 인터페이스는 데이터 저장을 할 수 없기 때문에 데이터를 저장할 인스턴스 or 정적 필드 선언 불가
- 대신 상수 필드만 선언 가능
- `public static final`로 선언
- 인터페이스에 선언된 필드 모두 `public static final`의 특성
- 따라서 `public static final`생략 가능
- 상수는 선언과 동시에 초기값 지정 필요

```java
[public static final] 타입 상수명 = 값;
```

<br>

##### 1.2.3 추상 메소드 선언

- 인터페이스의 메소드는 추상 메소드로 선언
- 인터페이스에 선언된 추상 메소드는 모두 `public abstract` 특성
- 따라서 `public abstract`를 생략해도 컴파일 과정에서 자동으로 붙는다.

![image](https://user-images.githubusercontent.com/103157377/170893644-d7e1d0eb-1f23-415f-a9b8-b96702a51903.png)

<br>

##### 1.2.4 디폴트 메소드 선언

- 형태는 클래스의 인스턴스 메소드와 동일

- 디폴트 메소드는 `public` 특성

- 따라서 `public`을 생략해도 컴파일 과정에서 자동으로 붙는다.

  ```java
  [public] default 리턴타입 메소드명(매개변수, ⋯) { ⋯ }
  ```

<br>

##### 1.2.5 정적 메소드 선언

- 형태는 클래스의 정적 메소드와 완전히 동일
- 정적 메소드는 `public` 특성
- 따라서 `public`을 생략해도 컴파일 과정에서 자동으로 붙는다.

```java
[public] static 리턴타입 메소드명(매개변수, ⋯) { ⋯ }
```

<br>

#### 1.3 인터페이스 구현

- 인터페이스가 호출하는 객체는 인터페이스에서 정의된 추상 메소드와 동일한 메소드 이름, 매개 타입, 리턴 타입을 가진 실체 메소드를 가져야 한다.
- 이러한 객체를 인터페이스 구현(implement) 객체라고 함
- 구현 객체를 생성하는 클래스를 구현 클래스라고 함

![image](https://user-images.githubusercontent.com/103157377/170894158-ea955d49-0984-4953-98b7-0a28284764fe.png)

##### 1.3.1 구현 클래스

- 구현 클래스는 보통 클래스와 동일
- 클래스 선언부에 `implements`키워드 추가, 인터페이스명 명시

```java
public class 구현클래스명 implements 인터페이스명 {
    // 인터페이스에 선언된 추상 메소드의 실체 메소드 선언
}
```

<br>

#### 1.4 다중 인터페이스 구현 클래스

- 구현 클래스는 모든 인터페이스의 추상 메소드에 대해 실체 메소드 작성 필요, 하나라도 없으면 추상클래스로 선언

![image](https://user-images.githubusercontent.com/103157377/170894396-abce79f8-bc81-42b9-a278-a2b81ce198c5.png)

```java
public class 구현클래스명 implements 인터페이스A, 인터페이스B {
    // A에 선언된 추상 메소드의 실체 메소드 선언
    // B에 선언된 추상 메소드의 실체 메소드 선언
}
```

<br>

### 2. 실습

#### 2.1 인터페이스 없을 때

- Oracle(Object): 데이터베이스
- OracleDAO: 데이터베이스와 연동
- App: OracleDAO에 DB요청
- CustomerVO: Value Object, 데이터를 전송하는 매개체

![image](https://user-images.githubusercontent.com/103157377/170894728-c9f164a0-995a-4a41-a153-ac5e1a2ba4b1.png)

<br>

##### 2.1.1 CustomerVO

- p344/CustomerVO.java

```java
package p344;

public class CustomerVO {	// Value Object, 데이터를 전송하는 매개체
	// Field
	private String id;
	private String pwd;
	private String name;
	
	// Constructor
	public CustomerVO() {
	}
	public CustomerVO(String id, String pwd, String name) {
		this.id = id;
		this.pwd = pwd;
		this.name = name;
	}
	
	// Getter & Setter
	public String getId() {
		return id;
	}
	public void setId(String id) {
		this.id = id;
	}
	public String getPwd() {
		return pwd;
	}
	public void setPwd(String pwd) {
		this.pwd = pwd;
	}
	public String getName() {
		return name;
	}
	public void setName(String name) {
		this.name = name;
	}
	
    // toString
	@Override
	public String toString() {
		return "CustomerVO [id=" + id + ", pwd=" + pwd + ", name=" + name + "]";
	}
}
```

<br>

##### 2.1.2 OracleDAO

- 데이터베이스를 가상으로 구현한다.

- p344/OracleDAO.java

```java
package p344;

import java.util.ArrayList;

public class OracleDAO {
	
	public void connect() {
		System.out.println("Oracle Server Connected .......");
	}
	public void close() {
		System.out.println("Oracle Server Closed .......");
	}
	
	public void insert(CustomerVO c) {	// VO를 데이터베이스에 입력하는 역할
		connect();
		System.out.println(c);
		System.out.println("Inserted ...");// 아직 DB를 안배웠기 때문에 이렇게 표현
		close();
	}
	public void delete(String id) {		// 삭제
		connect();
		System.out.println(id);
		System.out.println("Deleted ...");
		close();
	}
	public CustomerVO select(String id) {	// App이 사용자 정보를 요청하면 Oracle에서 정보를 가져와서 CustomerVO를 만들어서 App에 주는 기능
		connect();
		String pwd = "pwd01";
		String name = "James";
		CustomerVO c = new CustomerVO(id, pwd, name);
		close();
		return c;
	}
	public ArrayList<CustomerVO> select(){	// 모든 Customer 정보를 가져온다, Overloading
		connect();
		ArrayList<CustomerVO> list = new ArrayList<CustomerVO>(); // new ArrayList<CustomerVO>()에서 CustomerVO는 없어도됨
		list.add(new CustomerVO("id01","pwd01","James1"));		// 리스트에 객체 넣기
		list.add(new CustomerVO("id02","pwd02","James2"));
		list.add(new CustomerVO("id03","pwd04","James3"));
		close();
		return list;
	}
}
```

<br>

##### 2.1.3 App

- p344/App.java

```java
package p344;

import java.util.ArrayList;
import java.util.Scanner;

public class App {

	public static void main(String[] args) {
		System.out.println("Start ...");
		OracleDAO dao = new OracleDAO();
		
		Scanner sc = new Scanner(System.in);
		
		while(true) {
			System.out.println("Input cmd(i, d, s, a, q) ..."); // insert, delete, select, select all, quit
			String cmd = sc.next();
			
			if(cmd.equals("q")) {			// q를 누르면 반복문 종료
				System.out.println("Bye");
				break;
			}else if(cmd.equals("i")) {		// Customer 정보를 DB에 넣는다
				System.out.println("Input Customer info ..");
				System.out.println("Input Customer id: ");
				String id = sc.next();
				System.out.println("Input Customer pwd: ");
				String pwd = sc.next();
				System.out.println("Input Customer name: ");
				String name = sc.next();
				
				CustomerVO c = new CustomerVO(id, pwd, name);
				dao.insert(c);
			}else if(cmd.equals("d")) {
				System.out.println("Input Customer id: ");
				String id = sc.next();
				dao.delete(id);
			}else if(cmd.equals("s")) {
				System.out.println("Input Customer id: ");
				String id = sc.next();
				CustomerVO c = dao.select(id);
				System.out.println(c);
			}else if(cmd.equals("a")) {
				ArrayList<CustomerVO> list = dao.select();
				for (CustomerVO c : list) {
					System.out.println(c);
				}
			}
		}
		sc.close();
		System.out.println("End ...");
	}
}
```

- App과 OracleDAO는 결합도가 매우 높아 만약 둘 중 하나를 수정하거나 변경하면 코드를 처음부터 수정해야 한다는 번거로움이 생긴다.
- 이 때 App과 OracleDAO 사이에 interface를 둔다면 결합도를 낮춰 이러한 불편함을 줄일 수 있다.

<br>

#### 2.2 인터페이스 연결

![image](https://user-images.githubusercontent.com/103157377/171062231-40f30f66-fb03-492d-9fe6-a3378dfc61ac.png)



##### 2.2.1 DAO

- p345/DAO.java

  ```java
  package p345;
  
  import java.util.ArrayList;
  
  public interface DAO {					// interface는 원래 기능만 정의하는 껍데기이다.
  //	static final int a = 1000;			// 정해져있는 변수만 선언 가능
  	
  	
  	
  	public default void connect() {		// 최근에는 interface안에 함수도 만들 수 있도록 바뀌었다.
  		System.out.println("Connect .....");
  	}
  	public default void close() {		// 여기서 default는 일반 함수라는 뜻이다. private, public default 아님
  		System.out.println("Close .....");
  	}
  	
  	public void insert(CustomerVO c);	// abstract만 빠져있을 뿐 사실상 추상 메소드와 같다, 
  	public void delete(String id);
  	public CustomerVO select(String id);
  	public ArrayList<CustomerVO> select();
  }
  ```

<br>

##### 2.2.2 OracleDAO, MariadbDAO

- p344/OracleDAO

  ```java
  package p345;
  
  import java.util.ArrayList;
  
  public class OracleDAO implements DAO {
  
  	@Override
  	public void insert(CustomerVO c) {
  		connect();
  		System.out.println("Oracle Inserted: "+c);
  		close();
  	}
  
  	@Override
  	public void delete(String id) {
  		connect();
  		System.out.println("Oracle Deleted: "+id);
  		close();
  	}
  
  	@Override
  	public CustomerVO select(String id) {
  		connect();
  		System.out.println("Oracle Selected: "+id);
  		CustomerVO c = new CustomerVO("id01","pwd01","James");	// 가상 DB
  		close();
  		return c;
  	}
  
  	@Override
  	public ArrayList<CustomerVO> select() {
  		connect();
  		System.out.println("Oracle Selected All: ");
  		ArrayList<CustomerVO> list = new ArrayList<CustomerVO>();
  		list.add(new CustomerVO("id01","pwd01","James1"));
  		list.add(new CustomerVO("id02","pwd02","James2"));
  		list.add(new CustomerVO("id03","pwd04","James3"));
  		close();
  		return list;
  	}
  }
  ```

  - interface를 상속 받고, Override한다.

- p344/MariadbDAO.java

  ```java
  package p345;
  
  import java.util.ArrayList;
  
  public class MariadbDAO implements DAO {
  
  	@Override
  	public void insert(CustomerVO c) {
  		connect();
  		System.out.println("Mariadb Inserted: "+c);
  		close();
  	}
  
  	@Override
  	public void delete(String id) {
  		connect();
  		System.out.println("Mariadb Deleted: "+id);
  		close();
  	}
  
  	@Override
  	public CustomerVO select(String id) {
  		connect();
  		System.out.println("Mariadb Selected: "+id);
  		CustomerVO c = new CustomerVO("id01","pwd01","James");	// 가상 DB
  		close();
  		return c;
  	}
  
  	@Override
  	public ArrayList<CustomerVO> select() {
  		connect();
  		System.out.println("Mariadb Selected All: ");
  		ArrayList<CustomerVO> list = new ArrayList<CustomerVO>();
  		list.add(new CustomerVO("id01","pwd01","James1"));
  		list.add(new CustomerVO("id02","pwd02","James2"));
  		list.add(new CustomerVO("id03","pwd04","James3"));
  		close();
  		return list;
  	}
  }
  ```

<br>

##### 2.2.3 CustomerVO

- p344/CustomerVO.java

  ```java
  package p345;
  
  public class CustomerVO {	// Value Object, 데이터를 전송하는 매개체
  	// Field
  	private String id;
  	private String pwd;
  	private String name;
  	
  	// Constructor
  	public CustomerVO() {
  	}
  	public CustomerVO(String id, String pwd, String name) {
  		this.id = id;
  		this.pwd = pwd;
  		this.name = name;
  	}
  	
  	// Getter & Setter
  	public String getId() {
  		return id;
  	}
  	public void setId(String id) {
  		this.id = id;
  	}
  	public String getPwd() {
  		return pwd;
  	}
  	public void setPwd(String pwd) {
  		this.pwd = pwd;
  	}
  	public String getName() {
  		return name;
  	}
  	public void setName(String name) {
  		this.name = name;
  	}
  	
      // toString
  	@Override
  	public String toString() {
  		return "CustomerVO [id=" + id + ", pwd=" + pwd + ", name=" + name + "]";
  	}
  }
  ```

<br>

##### 2.2.4 App.java

- p344/App.java

  ```java
  package p345;
  
  import java.util.ArrayList;
  import java.util.Scanner;
  
  public class App {
  
  	public static void main(String[] args) {
  		System.out.println("Start ...");
  		DAO dao = new OracleDAO();		// 화면을 개발할 때는 인터페이스를 기준으로 개발한다.
  										// MariadbDAO, OracleDAO를 바꿔가면서 레고 조립하듯 코딩 가능
  		Scanner sc = new Scanner(System.in);
  		
  		while(true) {
  			System.out.println("Input cmd(i, d, s, a, q) ..."); // insert, delete, select, select all, quit
  			String cmd = sc.next();
  			
  			if(cmd.equals("q")) {			// q를 누르면 반복문 종료
  				System.out.println("Bye");
  				break;
  			}else if(cmd.equals("i")) {			// Customer 정보를 DB에 입력
  				System.out.println("Input Customer info ..");
  				System.out.println("Input Customer id: ");
  				String id = sc.next();
  				System.out.println("Input Customer pwd: ");
  				String pwd = sc.next();
  				System.out.println("Input Customer name: ");
  				String name = sc.next();
  				
  				CustomerVO c = new CustomerVO(id, pwd, name);
  				dao.insert(c);
  			}else if(cmd.equals("d")) {
  				System.out.println("Input Customer id: ");
  				String id = sc.next();
  				dao.delete(id);
  			}else if(cmd.equals("s")) {
  				System.out.println("Input Customer id: ");
  				String id = sc.next();
  				CustomerVO c = dao.select(id);
  				System.out.println(c);
  			}else if(cmd.equals("a")) {
  				ArrayList<CustomerVO> list = dao.select();
  				for (CustomerVO c : list) {
  					System.out.println(c);
  				}
  			}
  		}
  		sc.close();
  		System.out.println("End ...");
  	}
  }
  ```

<br>



