# 깃허브 특강
## 2022.04.08

>



### 1. Github

#### 1.1 원격 저장소(Remote Repository)

- Git의 주요 목적 중 하나인 협업을 위해 로컬 저장소와 원격 저장소의 연동

#### 1.2 Github에서 원격 저장소 생성

![화면 오른쪽 상단 (+)버튼을 누르고 New Repository 클릭](https://user-images.githubusercontent.com/103157377/167742810-ccf732e3-24af-43cd-bb27-a4085a1de9e1.png)

- 화면 오른쪽 상단 (+)버튼을 누르고 New Repository 클릭

![image](https://user-images.githubusercontent.com/103157377/168068958-5bccf8ad-d1b3-4b2e-91bf-463628612af7.png)

- 저장소의 이름, 설명, 공개 여부를 선택하고 Create repository를 클릭

<br/>

#### 1.3 로컬 저장소와 원격 저장소 연결

1. 원격 저장소가 잘 생성되었는지 확인 후, 저장소의 주소를 복사

   ![image](https://user-images.githubusercontent.com/103157377/168069557-01434f13-9869-4214-8684-4e97670cebf4.png)

2. 홈 디렉토리의 폴더에서 VScode 열기

3. `git init`을 통해 폴더를 로컬 저장소로 만들기

   ```bash
   $ git init
   ```

4. `git remote `

   1. 등록: `git remote add <이름> <주소>`

      ```bash
      $ git remote add origin https://github.com/earlyou/TIL.git
      ```

   2. 조회

      ```bash
      $ git remote -v
      ```

   3. 삭제

      연결을 끊는 것이지, 저장소를 삭제 하는 것이 아니다.

      ```bash
      $ git remote rm origin
      $ git remote remove origin
      ```

<br/>

#### 1.4 원격 저장소에 업로드

- 커밋을 원격저장소에 업로드 하는 것.
- 로컬 저장소에서 커밋을 생성해야 업로드할 수 있다.

1. 로컬 저장소에서 커밋 생성

   ```bash
   $ git add a.txt
   
   $ git commit -m "first commit"
   
   # 커밋 확인
   $ git log --oneline
   ```

2. `git push`

   - 로컬 저장소의 커밋을 원격 저장소에 업로드하는 명령어
   - `git push <저장소 이름> <브랜치 이름>`
   - `-u`를 사용하면 두 번째 푸쉬 부터는 저장소 이름과 브랜치 이름 생략 가능

   ```bash
   $ git push origin master
   
   $ git push -u origin master
   $ git push
   ```

3. vscode 자격 증명

   - 처음으로 원격 저장소와 연동을 할 때는 `push`하려는 사용자가 로그인을 함으로써 자격을 증명한다.

   ![image](https://user-images.githubusercontent.com/103157377/168071589-e8012338-dd73-4a99-b127-5acc6c57bc34.png)

   - Sign in with your browser

   ![image](https://user-images.githubusercontent.com/103157377/168071709-7b457826-e9e6-4d71-9d76-da0226746905.png)

   - Authorize GitCredentialManager

   ![image](https://user-images.githubusercontent.com/103157377/168071800-ee78b247-5836-4350-ac9f-ebeae0f5b606.png)

   - 증명 완료 후 git push 완료

4.  원격 저장소에서 정상 업로드 확인

   ![image](https://user-images.githubusercontent.com/103157377/168072093-41cb660b-bf91-42e0-9914-f692491fa27a.png)

<br/>

### 2. README.md

#### 2.1 README.md란?

- README.md 는 원격 저장소의 소개와 설명이 담겨있는 대문 역할
- 반드시 이름을 README.md로 해야 Github가 인식

<br/>

#### 2.2 README.md파일 push하기

```bash
$ git touch README.md

$ git add README.md

$ git commit -m "README.md"

$ git push origin master
```

- 예시

  ![image](https://user-images.githubusercontent.com/103157377/168073792-b6de4c83-226f-433b-8603-1629c4c35a98.png)

  [출처: https://github.com/namjunemy/TIL](https://github.com/namjunemy/TIL)

<br/>

### 3. `.gitignore`

#### 3.1 `.gitignore`

- 특정 파일 혹은 폴더에 대해 Git이 버전 관리를 하지 못하도록 지정하는 파일

1. `.gitignore`에 작성하는 목록

   - 민감한 개인 정보가 담긴 파일(전화번호, 계좌번호, 비밀번호, API KEY 등)
   - OS에서 활용되는 파일
   - IDE(Eclipse 등)혹은 Text editor(vscode 등) 등에서 활용되는 파일
   - 개발 언어(Java) 혹은 프레임워크에서 사용되는 파일

2. `.gitignore` 작성 시 주의 사항

   - 반드시 파일 이름을 `.gitignore`로 생성
   - `git add`하기 전에 미리 `.gitignore`작성 필수

3. `.gitignore` 쉽게 작성하기

   - 사이트에서 자신의 개발 환경에 맞는 것을 선택, 검색 후 전체 복사 후 붙여넣기

   - [https://www.toptal.com/developers/gitignore/](https://www.toptal.com/developers/gitignore/)
   - [gitignore 저장소](https://github.com/github/gitignore)

<br/>

#### 3.2 `.gitignore` 심화 내용

- .gitignore 패턴 규칙
  1. 아무것도 없는 라인이나, `#`로 시작하는 라인은 무시
  2. 슬래시(/)로 시작하면 하위 디렉터리에 재귀적으로 적용되지 않음
  3. 디렉터리는 슬래시(/)를 끝에 사용하는 것으로 표현
  4. 느낌표(!)로 시작하는 패턴의 파일은 ignore(무시)하지 않음
  5. 표준 Glob 패턴을 사용
     - `*(asterisk)`는 문자가 하나도 없거나 하나 이상을 의미
     - `[abc]`는 중괄호 안에 있는 문자 중 하나를 의미.
     - 물음표(?)는 문자 하나를 의미
     - `[0-9]`처럼 중괄호 안에 하이픈(-)이 있는 경우 0에서 9사이의 문자 중 하나를 의미
     - `**(2개의 asterisk)`는 디렉터리 내부의 디렉터리까지 지정 가능, (`a/**/z`라고 작성하면 `a/z`, `a/b/z`, `a/b/c/z` 까지 모두 영향.)

- 패턴 예시

  ```shell
  # .gitignore
  
  # 확장자가 txt인 파일 무시
  *.txt
  
  # 현재 확장자가 txt인 파일이 무시되지만, 느낌표를 사용하여 test.txt는 무시하지 않음
  !test.txt
  
  # 현재 디렉터리에 있는 TODO 파일은 무시하고, folder/TODO 처럼 하위 디렉터리에 있는 파일은 무시하지 않음
  /TODO
  
  # build/ 디렉터리에 있는 모든 파일은 무시
  build/
  
  # folder/notes.txt 파일은 무시하고 folder/child/arch.txt 파일은 무시하지 않음
  folder/*.txt
  
  # folder 디렉터리 아래의 모든 .pdf 파일을 무시
  folder/**/*.pdf
  ```

<br/>

### 4. clone, pull

#### 4.1 원격 저장소 가져오기

1. `git clone`

   - 원격 저장소 안에 있는 내역을 모두 가져와, 로컬 저장소를 새로 생성한다.

   - 원격 저장소를 통째로 복사해서 옮기는 것으로 완전 새로운 환경에서 원격 저장소에 접근할 때 쓰는 명령어이다.

   - `git clone <원격 저장소 주소>`

     ```bash
     $ git clone https://github.com/earlyou/TIL.git
     ```

   - clone되어 생성된 로컬 저장소는 `git init`과 `git remote add`가 이미 수행되어있다.

2. `git pull`

   - 원격 저장소와 로컬 저장소가 이미 연동이 돼있는 상태에서, 원격 저장소에서만 변경사항이 일어났을 때 쓰는 명령어

   - 원격 저장소의 변경사항을 가져와 로컬 저장소를 업데이트한다.

   - `git pull <저장소 이름> <브랜치 이름>`

     ```bash
     $ git pull origin master
     ```

<br/>

### 5. Branch

#### 5.1 Branch

1. Branch란?

   ![image](https://user-images.githubusercontent.com/103157377/168079105-66250a74-f532-48a5-86a0-c6a1091390ce.png)

   - 브랜치란 나뭇가지처럼 작업 공간을 여러 갈래로 나누어 독립적으로 작업할 수 있도록 도와주는 도구이다.
   - 장점
     1. 브랜치는 독립 공간을 형성하기 때문에 원본(master)에 영향을 주지 않아 안전
     2. 하나의 작업은 하나의 브랜치로 나누어 진행되므로 체계적 개발 가능
     3. Git은 브랜치 만드는 속도도 빠르고 용량도 적게 든다.
   - 써야하는 이유
     1. master 브랜치는 상용이기 때문에 항상 사용자에게 공개된 상태이다.
     2. 업데이트를 하거나 디버깅을 할 때, master를 함부로 건들면 사용자에게 치명적인 영향을 끼칠 수 있다.
     3. 따라서 별도의 브랜치를 만들어서 작업을 진행한다면 사용자에게 전혀 영향을 주지 않는 상태로 업데이트 작업이나 디버깅 작업을 할 수 있다.

2. `git branch`

   - 조회, 생성, 삭제 등

   ```bash
   # 브랜치 목록 확인
   $ git branch
   
   # 원격 저장소의 브랜치 목록 확인
   $ git branch -r
   
   # 새로운 브랜치 생성
   $ git branch <브랜치 이름>
   
   # 특정 커밋 기준으로 브랜치 생성
   $ git branch <브랜치 이름> <커밋 ID>
   
   # 특정 브랜치 삭제
   $ git branch -d <브랜치 이름> # 병합된 브랜치만 삭제 가능
   $ git branch -D <브랜치 이름> # (주의) 강제 삭제 (병합되지 않은 브랜치도 삭제 가능)
   ```

3. `git switch`

   - 다른 브랜치로 HEAD를 이동시키는 명령어
   - HEAD: 현재 브랜치를 가리키는 포인터

   ```bash
   # 다른 브랜치로 이동
   $ git switch <다른 브랜치 이름>
   
   # 브랜치를 새로 생성과 동시에 이동
   $ git switch -c <브랜치 이름>
   
   # 특정 커밋 기준으로 브랜치 생성과 동시에 이동
   $ git switch -c <브랜치 이름> <커밋 ID>
   ```

   <br/>

#### 5.2 Branch 실습

##### 5.2.1 사전 세팅

1. test.txt 생성 후 3개의 커밋 생성

   ```bash
   $ touch test.txt
   
   # test.txt에 master-1 작성
   $ git add .
   $ git commit -m "master-1"
   
   # test.txt에 master-2 작성
   $ git add .
   $ git commit -m "master-2"
   
   # test.txt에 master-3 작성
   $ git add .
   $ git commit -m "master-3"
   ```

2. `git log --oneline`으로 커밋 확인

   ```bash
   $ git log --oneline
   0604dcd (HEAD -> master) master-3
   9c22c89 master-2
   3d71510 master-1
   ```

3. 현재 상황

   ![image](https://user-images.githubusercontent.com/103157377/168082314-456cc3b0-e8a6-4566-b85a-8ba703b0c698.png)

<br/>

##### 5.2.2 브랜치 생성, 조회

1. login이라는 이름으로 브랜치 생성

   ```bash
   $ git branch login
   ```

2. 브랜치가 생성되었는지 확인

   ```bash
   $ git branch
     login
   * master
   # 아직 HEAD가 master를 가리키고있다.
   ```

3. `git log --oneline` 으로 확인

   ```bash
   $ git log --oneline
   0604dcd (HEAD -> master, login) master-3
   9c22c89 master-2
   3d71510 master-1
   ```

4. master 브랜치에 1커밋 작성

   ```bash
   $ git add .
   $ git commit -m "master-4"
   ```

5. 현재 상태

   ```bash
   $ git log --oneline
   5ca7701 (HEAD -> master) master-4
   0604dcd (login) master-3
   9c22c89 master-2
   3d71510 master-1
   ```

   ![image](https://user-images.githubusercontent.com/103157377/168083270-81c12760-0d5a-446d-87e3-44c8c361b3d3.png)

<br/>

##### 5.2.3 브랜치 이동

1. login으로 브랜치 이동

   ```bash
   $ git switch login
   ```

2. test.txt를 열어보면 master-4가 지워져있다.

   ```bash
   # login 브랜치의 test.txt
   master-1
   master-2
   master-3
   ```

3. `git log --oneline`

   ```bash
   $ git log --oneline
   0604dcd (HEAD -> login) master-3
   9c22c89 master-2
   3d71510 master-1
   ```

4.  master 브랜치가 보이지는 않지만 브랜치를 조회해보면 master가 보인다.

   ```bash
   $ git branch
   * login
     master
   ```

5. `git log --oneline -all` 현재 상태

   ```bash
   $ git log --oneline --all
   5ca7701 (master) master-4
   0604dcd (HEAD -> login) master-3
   9c22c89 master-2
   3d71510 master-1
   ```

   ![image](https://user-images.githubusercontent.com/103157377/168084201-19b6e26f-ad54-443e-8dc2-5f126fe59878.png)

<br/>

##### 5.2.4 login 브랜치에 커밋 생성

1. test.txt에 login-1 작성

   ```bash
   # login 브랜치의 test.txt
   master-1
   master-2
   master-3
   login-1
   ```

2. test_login.txt 생성 후 login-1이라고 작성

   ```bash
   $ touch test_login.txt
   
   # test_login.txt에 작성
   login-1
   ```

3. 커밋

   ```bash
   $ git add .
   $ git commit -m "login-1"
   ```

4. `git log --oneline --all --graph`로 현재 상황 조회하기

   ```bash
   $ git log --oneline --graph --all
   * 3b0a091 (HEAD -> login) login-1
   | * 5ca7701 (master) master-4
   |/
   * 0604dcd master-3
   * 9c22c89 master-2
   * 3d71510 master-1
   ```

   ![image](https://user-images.githubusercontent.com/103157377/168084823-e291a913-6f4b-49ca-98d8-4e8b5e337c99.png)

<br/>

### 6. Branch-merge

#### 6.1 Branch Merge

- 각 브랜치에서 작업 끝난 후 master에 변경사항 반영하기

##### 6.1.1 `git merge`

- 브랜치를 합치는 명령어

- `git merge <합칠 브랜치 이름>`

- merge하기 전에 메인 브랜치로 switch해야 한다.

  ```bash
  # 1. 현재 branch1과 branch2가 있고, HEAD가 가리키는 곳은 branch1 입니다.
  $ git branch
  * branch1
    branch2
  
  # 2. branch2를 branch1에 합치려면?
  $ git merge branch2
  
  # 3. branch1을 branch2에 합치려면?
  $ git switch branch2
  $ git merge branch1
  ```

<br/>

##### 6.1.2 Merge의 세 종류

1. Fast-Forward

   - 브랜치를 병합할 때, '빠르게 감기'처럼 브랜치가 가리키는 커밋을 앞으로 이동시키는 것

   1. master는 C2 커밋을, hotfix는 C4 커밋을 가리키고 있을 때

      ![image](https://user-images.githubusercontent.com/103157377/168086374-22694008-40fc-43e4-b043-6dfdb9ad7574.png)

   2. master에 hotfix를 병합한다면?

      ```bash
      $ git switch master
      $ git merge hotfix
      Updating s1d5f1s..1325sd4
      Fast-forward
       index.html | 2 ++
       1 file changed, 2 insertions(+)
      ```

      

