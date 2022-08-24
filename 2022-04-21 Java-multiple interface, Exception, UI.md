## Multicampus Java day11

## 2022-04-21

> [1. 다중 인터페이스 구현 클래스](#1-다중-인터페이스-구현-클래스)
> 
> [2. 예외 처리](#2-예외-처리)
> 
> ​    [2.1 예외와 예외 클래스](#21-예외와-예외-클래스)
> 
> ​    [2.2 예외 처리 코드](#22-예외-처리-코드)
> 
> ​    [2.3 예외 종류에 따른 처리 코드](#23-예외-종류에-따른-처리-코드)
> 
> ​    [2.4 예외 떠넘기기](#24-예외-떠넘기기)
> 
> ​    [2.5 사용자 정의 예외와 예외 발생](#25-사용자-정의-예외와-예외-발생)
> 
> ​    [2.6 예외 정보 얻기](#26-예외-정보-얻기)
> 
> [3. 실습](#3-실습)
> 
> ​    [3.1 예외 처리](#31-예외-처리)
> 
> ​    [3.2 사용자 정의 예외, 예외 떠넘기기](#32-사용자-정의-예외-예외-떠넘기기)
> 
> ​    [3.3 UI 만들기](#33-ui-만들기)

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
      ⋯
  }
  ```

- 발생할 수 있는 Exception 종류별로 `throws`할 수 있지만, `throws Exception`만으로 모든 예외 떠넘기기 가능

- ```java
  리턴타입 메소드명(매개변수,⋯) throws Exception {
      ⋯
  }
  ```

- `throws` 키워드가 붙은 메소드는 반드시 `try` 블록 내에서 호출되어야 한다.

- `catch` 블록에서 떠넘겨 받은 예외를 처리한다,
  
  ```java
  public void method1() {
      try {
          method2();
      } catch(ClassNotFoundException e) {
          // 예외 처리 코드
          System.out.println("클래스가 존재하지 않습니다.");
      }
  }
  
  public void method2() throws ClassNotFoundException {
      Class clazz = Class.forName("java.lang.String2");
  }
  ```

<br>

#### 2.5 사용자 정의 예외와 예외 발생

- 자바 표준 API에서 제공하는 예외 클래스만으로는 다양한 종류의 예외 표현이 제한적
- 애플리케이션 서비스와 관련된 예외를 애플리케이션 예외(Application Exception)
- 사용자 정의 예외라고도 한다.

##### 2.5.1 사용자 정의 예외 클래스 선언

- 일반 예외는 `Exception` 상속

- 실행 예외는 `RuntimeException` 상속
  
  ```java
  public class XXXException extends [ Exception | RuntimeException ] {
      public XXXException() {}
      public XXXException(String message) { super(message); }
  }
  ```

<br>

##### 2.5.2 예외 발생시키기

- 코드에서 사용자 정의 예외 발생시키는 방법
  
  ```java
  throw new XXXException();
  throw new XXXException("메시지");
  ```

- 메소드 내부에서 `try-catch`블록으로 예외를 처리할 수 있다.

- 하지만 대부분은 자신을 호출한 곳에서 예외 처리하도록 `throws` 키워드로 떠넘긴다.
  
  ```java
  public void method() throws XXXException {
      throw new XXXException("메시지");
  }
  ```

- 메소드는 호출한 곳에서 예외처리
  
  ```java
  try {
      method();
  } catch(XXXException e) {
      // 예외 처리
  }
  ```

<br>

#### 2.6 예외 정보 얻기

- `try`블록에서 예외 발생하면 예외 객체는 `catch`블록의 매개 변수에서 참조하므로 변수를 이용하면 예외 객체 정보 얻기 가능

- 모든 예외 객체는 Exception 클래스 상속, Exception이 갖는 메소드들은 모든 예외 객체에서 호출 가능

- 가장 많이 쓰는 메소드는 `getMessage()`, `printStackTrace()`
  
  ```java
  try{
      // 예외 객체 생성
  } catch(Exception e) {
      // 예외가 갖는 Message 얻기
      String message = e.getMessage();
  
      // 예외의 발생 경로 추적
      e.printStackTrace();
  }
  ```

<br>

### 3. 실습

#### 3.1 예외 처리

##### 3.1.1 예외 발생과 처리

- 예외 발생 예시

- java day11/p422/Ex1.java
  
  ```java
  public class Ex1 {
      public static void main(String[] args) {
          Scanner sc = new Scanner(System.in);
          System.out.println("Input Number");
          String num = sc.next();            // 사용자가 숫자 입력
          int n = Integer.parseInt(num);    // 입력 값을 Integer로 변경
          System.out.println(n);            // 입력 숫자 출력
          sc.close();
      }
  }
  ```

- 실행을 하고 숫자가 아닌 영문이나 한글을 입력하면

- `Integer.parseInt(num);`구문에서 `NumberFormationException`이 발생한다.
  
  ```console
  Input number
  a
  
  Exception in thread "main" java.lang.NumberFormationException: For input String : "a"
  ```

- 예외 처리 예시
  
  ```java
  public class Ex1 {
      public static void main(String[] args) {
          Scanner sc = new Scanner(System.in);
          System.out.println("Input Number");
          String num = sc.next();            // 사용자가 숫자 입력
          int n = 0;
          try {
              n = Integer.parseInt(num);    // 입력 값을 Integer로 변경
          } catch(NumberFormationException e) {
              System.out.println("숫자가 아닙니다.");
          }
          System.out.println(n);            // 입력 숫자 출력
          sc.close();
      }
  }
  ```

- `try-catch` 안에서 선언된 변수는 local variable이기 때문에 `try-catch`블록 밖에서는 사용할 수 없다. 따라서 `n`을 `try-catch`블록 밖에서 선언

- 실행 하고 숫자가 아닌 문자 입력
  
  ```console
  Input number
  d
  숫자가 아닙니다.
  0
  ```

<br>

##### 3.1.2 `try-catch`블록 다중 사용

- java day11/p422/Ex3.java
  
  ```java
  public class Ex2 {    // 예외 상황 Exception
  
      public static void main(String[] args) {
          Scanner sc = new Scanner(System.in);
          System.out.println("Input number");
          String num = sc.next();
          int n = 0;
          int result = 0;
          try {
              n = Integer.parseInt(num);
              result = 100 / n;
              System.out.println(result);
          }catch(ArithmeticException e) {
              System.out.println("분모가 0입니다.");
          }catch(NumberFormatException e) {
              System.out.println("숫자가 아닙니다.");
          }finally {
              sc.close();
              System.out.println("end");
          }
      }
  
  }
  ```

- 예상되는 `Exception`에 따라 다르게 `catch`블록을 여러 번 쓸 수 있다.

<br>

#### 3.2 사용자 정의 예외, 예외 떠넘기기

- 은행 시스템 같은 경우, 잔액보다 큰 금액을 출금 하거나, 음수의 값을 입금할 때, `Exception`이 발생하도록 제어하고 싶지만

- 자바 API에서는 이러한 `Exception`을 제공해주지 않는다.

- 따라서 개발자가 직접 `Exception`을 만들어 `throws` 해줘야 한다.

- Java day11/bank/MinusException.java, OverdrawnException.java
  
  ```java
  public class MinusException extends Exception {
      public MinusException() { }
      public MinusException(String msg) { super(msg); }
  }
  
  public class OverdrawnException extends Exception {
      public OverdrawnException() { }
      public OverdrawnException(String msg) { super(msg); }
  }
  ```

- 예외 떠넘기기

- Java day11/bank/Account.java
  
  ```java
  public class Account {
      // Fields
      private String accNo;
      private double balance;
  
      // Constructors
      public Account() {
      }
      public Account(String accNo) {
          this.accNo = accNo;
      }
      public Account(String accNo, double balance) {
          this.accNo = accNo;
          this.balance = balance;
      }
  
      // Getter & Setter
      public String getAccNo() {
          return accNo;
      }
      public double getBalance() {
          return balance;
      }
  
      // Operation
      // 출금 금액이 1보다 작으면 안된다.
      // 출금 금액이 잔액보다 많으면 안된다.
      public void deposit(double money) throws Exception {
          if(money < 1) {
              throw new MinusException("마이너스입니다.");
          }
          this.balance += money;
      }
      public void withdraw(double money) throws MinusException, OverdrawnException {        
          if(money < 1) {
              throw new MinusException("음수입니다.");
          }
          if(this.balance < money) {                
              throw new OverdrawnException("잔액부족");
          }
          this.balance -= money;
      }
      public double select() {
          return this.balance;
      }
  
      // toString
      @Override
      public String toString() {
          return "Account [accNo=" + accNo + ", balance=" + balance + "]";
      }
  }
  ```

- Account 클래스 내부 메서드에서 `throws`를 이용해`Exception`을 떠넘기도록 할 수 있다.

- Java day11/bank/BankApp.java
  
  ```java
  public class BankApp {
  
      public static void main(String[] args) {
          Account acc = new Account("1111", 10000);
          try {
              acc.deposit(-100);
          } catch (Exception e) {
              System.out.println(e.getMessage());
          }
  
          try {
              acc.withdraw(1000);
          } catch (MinusException | OverdrawnException e) {
              System.out.println(e.getMessage());
          }
          System.out.println(acc);
      }
  }
  ```

<br>

#### 3.3 UI 만들기

- Java day11/awt/MyFrame.java
  
  ```java
  public class MyFrame {
      // Field
      Frame f;
      Button b;
  
      // Constructor
      public MyFrame() {
          f = new Frame("My Frame");
          b = new Button("Click");
          b.addActionListener(new ActionListener() {
  
              @Override
              public void actionPerformed(ActionEvent e) {
                  b.setLabel("Clicked");
              }
          });
      }
  
      // Method
      public void setView() {
          f.add(b, "North");		// 북쪽에 버튼 달기
          f.setSize(300,200);		// 사이즈
          f.setVisible(true);		// 화면에 보여져라
          f.addWindowListener(new WindowAdapter() {
              @Override
              public void windowClosing(WindowEvent e) {
                  System.exit(0);
              }
  
          });
      }
  }
  ```

- Java day11/awt/App.java
  
  ```java
  public class App {
  
      public static void main(String[] args) {
          MyFrame m = new MyFrame();        // 객체 생성
          m.setView();                    // 객체 행위
      }
  
  }
  ```

- 모바일 어플리케이션 만들 때 많이 쓴다. 
  
  ![image](https://user-images.githubusercontent.com/103157377/176991631-60e7d878-7f94-4244-a635-051b5db7812b.png)

<br>

#### 3.4 다중 인터페이스 구현

![image](https://user-images.githubusercontent.com/103157377/186331002-f1a4ae61-b2d5-45cc-a160-078a6f1cb124.png)

- Java day11/ws/BookVO.java

  ```java
  public class BookVO {
  	// Field
  	private String isdn;
  	private String bname;
  	private String aname;
  	
  	// Constructor
  	public BookVO() {
  	}
  	public BookVO(String isdn, String bname, String aname) {
  		this.isdn = isdn;
  		this.bname = bname;
  		this.aname = aname;
  	}
  
  	// Getter & Setter
  	public String getIsdn() {
  		return isdn;
  	}
  	public String getBname() {
  		return bname;
  	}
  	public String getAname() {
  		return aname;
  	}
  	public void setBname(String bname) {
  		this.bname = bname;
  	}
  	public void setAname(String aname) {
  		this.aname = aname;
  	}
  	
  	
  	@Override
  	public String toString() {
  		return "BookVO [isdn=" + isdn + ", bname=" + bname + ", aname=" + aname + "]";
  	}
  	
  }
  ```

- Java day11/ws/Search.java

  ```java
  public interface Search {
  	public ArrayList<BookVO> search(String bname) throws NotFoundException;
  }
  ```

- Java day11/ws/DAO.java

  ```java
  public interface DAO {
  	public void insert(BookVO b) throws DuplicatedIDException;
  	public void delete(String isdn) throws NotFoundException;
  	public BookVO update(String isdn, String bname, String aname) throws NotFoundException;
  	public BookVO select(String bname) throws NotFoundException;
  	public ArrayList<BookVO> select() throws NotFoundException;
  }
  ```

- Java day11/ws/OracleDAO.java

  ```java
  public class OracleDAO implements DAO, Search {
  	
  	HashMap<String, BookVO> map;
  	
  	// Constructor
  	public OracleDAO() {
  		map = new HashMap<String, BookVO>();
  	}
  
  	@Override
  	public ArrayList<BookVO> search(String bname) throws NotFoundException {
  		ArrayList<BookVO> list = new ArrayList<BookVO>();
  		if(map.size() == 0) {
  			throw new NotFoundException("책 정보가 없습니다.\n");
  		}
  		Collection<BookVO> col = map.values();
  		Iterator<BookVO> it = col.iterator();
  		
  		while(it.hasNext()) {
  			BookVO b = it.next();
  			if(b.getBname().equals(bname)) {
  				list.add(b);
  			}
  		}
  		
  		return list;
  	}
  
  	@Override
  	public void insert(BookVO b) throws DuplicatedIDException {
  		String key = b.getIsdn();
  		if(map.containsKey(key)) {
  			throw new DuplicatedIDException("중복된 ID가 있습니다.\n");
  		}
  		map.put(key, b);
  	}
  
  	@Override
  	public void delete(String isdn) throws NotFoundException {
  		if(!map.containsKey(isdn)) {
  			throw new NotFoundException("책을 찾을 수 없습니다.\n");
  		}
  		map.remove(isdn);
  	}
  
  	@Override
  	public BookVO update(String isdn, String bname, String aname) throws NotFoundException {
  		BookVO b = map.get(isdn);
  		if(!map.containsKey(isdn)) {
  			throw new NotFoundException("책을 찾을 수 없습니다.\n");
  		}
  		b.setBname(bname);
  		b.setAname(aname);
  		return b;
  	}
  
  	@Override
  	public BookVO select(String bname) throws NotFoundException {
  		BookVO b = null;
  		if(!map.containsKey(bname)) {
  			throw new NotFoundException("책을 찾을 수 없습니다.");
  		}
  		b = map.get(bname);
  		return b;
  	}
  
  	@Override
  	public ArrayList<BookVO> select() throws NotFoundException {
  		ArrayList<BookVO> list = new ArrayList<BookVO>();
  		
  		if(map.size() == 0) {
  			throw new NotFoundException("책을 찾을 수 없습니다.");
  		}
  		
  		Collection<BookVO> col = map.values();
  		Iterator<BookVO> it = col.iterator();
  		
  		while(it.hasNext()) {
  			BookVO book = it.next();
  			list.add(book);
  		}
  		
  		return list;
  	}
  
  }
  ```

- Java day11/ws/BookApp.java

  ```java
  public class BookApp {
  
  	public static void main(String[] args) {
  		System.out.println("도서관 프로그램을 시작합니다.");
  		OracleDAO oracledao = new OracleDAO();
  		DAO dao = oracledao;
  		Search search = oracledao;
  		Scanner sc = new Scanner(System.in);
  		
  		while(true) {
  			System.out.println("\n이용하실 서비스를 입력해주세요.\n"
  					+ "(insert, delete, update, select, all, search, quit)");
  			String cmd = sc.next();
  			
  			if(cmd.equals("insert")) {
  				System.out.println("새로운 ISBN을 입력해주세요.");
  				String isdn = sc.next();
  				System.out.println("새로운 책 이름을 입력해주세요.");
  				String bname = sc.next();
  				System.out.println("책의 저자를 입력해주세요.");
  				String aname = sc.next();
  				
  				BookVO b = new BookVO(isdn, bname, aname);
  				try {
  					dao.insert(b);
  				} catch (DuplicatedIDException e) {
  					System.out.println(e.getMessage());
  				}
  			}else if(cmd.equals("delete")) {
  				System.out.println("삭제할 책의 ISDN을 입력하세요.");
  				String isdn = sc.next();
  				try {
  					dao.delete(isdn);
  				}catch (NotFoundException e) {
  					System.out.println(e.getMessage());
  				}
  			}else if(cmd.equals("update")) {
  				System.out.println("수정할 책의 ISDN을 입력해주세요.");
  				String isdn = sc.next();
  				System.out.println("책의 이름을 수정해주세요.");
  				String bname = sc.next();
  				System.out.println("책의 저자를 수정해주세요.");
  				String aname = sc.next();
  				try {
  					BookVO b = dao.update(isdn, bname, aname);
  					System.out.println("책 정보가 수정되었습니다.\n"+b);
  				} catch (NotFoundException e) {
  					System.out.println(e.getMessage());
  				}
  			}else if(cmd.equals("select")) {
  				System.out.println("조회하고 싶은 책의 ISDN을 입력해주세요.");
  				String isdn = sc.next();
  				try {
  					BookVO b = dao.select(isdn);
  					System.out.println(b);
  				}catch(NotFoundException e) {
  					System.out.println(e.getMessage());
  				}
  			}else if(cmd.equals("all")) {
  				System.out.println("모든 책 리스트를 출력합니다.\n");
  				try {
  					ArrayList<BookVO> list = dao.select();
  					for (BookVO b : list) {
  						System.out.println(b);
  					}
  				} catch (NotFoundException e) {
  					System.out.println(e.getMessage());
  				}
  			}else if(cmd.equals("search")) {
  				System.out.println("찾고싶은 책의 이름을 입력해주세요.");
  				String bname = sc.next();
  				try {
  					ArrayList<BookVO> list = search.search(bname);
  					for (BookVO b : list) {
  						System.out.println(b);
  					}
  				} catch (NotFoundException e) {
  					System.out.println(e.getMessage());
  				}
  			}else if(cmd.equals("quit")) {
  				System.out.println("프로그램을 종료합니다.");
  				sc.close();
  				break;
  			}
  		}
  		
  	}
  
  }
  ```

  
