# Arduino-Using VSCode for Arduino(VSCode로 아두이노 개발환경 만들기)

## 2022-09-02

>[1. VSCode 사용 이유](#1-vscode-사용-이유)
>
>[2. 개발환경 구성](#2-개발환경-구성)
>
>​	[2.1 Arduino IDE 설치](#21-arduino-ide-설치)
>​	[2.2 VSCode에서 Arduino Extension 설치](#22-vscode에서-arduino-extension-설치)
>​	[2.3 VSCode 아두이노 환경 설정하기](#23-vscode-아두이노-환경-설정하기)
>​	[2.4 프로젝트 생성, 빌드, 다운로드](#24-프로젝트-생성-소스코드-업로드)
>
>[3. 추가 설정(선택)](#3-추가-설정선택)
>​	[3.1 빌드 출력 파일 경로 지정](#31-빌드-출력-파일-경로-지정)

<br/>

### 1. VSCode 사용 이유

- 아두이노 전용 IDE가 있지만 Visual Studio Code를 사용하는 이유
  - 낮은 가독성
  - 코드 자동완성 기능 없음
  - 코드 탐색 기능 없음
  - 디버깅모드 없음



### 2. 개발환경 구성

- [Visual Studio Code](https://code.visualstudio.com/download)가 이미 설치가 되어 있다는 전제 하에 진행

#### 2.1 Arduino IDE 설치

- Arduino IDE 다운로드 [링크](https://www.arduino.cc/en/Main/Software)

- Installer 다운로드 권장

​	![image](https://user-images.githubusercontent.com/103157377/188250583-cb919de0-964d-4c06-a667-c7a4cba8764c.png)

- 설치 과정은 생략

<br/>

#### 2.2 VSCode에서 Arduino Extension 설치

- **Arduino는 C언어 기반이기 때문에 C/C++ Extensions도 같이 설치해야 한다.**(중요!)

- 원하는 폴더에 우클릭 &rarr; 'Code(으)로 열기' 클릭

  ![image](https://user-images.githubusercontent.com/103157377/188250739-9dff68df-ab21-4411-b5b5-63c381ca4470.png)

- 좌측 사이드바에서 'Extensions' 아이콘 클릭

- 검색 칸에 'Arduino' 검색

- Microsoft사의 'Arduino for Visual Studio Code' 선택

- Install 클릭하여 설치

  ![image](https://user-images.githubusercontent.com/103157377/188250882-acbfa3d0-3625-4f16-87b3-a15d3b970f72.png)

<br/>

#### 2.3 VSCode 아두이노 환경 설정하기

- VSCode에서 `Ctrl + ,`로 설정환경 진입

- 'Extensions' 클릭 &rarr; 'Arduino configuration' 클릭

- 'Edit in settings.json' 클릭

  ![image](https://user-images.githubusercontent.com/103157377/188251004-2bd58a4b-e0fa-43cd-b650-eeebf1694570.png)

- settings.json에 아래 코드 삽입, 저장

  ```json
  {
  	"arduino.path": "C:/Program Files (x86)/Arduino",
  	"arduino.commandPath": "arduino_debug.exe",
   	"arduino.logLevel": "info",
  	"arduino.allowPDEFiletype": false,
  	"arduino.enableUSBDetection": true,
  	"arduino.disableTestingOpen": false,
  	"arduino.skipHeaderProvider": false,
  	"arduino.additionalUrls": [
  		"https://raw.githubusercontent.com/VSChina/azureiotdevkit_tools/master/package_azureboard_index.json",
  		"http://arduino.esp8266.com/stable/package_esp8266com_index.json"
  	],
  	"arduino.defaultBaudRate": 115200
  }
  ```

  ![image](https://user-images.githubusercontent.com/103157377/188251121-a82805d5-834c-4a82-91fe-b60d11ebf5ab.png)

&check;	아두이노 설정 코드에서 arduino.path의 값이 자신의 PC에 아두이노가 설치된 경로가 맞는지 확인 필요

<br/>

#### 2.4 프로젝트 생성, 소스코드 업로드

- 진행하기 전에 아두이노 보드와 PC를 연결한 상태로 진행

​	![image](https://user-images.githubusercontent.com/103157377/188251403-4720b0c4-efdb-4fb6-ba94-916da55029bf.png)

<br/>

##### 2.4.1 프로젝트 생성

- VSCode에서 `F1`을 누른 후 'Arduino: Initialize' 선택

  ![image](https://user-images.githubusercontent.com/103157377/188251454-5cc89fde-f51b-4404-8ad9-cd2b318423ef.png)

- 원하는 파일 명을 입력하고 `Enter`, or 우클릭 &rarr; 'New File...'로 새 파일 생성해도 된다.

  ![image](https://user-images.githubusercontent.com/103157377/188251535-f72e9d74-cbe5-4f5e-9dbd-5bf836264852.png)

<br/>

##### 2.4.2 보드, 포트 설정

- 아두이노 보드 선택

  ![image](https://user-images.githubusercontent.com/103157377/188251642-e70ca775-d5ef-4b0e-87e6-ac6aa9e4adce.png)

- 자신이 사용하는 보드 선택

  ![image](https://user-images.githubusercontent.com/103157377/188251725-c1351e2a-d173-4ecc-a5a5-42cf527811ba.png)

- OUTPUT에 로그가 뜬다

  ![image](https://user-images.githubusercontent.com/103157377/188251707-67ab6041-eb97-4715-8d67-53cee14ab179.png)

- 포트 선택

  ![image](https://user-images.githubusercontent.com/103157377/188251795-696ad7e8-6604-4eff-8b96-1674584175b3.png)

- 인식되는 포트 선택

  ![image](https://user-images.githubusercontent.com/103157377/188251835-04af4cb8-1d96-492c-b530-3190f10352ac.png)

<br/>

##### 2.4.3 소스코드 업로드

- 간단한 코드 작성

  ```c
  void setup()
  {
  	pinMode(13,OUTPUT);     // 13번 핀 사용
  }
  
  void loop()                 // 무한 반복
  {
  	digitalWrite(13,HIGH);  // 13번 핀에 5V 전압 설정
      delay(500);             // 500ms 대기
      digitalWrite(13,LOW);   // 13번 핀 전류 차단
      delay(500);             // 500ms 대기
  }
  ```

- 업로드 버튼 클릭

  ![image](https://user-images.githubusercontent.com/103157377/188252317-2d8c9e95-aa96-41dc-8fbf-433bb98430ea.png)

- 실행 결과 확인

  ![arduino testing](https://user-images.githubusercontent.com/103157377/188252248-93489141-a4e6-40b2-b911-47a3c968835c.gif)

  

<br />

### 3. 추가 설정(선택)

- 빌드 결과 폴더를 지정하기 위해 .vscode/arduino.json 경로로 들어가 파일 수정
- 빌드 결과 폴더를 지정하지 않아도 문제는 없지만 빌드시 임시 폴더 생성하는데 시간이 소요됨, 결과물 파일을 찾을 수 없다는 단점

<br/>

#### 3.1 빌드 출력 파일 경로 지정

- .vscode/arduino.json 경로로 들어가 파일 열기

- 빌드 결과 저장 폴더를 지정하는 코드 추가

  ```json
  {
      "sketch": "app.ino",
      "output": "build",
      "board": "arduino:avr:uno",
      "port": "COM3"
  }
  ```

- 오류 발생 시 나머지 추가 설정은 [링크](https://juahnpop.tistory.com/71) 참고