# 깃허브 특강
## 2022.04.07

[강의자료 링크](https://hphk.notion.site/hphk/Git-22-04-07-22-04-08-AI-14-83024d717d9b41a7b76636858f95a21b)

> git을 쓰는 이유
>
> - 버전관리
> - 포트폴리오
>
> git 사전지식
>
> - git bash
> - VScode
> - Markdown
>
> git 기초
>
> - 작동 원리
> - `init`, `status`, `add`, `commit`, `log`



### 1. Why

#### 1.1  git 이용한 버전 관리
- 분산 버전 관리 프로그램
- 버전관리 하는 이유: 백업, 복구, 협업
- (변경사항+변경된 버전)SnapShot 관리
- (변경사항+최종버전)Delta 관리
<br/>
1. 중앙 집중식 버전 관리(SVN)
- 서버 컴퓨터(클라우드 등)에서 버전 관리, 개발자들이 수정해서 업로드
- 서로 갖고있는 버전이 다르기 때문에 서버 컴퓨터 손상 시 복구 불가능
<br/>
2. 분산 버전 관리(git)
- 서버 컴퓨터에 있는 버전과 개발자들이 갖고 있는 버전이 동일
- 서버 컴퓨터 손상되어도 복구 가능
<br/>
#### 1.2 github를 이용한 포트폴리오
[포트폴리오 예시](https://github.com/jojoldu)
	- github = Social Coding
	- SNS 역할이 아닌 협업을 위한 도구
	- github = GitLab = Bitbucket
<br/><br/>

### 2. 사전 지식
#### 2.1 Git Bash 쓰기
![image](https://user-images.githubusercontent.com/103157377/167625300-ec58131e-c1f5-4321-87ac-4ba71ac9aa1b.png)

| CLI  | GUI  |
| ---- | ---- |

Git을 사용할 땐 CLI 환경을 써야 한다.

Git Bash 명령어 정리

| touch a.txt |         a.txt 만들기         |
| :---------: | :--------------------------: |
|  rm. atxt   |       a.txt 완전 삭제        |
|  mkdir CLI  |       CLI 폴더 만들기        |
|     ls      |     구성파일, 폴더 표시      |
|  ctrl + L   |         화면 깨끗이          |
|   cd CLI    |      CLI폴더로 들어가기      |
|    ls -a    | 숨김폴더, 상위항목 전부 표시 |
|    cd ..    |       상위 폴더로 이동       |
|    cd .     |       현재 폴더로 이동       |
|  rm -r CLI  |         폴더 지우기          |

<br/>

#### 2.2 VScode 사용하기

<img src="https://user-images.githubusercontent.com/103157377/167627013-75f8e03f-d3d3-4062-a369-b295e24e6554.png" alt="image" style="zoom:50%;" />

원하는 디렉토리에서 우클릭 후 'Code로 열기' 클릭

![image](https://user-images.githubusercontent.com/103157377/167627475-e798a81d-c2ec-4a25-9d44-cb539d8e41e0.png)

ctrl + `을 눌러서 git 터미널 열기 가능

<br/>

#### 2.3 Markdown

##### 2.3.1 마크 다운이란?

- 마크업과 반대인 개념이 아니라, 마크다운은 마크업의 부분집합
- 경량 마크업이라고도 한다.
- 글에 역할을 부여하는 작업니다.(제목, 본문, 인용 등)
- Github에 마크다운을 쓰기 위해서 배운다.

<br/>

##### 2.3.2 마크다운 장, 단점

1. 장점
   - 쉽고 직관적인 문법
   - 쉬운 관리
   - 다양한 지원 가능한 플랫폼과 프로그램

2. 단점

   - 표준이 없어서 사용자마다 다른 문법
   - 모든 HTML 마크업 기능 대체 불가능

3. 주의사항

   - 마크다운의 목적은 글에 역할을 부여하는 것
   - 글씨 크기를 키우고 싶다는 이유로 내용에 제목 역할 부여하면 안된다.

   <br/>

##### 2.3.3 마크 다운 문법 종류

|                문법                 |               개요                |                       설명                        |
| :---------------------------------: | :-------------------------------: | :-----------------------------------------------: |
|            #[space]text             |              제목 1               | #개수가 늘어날 수록 글자가 작아진다. 6개까지 가능 |
|              -[space]               |            목록 만들기            |                                                   |
|                [tab]                |             들여쓰기              |             목록이나 문단을 들여쓴다              |
|            [shift]+[tab]            |        목록 들여쓰기 취소         |                                                   |
|           \[Enter][Enter]           |           목록 탈출하기           |                                                   |
|              1.[space]              |         번호 목록 만들기          |                                                   |
|              \*text\*               |              *text*               |                     기울임체                      |
|             \*\*text\**             |             **text**              |                       굵게                        |
|             \~~text\~~              |             ~~text~~              |                      취소선                       |
|     \`println("Hello World")\`      |     `println("Hello World")`      |       인라인 코드, 소스코드 한 줄 표현 가능       |
| \```for a in range(5): print(i)\``` | ```for a in range(5): print(i)``` |       블록 코드, 소스코드 여러 줄 표현 가능       |
|              ctrl + /               |      마크다운 소스코드 보기       |                                                   |
|            \|--------\|             |             표 만들기             |                                                   |
|                  \                  |  뒤에 나오는 문자 그대로 적힌다   |         문법을 무시하고 그대로 표현된다.          |
|        \!\[text]\(image url)        |            이미지 삽입            |                text는 대체 텍스트                 |
|                  >                  |             인용 표현             |                                                   |
|         \[text]\(link url)          |             링크삽입              |              링크가 text로 표시된다.              |
|            ---, ***, ___            |              수평선               |                                                   |

<br/>

### 3. Git 기초

#### 3.1 작동 원리

1. git은 크게 3가지로 구성된다.
   1. Working Directory
   2. Staging Area
   3. git Repository

Working Directory는 사용자가 작업하는 공간이다. 만약 여기서 a.txt를 만들어 편집하고 저장한다고 하자. 이 저장한 파일을 Staging Area로 add 해서 버전관리 준비를 하고 마지막으로  commit을 해 Repository로 보냄으로써 버전관리가 되는 것이다.



#### 3.2 실습

##### 3.2.1 Git 초기 설정

> 최초 한 번만 설정

1. 누가 Commit을 했는지 확인할 수 있도록 사용자 이름과 이메일을 설정
2. 수정하고 싶을 때 이름, 이메일 주소만 바꿔서 다시 입력할 수 있다.

```bash
$ git config --global user.name "이름"
$ git config --global user.email "메일 주소"
```

3. 올바르게 설정 되었는지 확인 가능

```bash
$ git config --global -l
$ git config --global --list
```

<br/>

##### 3.2.2 Git 기본 명령어

1. git init

```bash
$ git init
```

- 현재 작업 중인 Directory를 git으로 관리한다는 뜻이다.

- `.git`이라는 숨김 폴더를 생성하고, 터미널에는 아래와 같이 표기된다.

```bash
Initialized empty Git repository in C:/Users/kyle/git-practice/.git/

kyle@KYLE MINGW64 ~/git-practice (master)
```

<br/>

2. git status

```bash
$ git status
```

- Working Directory와 Staging Area에 있는 파일들의 상태를 알려주는 명령어

- 수시로 status를 확인하여 파일들의 상태를 조회하는 것이 중요하다.

- `Untracked`: Git이 관리하지 않는 파일

- `Tracked`: Git이 관리하는 파일

  a. `Unmodified`: 최신 상태

  b. `Modified`: 수정되었지만 Staging Area에 반영되지 않은 상태

  c. `Staged`: Staging Area에 올라간 상태

![image](https://user-images.githubusercontent.com/103157377/167634382-def4dbb8-d8e0-4cd0-8522-81d0ecd5c25c.png)

<br/>

##### 3.2.3 git add

```bash
# 특정 파일
$ git add a.txt

# 특정 폴더
$ git add my_folder/

# 현재 디렉토리에 속한 파일/폴더 전부
$ git add .
```

- 수정된 Working Directory에 있는 파일을 Staging Area로 올리는 명령어
- Git이 해당 파일을 추적(관리)할 수 있도록 만듦
- 파일 상태를 `Staged`로 변경

<br/>

##### 3.2.4 git commit

```bash
$ git commit -m "text"
```

- Staging Area에 있는 파일의 변경사항을 하나의 버전(커밋)으로 저장하는 명령어
- `"text"`는 버전관리를 위해 해당 버전에 이름을 붙히는 것으로 버전의 특성에 맞게 텍스트를 적는 것을 권장
- 각각의 커밋은 SHA-1 알고리즘에 의해 고유 해시 ID를 갖는다.

<br/>

##### 3.2.5 git log

```bash
$ git log
$ git log --oneline
$ git log --graph
$ git log --all
$ git log --reverse
$ git log -p
$ git log -2
```

- 커밋의 내역(ID, 작성자, 시간, 메시지) 조회
  - `oneline`: 한 줄로 요약
  - `--graph`: branch와 merge를 그래프로 표현
  - `--all`: 모든 branch 내역 표현
  - `--reverse`: 커밋 내역의 순서를 오래된 순으로 조회
  - `-p`: 파일 변경 내용 같이 조회
  - `-2`: 원하는 갯수 만큼 내역 조회(임의 숫자 가능)
