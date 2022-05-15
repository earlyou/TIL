# Multicampus Java day05

## 2022-04-14

>[1. 배열의 min, max](#1-배열의-min-max)
>
>[2. 조별로 문제 내기](#2-조별로-문제-내기)

### 1. 배열의 min, max

- 배열의 최대값과 최솟값을 구하는 예제

  ```java
  public static void main(String[] args) {
      int ar[] = new int[5];
      Random rd = new Random();
      
  	for (int i = 0; i < ar.length; i++) {
          ar[i] = rd.nextInt(9)+1;
      }
      System.out.println(Arrays.toString(ar));
      
      int max = 0;
      int min = 99;
      for (int i = 0; i < ar.length; i++) {
          if(max < ar[i]) {
              max = ar[i];
          }
          if(min > ar[i]) {
              min = ar[i];
          }
      }
  
      System.out.printf("Max: %d\nMin: %d", max, min);
  }
  ```

<br/>

### 2. 조별로 문제 내기

- `*`로 원하는 층수의 피라미드 만들기

  ```java
  public static void main(String[] args) {
      Scanner sc = new Scanner(System.in);
      System.out.println("피라미드 층수: ");
      int row = sc.nextInt();
  
      for (int i=0; i<row; i++) {
          for (int j=1; j<row-i; j++) {	
              System.out.print(" ");
          }
          for (int j=0; j<i*2+1; j++) {
              System.out.print("*");
          }
          System.out.println("");
      }
      sc.close();
  }
  ```

- 1에서부터 6까지의 눈을 가진 3개의 주사위를 던져서 다음과 같은 규칙에 따라 상금을 받는 게임이 있다. 같은 눈이 3개가 나오면 10,000원+(같은 눈)×1,000원의 상금을 받게 된다. 같은 눈이 2개만 나오는 경우에는 1,000원+(같은 눈)×100원의 상금을 받게 된다. 모두 다른 눈이 나오는 경우에는 (그 중 가장 큰 눈)×100원의 상금을 받게 된다. 3개 주사위의 나온 눈이 주어질 때, 상금을 계산하는 프로그램을 작성 하시오.

  ```java
  public static void main(String[] args) {
      Random r = new Random();
      int dice1 = r.nextInt(6)+1;
      int dice2 = r.nextInt(6)+1;
      int dice3 = r.nextInt(6)+1;
  
      System.out.println(dice1);
      System.out.println(dice2);
      System.out.println(dice3);
  
      if (dice1==dice2 && dice1==dice3) {
          System.out.println("상금: " + ((dice1*1000)+10000));
      } else if (dice1==dice2){
          System.out.println("상금: " + (Math.max(dice1,dice2)*100+1000));
      } else if (dice1==dice3){
          System.out.println("상금: " + (Math.max(dice1,dice3)*100+1000));
      } else if (dice2==dice3) {
          System.out.println("상금: " + (Math.max(dice2,dice3)*100+1000));
      } else {
          System.out.println("상금: " + (Math.max(Math.max(dice1,dice2),dice3)*100));
      }
  }
  ```

  