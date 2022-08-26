# Multicampus Java day12

## 2022-04-22

>

<br>

### 1. 기본 API 클래스 (Chapter 11)

#### 1.2 java.lang 패키지

- 자바 프로그램의 기본적인 클래스를 담은 패키지
- 포함된 클래스와 인터페이스는 `import`없이 사용
- 주요 클래스

| 클래스                                                       | 용도                                                         |
| :----------------------------------------------------------- | :----------------------------------------------------------- |
| Object                                                       | - 자바 클래스의 최상위 클래스로 사용                         |
| System                                                       | - 표준 입력장치(키보드)로부터 데이터를 입력 받을 때 사용<br />- 표준 출력장치(모니터)로 출력하기 위해 사용<br />- 자바 가상 머신을 종료시킬 때 사용<br />- Garbage Collector 실행 요청할 때 사용 |
| Class                                                        | - 클래스를 메모리로 로딩할 때 사용                           |
| String                                                       | - 문자열을 저장하고 여러가지 정보를 얻을 때 사용             |
| StringBuffer, StringBuilder                                  | - 문자열을 저장하고 내부 문자열을 조작할 때 사용             |
| Math                                                         | - 수학 함수를 이용할 때 사용                                 |
| Wrapper(Byte, Short, Character, Integer, <br />Float, Double, Boolean) | - 기본 타이브이 데이터를 갖는 객체를 만들 때 사용<br />- 문자열을 기본 타입으로 변환할 때 사용<br />- 입력값 검사에 사용 |

<br/>

##### 1.2.1 Object 클래스

- 클래스 선언 시 `extends` 키워드로 다른 클래스를 상속하지 않으면 암시적으로 java.lang.Object 클래스를 상속 받는다.
- 자바의 모든 클래스는 Object 클래스의 자식이거나 자손 클래스, Object는 자바의 최상위 부모 클래스

![image](https://user-images.githubusercontent.com/103157377/186350326-cbac74e2-d8af-437c-8f49-8cf864abce2f.png)

- 주요 메서드

| 메서드     | 용도                                                         |
| ---------- | ------------------------------------------------------------ |
| equals()   | - 두 객체의 동등 비교에 사용<br />- 논리적으로 동등하면 true, 그렇지 않으면 false 리턴 |
| hashCode() | - 객체의 메모리 번지를 이용해 해시코드를 만들어 리턴<br />- HashSet, HashMap, Hashtable 객체의 해시코드 값이 동등한지 비교 |
| toString() | - 객체의 문자 정보 리턴                                      |
| clone()    | - 원본 객체의 필드값과 동일한 값을 가지는 새로운 객체 생성<br />- 원본 객체 보호하기 위해 사용<br />- thin clone과 deep clone |
| finalize() | - 참조하지 않는 배열이나 객체를 소멸시키기 위해 Garbage Collector가 사용하는 메소드<br />- 메소드를 재정의해서 동작 가능 |

<br/>

##### 1.2.2 System클래스

- 자바 프로그램은 JVM 위에서 실행되기 때문에 OS 기능을 자바 코드로 접근하기 어렵다.
- System 클래스는 OS의 일부 기능 이용 가능
- 모든 필드와 메소드는 정적으로 구성
- 메소드 종류

| 메서드                          | 용도                                                         |
| ------------------------------- | ------------------------------------------------------------ |
| exit()                          | - 강제로 JVM 종료                                            |
| gc()                            | - JVM에게 Garbage Collector를 가능한 빨리 실행해 달라고 요청 |
| currentTimeMillis(), nanoTime() | - 현재 시간을 밀리세컨드(1/1000) 단위와 나노세컨드(1/10^9) 단위의 long 값으로 리턴 |
| getProperty()                   | - JVM이 시작할 때 자동 설정되는 시스템의 속성값을 리턴, 버전, 경로, OS 등 |
| getenv()                        | - OS에서 이름과 값으로 관리되는 문자열 정보인 환경 변수를 리턴 |

<br/>

#### 1.3 java.util 패키지

- 자바 프로그램 개발에 조미료 같은 역할

- 대부분 컬렉션 클래스로 구성
- 주요 클래스

| 클래스          | 용도                                            |
| :-------------- | ----------------------------------------------- |
| Arrays          | - 배열을 조작(비교, 복사, 정렬, 찾기)할 때 사용 |
| Calender        | - 운영체제의 날짜와 시간을 얻을 때 사용         |
| Date            | - 날짜와 시간 정보를 저장하는 클래스            |
| Objects         | - 객체 비교, null 여부 등을 조사할 때 사용      |
| StringTokenizer | - 특정 문자로 구분된 문자열을 뽑아낼 때 사용    |
| Random          | - 난수를 얻을 때 사용                           |

<br/>

##### 1.3.1 Objects 클래스

- 객체 비교, 해시코드 생성, null 검사, 문자열 리턴 등 정적 메소드들로 구성된 Object의 유틸리티 클래스
- 메소드 종류

| 리턴 타입 | 메소드(매개 변수)                                       | 설명                                                         |
| --------- | ------------------------------------------------------- | ------------------------------------------------------------ |
| int       | compare(T a, T b, Comparator<T> c)                      | 두 객체 a와 b를 Comparator를 사용해 비교                     |
| boolean   | deepEquals(Object a, Object b)                          | 두 객체의 깊은 비교(배열의 항목까지 비교)                    |
| boolean   | equals(Object a, Object b)                              | 두 객체의 얕은 비교(번지만 비교)                             |
| int       | hash(Object... values)                                  | 매개값이 저장된 배열의 해시코드 생성                         |
| int       | hashCode(Object o)                                      | 객체의 해시코드 생성                                         |
| boolean   | isNull(Object obj)                                      | 객체가 null인지 조사                                         |
| boolean   | nonNull(Object obj)                                     | 객체가 null이 아닌지 조사                                    |
| T         | requireNonNull(T obj)                                   | 객체가 null인 경우 예외 발생                                 |
| T         | requireNonNull(T obj, String message)                   | 객체가 null인 경우 예외 발생(주어진 예외 메시지 포함)        |
| T         | requireNonNull(T obj, Supplier<String> messageSupplier) | 객체가 null인 경우 예외 발생(람다식이 만든 예외 메시지 포함) |
| String    | toString(Object o)                                      | 객체의 toString() 리턴값 리턴                                |
| String    | toString(Object o, String nullDefault)                  | 객체의 toString() 리턴값 리턴, 첫 번째 매개값이 null일 경우 두 번째 매개값 리턴 |

 