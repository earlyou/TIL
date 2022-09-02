# Multicampus Java day12

## 2022-04-22

>

<br>

### 1. 기본 API 클래스 (Chapter 11)

#### 1.1 java.lang 패키지

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

##### 1.1.1 Object 클래스

- 클래스 선언 시 `extends` 키워드로 다른 클래스를 상속하지 않으면 암시적으로 java.lang.Object 클래스를 상속 받는다.
- 자바의 모든 클래스는 Object 클래스의 자식이거나 자손 클래스, Object는 자바의 최상위 부모 클래스

![image](https://user-images.githubusercontent.com/103157377/186350326-cbac74e2-d8af-437c-8f49-8cf864abce2f.png)

- 주요 메서드

| 메소드       | 용도                                                         |
| ------------ | ------------------------------------------------------------ |
| `equals()`   | - 두 객체의 동등 비교에 사용<br />- 논리적으로 동등하면 true, 그렇지 않으면 false 리턴 |
| `hashCode()` | - 객체의 메모리 번지를 이용해 해시코드를 만들어 리턴<br />- HashSet, HashMap, Hashtable 객체의 해시코드 값이 동등한지 비교 |
| `toString()` | - 객체의 문자 정보 리턴                                      |
| `clone()`    | - 원본 객체의 필드값과 동일한 값을 가지는 새로운 객체 생성<br />- 원본 객체 보호하기 위해 사용<br />- thin clone과 deep clone |
| `finalize()` | - 참조하지 않는 배열이나 객체를 소멸시키기 위해 Garbage Collector가 사용하는 메소드<br />- 메소드를 재정의해서 동작 가능 |

<br/>

##### 1.1.2 System클래스

- 자바 프로그램은 JVM 위에서 실행되기 때문에 OS 기능을 자바 코드로 접근하기 어렵다.
- System 클래스는 OS의 일부 기능 이용 가능
- 모든 필드와 메소드는 정적으로 구성
- 메소드 종류

| 메소드                              | 용도                                                         |
| ----------------------------------- | ------------------------------------------------------------ |
| `exit()`                            | - 강제로 JVM 종료                                            |
| `gc()`                              | - JVM에게 Garbage Collector를 가능한 빨리 실행해 달라고 요청 |
| `currentTimeMillis()`, `nanoTime()` | - 현재 시간을 밀리세컨드(1/1000) 단위와 나노세컨드(1/10<sup>9</sup>) 단위의 long 값으로 리턴 |
| `getProperty()`                     | - JVM이 시작할 때 자동 설정되는 시스템의 속성값을 리턴, 버전, 경로, OS 등 |
| `getenv()`                          | - OS에서 이름과 값으로 관리되는 문자열 정보인 환경 변수를 리턴 |

<br/>

##### 1.1.3 Class 클래스

- 자바의 클래스와 인터페이스의 메타 데이터를 Class 클래스로 관리
- 메소드 종류

| 메소드                                                       | 용도                                                         |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| `getClass()`                                                 | Class 객체를 얻기 위해 사용                                  |
| `forName()`                                                  | Class는 생성자가 없기 때문에 사용하는 정적 메서드            |
| `getDeclaredConstructors()`, `getDeclaredFields()`, `getDeclaredMethods()` | 클래스에 선언된 생성자, 필드, 메소드 정보를 리턴(Reflection). 상속된 멤버는 리턴하지 않는다. |
| `newInstance()`                                              | 동적 객체 생성                                               |

<br/>

##### 1.1.4 String 클래스

- 문자열 생성, 추출, 비교, 찾기, 분리, 변환 등 메소드 사용 가능
- 주로 사용하는 메소드

| 리턴 타입 | 메소드명(매개 변수)                                      | 설명                                                         |
| --------- | -------------------------------------------------------- | ------------------------------------------------------------ |
| char      | `charAt(int index)`                                      | 특정 위치의 문자 리턴                                        |
| boolean   | `equals(Object anObject)`                                | 두 문자열 비교                                               |
| byte[]    | `getBytes()`                                             | byte[]로 리턴                                                |
| byte[]    | `getBytes(Charset charset)`                              | 주어진 문자셋으로 인커딩한 byte[]로 리턴                     |
| int       | `indexOf(String str)`                                    | 문자열 내에서 주어진 문자열의 위치 리턴                      |
| int       | `length()`                                               | 총 문자 수 리턴                                              |
| String    | `replace(CharSequence target, CharSequence replacement)` | target 부분을 replacement로 대치한 새로운 문자열 리턴        |
| String    | `substring(int beginIndex)`                              | beginIndex 위치에서 끝까지 잘라낸 새로운 문자열 리턴         |
| String    | `substring(int beginIndex, int endIndex)`                | beginIndex 위치에서 endIndex 전까지 잘라낸 새로운 문자열 리턴 |
| String    | `to LowerCase()`                                         | 알파벳 소문자로 변환한 새로운 문자열 리턴                    |
| String    | `to UpperCase()`                                         | 알파벳 대문자로 변환한 새로운 문자열 리턴                    |
| String    | `trim()`                                                 | 앞 뒤 공백을 제거한 새로운 문자열 리턴                       |
| String    | `valueOf(int i)`<br />`valueOf(double d)`                | 기본 타입값을 문자열로 리턴                                  |

<br/>

##### 1.1.5 StringBuffer, StringBuilder 클래스

- 문자열을 저장하는 String은 내부의 문자열 수정 불가능
- `replace()`메소드를 쓰거나 `+` 연산자를 사용할 경우에도 문자열을 수정하는 것이 아닌, 새로운 객체를 만들어 참조하는 것
- 특히 `+` 연산자를 많이 사용할 수록 String 객체의 수가 늘어나기 때문에 프로그램 성능 저하 초래
- 문자열 변경 작업이 많을 때는 StringBuffer 또는 StringBuilder 클래스 사용 권장
- buffer에 문자열 저장한 후, 그 안에 추가, 수정, 삭제 작업 가능하도록 설계
- StringBuffer는 멀티 스레드 환경에서 사용 가능
- StringBuilder는 단일 스레드 환경에서만 사용 가능
- StringBuilder의 주요 메소드

| 메소드                                    | 설명                                              |
| ----------------------------------------- | ------------------------------------------------- |
| `append(...)`                             | 문자열 끝에 주어진 매개값 추가                    |
| `insert(int offset, ...)`                 | 문자열 중간에 주어진 매개값 추가                  |
| `delete(int start, int end)`              | 문자열 일부분 삭제                                |
| `deleteCharAt(int index)`                 | 문자열에서 주어진 index의 문자 삭제               |
| `replace(int start, int end, String str)` | 문자열의 일부분을 다른 문자열로 대치              |
| `reverse()`                               | 문자열의 순서를 뒤바꿈                            |
| `setCharAt(int index, char ch)`           | 문자열에서 주어진 index의 문자를 다른 문자로 대치 |

<br/>

##### 1.1.6 Math 클래스

- 수학 계산에 사용할 수 있는 정적 메소드 제공

| 메소드                                                       | 설명                  |
| ------------------------------------------------------------ | --------------------- |
| `int abs(int a)`<br />`double abs(double a)`                 | 절대 값               |
| `double ceil(double a)`                                      | 올림                  |
| `double floor(double a)`                                     | 버림                  |
| `int max(int a, int b)`<br />`double max(double a, double b)` | 최대 값               |
| `int min(int a, int b)`<br />`double min(double a, double b)` | 최소 값               |
| `double random()`                                            | 랜덤 값               |
| `double rint(double a)`                                      | 가까운 정수의 실수 값 |
| `long round(double a)`                                       | 반올림                |

- 숫자를 원하는 형식으로 표현하기 위해 **DecimalFormat**클래스 사용

| 기호 | 의미                                               | 패턴 예                          | 1234567.89 &rarr; 변환 결과                      |
| ---- | -------------------------------------------------- | -------------------------------- | ------------------------------------------------ |
| 0    | 10진수(빈 자리는 0으로 채움)                       | 0<br />0.0<br />0000000000.00000 | 12345678<br />1234567.9<br />0001234567.89000    |
| #    | 10진수(빈 자리는 채우지 않음)                      | #<br />#.#<br />##########.##### | 12345678<br />1234567.9<br />1234567.89          |
| .    | 소수점                                             | #.0                              | 1234567.9                                        |
| -    | 음수 기호                                          | +#.0<br />-#.0                   | +1234567.9<br />-1234567.9                       |
| ,    | 단위 구분                                          | #,###,0                          | 1,234,567,9                                      |
| E    | 지수 문자                                          | 0.0E0                            | 1.2E6                                            |
| ;    | 양수와 음수의 패턴을 모두 기술할 경우, 패턴 구분자 | +#,### ; -#,###                  | +1,234,568(양수일 때)<br />-1,234,568(음수일 때) |

<br/>

##### 1.1.7 Random 클래스

- 난수를 얻어내기 위한 다양한 메소드 제공
- 생성자 종류

| 생성자              | 설명                                                    |
| ------------------- | ------------------------------------------------------- |
| `Random()`          | 호출 시마다 다른 종자값(현재시간 이용)이 자동 설정된다. |
| `Random(long seed)` | 매개값으로 주어진 종자값이 설정된다.                    |

- 메소드 종류

| 리턴 값 | 메소드(매개 변수) | 설명                                                         |
| ------- | ----------------- | ------------------------------------------------------------ |
| boolean | `nextBoolean()`   | boolean 타입의 난수 리턴                                     |
| double  | `nextDouble()`    | double 타입의 난수 리턴(0.0 <= ~ < 1.0)                      |
| int     | `nextInt()`       | int 타입의 난수 리턴(-2<sup>31</sup> <= ~ <= 2<sup>31</sup>-1) |
| int     | `nextInt(int n)`  | int 타입의 난수 리턴(0 <= ~ < n-1)                           |

<br/>

#### 1.2 java.util 패키지

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

##### 1.2.1 Objects 클래스

- 객체 비교, 해시코드 생성, null 검사, 문자열 리턴 등 정적 메소드들로 구성된 Object의 유틸리티 클래스
- 메소드 종류

| 리턴 타입 | 메소드(매개 변수)                                         | 설명                                                         |
| --------- | --------------------------------------------------------- | ------------------------------------------------------------ |
| int       | `compare(T a, T b, Comparator<T> c)`                      | 두 객체 a와 b를 Comparator를 사용해 비교                     |
| boolean   | `deepEquals(Object a, Object b)`                          | 두 객체의 깊은 비교(배열의 항목까지 비교)                    |
| boolean   | `equals(Object a, Object b)`                              | 두 객체의 얕은 비교(번지만 비교)                             |
| int       | `hash(Object... values)`                                  | 매개값이 저장된 배열의 해시코드 생성                         |
| int       | `hashCode(Object o)`                                      | 객체의 해시코드 생성                                         |
| boolean   | `isNull(Object obj)`                                      | 객체가 null인지 조사                                         |
| boolean   | `nonNull(Object obj)`                                     | 객체가 null이 아닌지 조사                                    |
| T         | `requireNonNull(T obj)`                                   | 객체가 null인 경우 예외 발생                                 |
| T         | `requireNonNull(T obj, String message)`                   | 객체가 null인 경우 예외 발생(주어진 예외 메시지 포함)        |
| T         | `requireNonNull(T obj, Supplier<String> messageSupplier)` | 객체가 null인 경우 예외 발생(람다식이 만든 예외 메시지 포함) |
| String    | `toString(Object o)`                                      | 객체의 toString() 리턴값 리턴                                |
| String    | `toString(Object o, String nullDefault)`                  | 객체의 toString() 리턴값 리턴, 첫 번째 매개값이 null일 경우 두 번째 매개값 리턴 |

 <br/>

##### 1.2.2 StringTokenizer 클래스

- 문자열이 특전 구분자(delimiter)로 연결되어 있을 경우 구분자 기준으로 문자열 분리를 위해 사용하는 메소드 포함
- 메소드 종류

| 메소드              | 용도                                                         |
| ------------------- | ------------------------------------------------------------ |
| `split()`           | 정규 표현식을 여러 종류의 구분자를 기준으로 문자열을 분리하고 배열로 리턴 |
| `StringTokenizer()` | 문자열이 한 종류의 구분자로 연결 돼있을 경우 문자열(token) 분리 가능 |

<br/>

##### 1.2.3 Date 클래스

- 날짜를 표현하는 클래스
- 생성자는 주로 `Date()` 만 사용, 현재 날짜를 불러온다.
- `Date now = new Date();`
- 날짜를 문자열로 얻고 싶다면 `toString()`메소드를 사용
- 특정 문자열 포맷으로 얻고 싶다면 **SimpleDateFormat** 클래스 이용

| 패턴 문자 | 의미                       | 패턴 문자 | 의미                 |
| --------- | -------------------------- | --------- | -------------------- |
| y         | 년                         | H         | 시(0 ~ 23)           |
| M         | 월                         | h         | 시(1 ~ 12)           |
| d         | 일                         | K         | 시(0 ~ 11)           |
| D         | 월 구분이 없는 일(1 ~ 365) | k         | 시(1 ~ 24)           |
| E         | 요일                       | m         | 분                   |
| a         | 오전/오후                  | s         | 초                   |
| w         | 년의 몇 번째 주            | S         | 밀리세컨드(1/1000초) |
| W         | 월의 몇 번째 주            |           |                      |

- `SimpleDateFormat sdf = new SimpleDateFormat("yyyy-MM-dd");`

<br/>

##### 1.2.4 Calender 클래스

- 달력을 표현한 클래스
- 추상 클래스이므로 new 연산자로 인스턴스 생성 불가
- 날짜와 시간 계산 방법이 지역과 문화 나라에 따라 다르기 때문
- 날짜와 시간을 계산하는데 꼭 필요한 메소드들만 포함
- 일반적으로는 하위 클래스는 필요없고 `getInstance()` 메소드를 사용하여 하위 객체를 얻는다.
- `Calender now = Calender.getInstance();`

| 예제                                        | 의미           |
| ------------------------------------------- | -------------- |
| `int year = now.get(Calender.YEAR);`        | 년도 리턴      |
| `int month = now.get(Calendar.MONTH) + 1;`  | 월 리턴        |
| `int day = now.get(Calendar.DAY_OF_MONTH);` | 일 리턴        |
| `int week = now.get(Calendar.DAY_OF_WEEK);` | 요일 리턴      |
| `int amPm now.get (Calendar.AM_PM);`        | 오전/오후 리턴 |
| `int hour = now.get(Calendar.HOUR);`        | 시 리턴        |
| `int minute = now.get(Calendar.MINUTE);`    | 분 리턴        |
| `int second = now.get(Calendar.SECOND);`    | 초 리턴        |

<br/>

#### 1.3 java.time 패키지

- Java 7 이전까지는 `Date` 와 `Calender`클래스를 이용해서 날짜와 시간 정보 제어
- Java 7 이후 `Date`의 대부분의 메소드는 Deprecated
- `Calender`클래스는 날짜와 시간 조작과 비교가 불가능
- Java 8부터는 날짜와 시간을 나타내는 여러 API를 새롭게 추가

| 패키지             | 설명                                                         |
| ------------------ | ------------------------------------------------------------ |
| java.time          | 날짜와 시간을 나타내는 핵심 API인 LocalDate, LocalTime, LocalDateTime, ZonedDateTime포함, ISO-8601에 정의된 달력 시스템 |
| java.time.chrono   | ISO-8601에 정의된 달력 시스템 외 다른 달력 시스템이 필요할 때 사용할 수 있는 API들 포함 |
| java.time.format   | 날짜와 시간을 파싱하고 포맷팅하는 API들 포함                 |
| java.time.temporal | 날짜와 시간을 연산하기 위한 보조 API들 포함                  |
| java.time.zone     | 타임존을 지원하는 API들 포함                                 |

<br/>

##### 1.3.1 날짜와 시간 객체 생성

- java.time 패키지의 5가지 클래스

| 클래스 명     | 설명                                            |
| ------------- | ----------------------------------------------- |
| LocalDate     | 로컬 날짜 클래스                                |
| LocalTime     | 로컬 시간 클래스                                |
| LocalDateTime | 로컬 날짜 및 시간 클래스(LocalDate + LocalTime) |
| ZonedDateTime | 특정 타임존(TimeZone)의 날짜와 시간 클래스      |
| Instant       | 특정 시점의 Time-Stamp 클래스                   |

<br/>

##### 1.3.2 날짜와 시간에 대한 정보 얻기

| 클래스        | 리턴 타입  | 메소드(매개 변수) | 설명                           |
| ------------- | ---------- | ----------------- | ------------------------------ |
| LocalDate     | int        | `getYear()`       | 년                             |
| LocalDate     | Month      | `getMonth()`      | Month 열거값                   |
| LocalDate     | int        | `getMonthValue()` | 월                             |
| LocalDate     | int        | `getDayOfYear()`  | 일년의 몇 번째 일              |
| LocalDate     | int        | `getDayOfMonth()` | 월의 몇 번째 일                |
| LocalDate     | DayOfWeek  | `getDayOfWeek()`  | 요일                           |
| LocalDate     | boolean    | `isLeapYear()`    | 윤년 여부                      |
| LocalTime     | int        | `getHour()`       | 시간                           |
| LocalTime     | int        | `getMinute()`     | 분                             |
| LocalTime     | int        | `getSecond()`     | 초                             |
| LocalTime     | int        | `getNano()`       | 나노초                         |
| ZonedDateTime | ZoneId     | `getZone()`       | 존 아이디 리턴(ex: Asia/Seoul) |
| ZonedDateTime | ZoneOffset | `getOffset()`     | 존 오프셋(시차) 리턴           |

<br/>

##### 1.3.3 날짜, 시간 조작

- 더하기, 빼기

| 클래스                                          | 리턴 타입                                       | 메소드(매개 변수)                                            | 설명                                                         |
| ----------------------------------------------- | ----------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| LocalDate<br />LocalDateTime<br />ZonedDateTime | LocalDate<br />LocalDateTime<br />ZonedDateTime | `minusYears(long)`<br />`minusMonths(long)`<br />`minusDays(long)`<br />`minusWeeks(long)`<br />`plusYears(long)`<br />`plusMonths(long)`<br />`plusWeeks(long)`<br />`plusDays(long)` | 년 빼기<br />달 빼기<br />일 빼기<br />주 빼기<br />년 더하기<br />달 더하기<br />주 더하기<br />일 더하기 |
| LocalTime<br />LocalDateTime<br />ZonedDateTime | LocalTime<br />LocalDateTime<br />ZonedDateTime | `minusHours(long)`<br />`minusMinutes(long)`<br />`minusSeconds(long)`<br />`minusNanos(long)`<br />`plusHours(long)`<br />`plusMinutes(long)`<br />`plusSeconds(long)`<br />`plusNanos(long)` | 시간 빼기<br />분 빼기<br />초 빼기<br />나노초 빼기<br />시간 더하기<br />분 더하기<br />초 더하기<br />나노초 더하기 |

<br/>

- 변경하기
  - '상대 변경'은 현재 날짜를 기준으로 상대적인 날짜를 리턴

| 클래스                                          | 리턴 타입                                       | 메소드(매개 변수)                                            | 설명                                                         |
| ----------------------------------------------- | ----------------------------------------------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| LocalDate<br />LocalDateTime<br />ZonedDateTime | LocalDate<br />LocalDateTime<br />ZonedDateTime | `withYear(int)`<br />`withMonth(int)`<br />`withDayOfMonth(int)`<br />`withDayOfYear(int)`<br />`with(TemporalAdjuster adjuster)` | 년 변경<br />월 변경<br />월의 일 변경<br />년의 일 변경<br />상대 변경 |
| LocalTime<br />LocalDateTime<br />ZonedDateTime | LocalTime<br />LocalDateTime<br />ZonedDateTime | `withHour(int)`<br />`withMinute(int)`<br />`withSecond(int)`<br />`withNano(int)` | 시간 변경<br />분 변경<br />초 변경<br />나노초 변경         |

<br/>

### 2. 컬렉션 프레임워크(Chapter 15)

- 배열(Array)의 문제점을 해결하고 객체들을 효율적으로 추가, 삭제, 검색할 수 있도록 java.util 패키지에 컬렉션과 관련된 인터페이스와 클래스들을 포함시켜 놓은 것

![image](https://user-images.githubusercontent.com/103157377/188152362-7af44184-4401-4a00-b99e-330561ff69f1.png)

- 인터페이스별로 사용할 수 있는 컬렉션

| 인터페이스 분류  | 특징                                               | 구현 클래스                             |
| ---------------- | -------------------------------------------------- | --------------------------------------- |
| Collection(List) | - 순서 유지하고 저장<br />- 중복 저장 가능         | ArrayList, Vector, LinkedList           |
| Collection(Set)  | - 순서 유지하지 않고 저장<br />- 중복 저장 불가    | HashSet, TreeSet                        |
| Map              | - Key, Value 쌍으로 저장<br />- Key 값은 중복 불가 | HashMap, Hashtable, TreeMap, Properties |

<br/>

#### 2.1 List 컬렉션

- 객체를 인덱스로 관리, 자동 인덱스 부여
- 인덱스로 객체 검색, 삭제 가능
- 객체 자체를 저장하지 않고 객체의 번지를 참조
- 동일한 객체 중복 저장 가능 &rarr; 동일 번지 참조
- null 저장 가능 &rarr; 객체 참조 X

​	![image](https://user-images.githubusercontent.com/103157377/188153899-21f0777a-4817-45dd-818e-8516a64558b7.png)

- List 인터페이스의 공통 메소드

| 기능 | 메소드                           | 설명                                             |
| ---- | -------------------------------- | ------------------------------------------------ |
| 추가 | boolean `add(E e)`               | 주어진 객체를 맨 끝에 추가                       |
| 추가 | void `add(int index, E element)` | 주어진 인덱스에 객체 추가                        |
| 추가 | E `set(int index, E element)     | 주어진 인덱스에 저장된 객체를 주어진 객체로 바꿈 |
| 검색 | boolean `contains(Object o)`     | 주어진 객체가 저장되어 있는지 여부               |
| 검색 | E `get(int index)`               | 주어진 인덱스에 저장된 객체 리턴                 |
| 검색 | boolean `isEmpty()`              | 컬렉션이 비어 있는지 조사                        |
| 검색 | int `size()`                     | 저장되어 있는 전체 객체 수 리턴                  |
| 삭제 | void `clear()`                   | 저장된 모든 객체 삭제                            |
| 삭제 | E `remove(int index)`            | 주어진 인덱스에 저장된 객체 삭제                 |
| 삭제 | boolean `remove(Object o)`       | 주어진 객체 삭제                                 |

<br />

##### 2.1.1 ArrayList

<br />

##### 2.1.2 Vector

<br />

##### 2.1.3 LinkedList

<br />

#### 2.2 Set 컬렉션

<br />

##### 2.2.1 HashSet

<br />

#### 2.3 Map 컬렉션

<br />

##### 2.3.1 HashMap

<br />

##### 2.3.2 Hashtable

<br />

##### 2.3.3 Properties

<br />

#### 2.3 LIFO와 FIFO 컬렉션

<br />

##### 2.3.1 Stack

<br />

##### 2.3.2 Queue

<br />

### 3. 제네릭(Chapter 13)

