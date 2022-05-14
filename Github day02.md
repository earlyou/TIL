# 깃허브 특강
## 2022.04.08

> [1. Github](#1-github)<br/>
>
> ​	[1.1 원격 저장소(Remote Repository)](#11-원격-저장소remote-repository)<br/>
>
> ​	[1.2 Github에서 원격 저장소 생성](#12-github에서-원격-저장소-생성)<br/>
>
> ​	[1.3 로컬 저장소와 원격 저장소 연결](#13-로컬-저장소와-원격-저장소-연결)<br/>
>
> ​	[1.4 원격 저장소에 업로드](#14-원격-저장소에-업로드)<br/>
>
> [2. README.md](#2-readmemd)<br/>
>
> ​	[2.1 README.md란?](#21-readmemd란)<br/>
>
> ​	[2.2 README.md파일 push하기](#22-readmemd파일-push하기)<br/>
>
> [3. `.gitignore`](#3-gitignore)<br/>
>
> ​	[3.1 `.gitignore`](#31-gitignore)
>
> ​	[3.2 `.gitignore` 심화 내용](#32-gitignore-심화-내용)
>
> [4. clone, pull](#4-clone-pull)<br/>
>
> ​	[4.1 원격 저장소 가져오기](#41-원격-저장소-가져오기)
>
> [5. branch](#5-branch)<br/>
>
> ​	[5.1 Branch](#51-branch)
>
> ​	[5.2 Branch 실습](#52-branch-실습)
>
> [6. Branch-merge](#6-branch-merge)<br/>
>
> ​	[6.1 Branch Merge](#61-branch-merge)
>
> [7. Git Workflow](#7-git-workflow)<br/>
>
> ​	[7.1 원격 저장소 소유권이 있는 경우(Shared repository model)](#71-원격-저장소-소유권이-있는-경우shared-repository-model)
>
> ​	[7.2 원격 저장소 소유권이 없는 경우(Fork & Pull model)](#72-원격-저장소-소유권이-없는-경우fork--pull-model)
>
> ​	[7.3 Pull Request(PR) 자세히 알아보기](#73-pull-requestpr-자세히-알아보기)



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
   
   # 브랜치 생성과 이동을 동시에 실행 가능
   $ git switch -c login
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

      ![image](https://user-images.githubusercontent.com/103157377/168093918-b531379a-1b3c-4ad5-8711-652c5dc1ebb5.png)

   3. hotfix가 가리키는 C4는 C2에 기반한 커밋이므로 master가 C4로 이동한다.

      이렇게 따로 merge 과정 없이 브랜치의 포인터가 이동하는 것을 Fast-Foward라고 한다.

   4. 병합 후 필요없는 hotfix는 삭제

      ```bash
      $ git branch -d hotfix
      ```

<br/>

2. 3-Way Merge

   - 브랜치를 병합할 때 각 브랜치의 커밋 2개와 공통 조상 하나를 사용하여 병합하는 것
   - 두 브랜치에서 다른 파일 or 같은 파일의 다른 부분을 수정했을 때 가능

   1. 같은 조상을 가진 다른 커밋을 한 두 브랜치

      ![image](https://user-images.githubusercontent.com/103157377/168095398-64d6d332-e35c-442c-84c9-a33e4c336032.png)

   2. master에 iss53 병합

      ```bash
      $ git switch master
      
      $ git merge iss53
      ```

   3. 두 브랜치는 갈래가 나뉘어있기 때문에 Fast-Forward로 합칠 수 없다.

      C4, C5를 비교하여 3-way merge를 진행한다.

      ![image](https://user-images.githubusercontent.com/103157377/168096133-8cfbeb7c-75b2-443e-ae60-f691ff5733c7.png)

   4. 병합이 완료된 불필요한 iss53은 삭제

      ```bash
      $ git branch -d iss53
      ```

<br/>

3. Merge Conflict

   - 병합하는 두 브랜치에서 같은 파일의 부분을 수정한 경우, 병합하는 과정에서 충돌이 발생하는 현상
   - 사용자는 수정된 두 내용 중 선택을하여 Conflict를 직접 해결해야 한다.

   1. merge 전 상태

      ![image](https://user-images.githubusercontent.com/103157377/168098551-2d9d351f-0de8-436b-aba1-95156ab7547c.png)

   2. 만약 master와 iss53이 같은 파일의 같은 부분을 수정하고 병합한다면?

      ```bash
      # Conflict 발생
      
      $ git merge iss53
      Auto-merging index.html
      CONFLICT (content): Merge conflict in index.html
      Automatic merge failed; fix conflicts and then commit the result.
      ```

   3. 충돌 파일 확인을 위해 `git status`실행

      ```bash
      $ git status
      On branch master
      You have unmerged paths.
        (fix conflicts and run "git commit")
      
      Unmerged paths:
        (use "git add <file>..." to mark resolution)
      
          both modified:      index.html
      
      no changes added to commit (use "git add" and/or "git commit -a")
      ```

   4. index.html을 열면 충돌 내역 확인 가능

      ```bash
      <<<<<<< HEAD:index.html
      <div id="footer">contact : email.support@github.com</div>
      =======
      <div id="footer">
       please contact us at support@github.com
      </div>
      >>>>>>> iss53:index.html
      ```

   5. `=======`위로는 master내용, 아래는 iss53내용. 이 중 하나를 선택하거나, 둘 다 선택하거나, 아예 새롭게 작성 가능

      ```bash
      <div id="footer">
      please contact us at email.support@github.com
      </div>
      ```

   6. 이후 `git add`와 `git commit`을 통해 병합한 내용 커밋

      ```bash
      $ git add .
      $ git commit
      ```

   7. Vim 편집기를 통해 커밋 내역 수정 가능

      ```bash
      Merge branch 'iss53'
      
      Conflicts:
          index.html
      #
      # It looks like you may be committing a merge.
      # If this is not correct, please remove the file
      #	.git/MERGE_HEAD
      # and try again.
      
      
      # Please enter the commit message for your changes. Lines starting
      # with '#' will be ignored, and an empty message aborts the commit.
      # On branch master
      # All conflicts fixed but you are still merging.
      #
      # Changes to be committed:
      #	modified:   index.html
      #
      ```

   8. Vim 편집기를 통한 커밋이 C6커밋이 된다.

      ![image](https://user-images.githubusercontent.com/103157377/168100467-dcb9994e-136e-4744-ac86-1b9210f77491.png)

   9. iss53은 필요 없으므로 삭제

      ```bash
      $ git branch -d iss53
      ```

<br/>

### 7. Git Workflow

> branch를 통해 협업하는 두 가지 방법
>
> 1. 원격 저장소 소유권이 있는 경우(Shared repository model)
> 2. 원격 저장소 소유권이 없는 경우(Fork & Pull model)

#### 7.1 원격 저장소 소유권이 있는 경우(Shared repository model)

##### 7.1.1 개념

- 원격 저장소가 자신의 소유이거나 collaborator로 등록되어 있는 경우에 가능
- master에 직접 개발하는 것이 아니라, **기능별로 브랜치를 따로 만들어서** 개발
- `pull request`를 사용하여 팀원 간 변경 내용에 대한 소통 진행

##### 7.1.2 작업 흐름

1. 소유권이 있는 원격 저장소를 로컬 저장소로 `clone`

   ![image](https://user-images.githubusercontent.com/103157377/168103190-c714188f-5d13-4c6b-82c9-484514869da0.png)

   ```bash
   $ git clone https://github.com/edukyle/django-project.git
   ```

2. 사용자는 자신이 작업할 기능에 대한 **브랜치 생성**, 그 안에서 기능 구현

   ![image](https://user-images.githubusercontent.com/103157377/168103470-ea45cab9-7ce7-4573-8cdf-7603dba1d51c.png)

   ```bash
   $ git switch -c feature/login
   ```

3. 기능 구현이 완료되면, 원격 저장소에 해당 브랜치를 `push`한다.

   ![image](https://user-images.githubusercontent.com/103157377/168103769-4d487071-9848-4762-800e-9a4410efacc5.png)

   ```bash
   $ git push origin feature/login
   ```

4. 원격 저장소에는 master와 각 기능의 브랜치가 반영됨

   ![image](https://user-images.githubusercontent.com/103157377/168103906-51e447c9-52bb-451a-ace0-ab6a22c77aaa.png)

5. Pull Request를 통해 브랜치를 master에 반영해달라고 요청, 코드 리뷰를 통해 소통도 가능

   ![image](https://user-images.githubusercontent.com/103157377/168104185-9bb41f8c-382f-40be-90a9-e48447c3f744.png)

6. 병합이 완료되면 원격 저장소에서 병합이 완료된 브랜치는 불필요하므로 삭제

   ![image](https://user-images.githubusercontent.com/103157377/168104347-94683ffb-9032-4ea8-ade6-25a61ab06487.png)

7. master에 브랜치가 병합되면, 각 사용자는 로컬의 master 브랜치로 이동하고 `git pull`을 한다.

   ![image](https://user-images.githubusercontent.com/103157377/168104617-cf910814-6dc7-4111-8548-effbab366ef1.png)
   ![image](https://user-images.githubusercontent.com/103157377/168104640-78839fe2-47a1-400c-ae47-1b9db60ca00a.png)

   ```bash
   $ git switch master
   $ git pull origin master
   ```

8. 병합 완료 후, 기존 로컬 브랜치 삭제(한 사이클 종료)

   ![image](https://user-images.githubusercontent.com/103157377/168104854-b8122a58-6b57-4498-92e0-5860552b03c0.png)

   ```bash
   $ git branch -d feature/login
   ```

9. 새로운 기능 추가를 위해 새로운 브랜치를 생성하며 위 과정을 반복

   ![image](https://user-images.githubusercontent.com/103157377/168105021-fecd5d86-2eea-471e-a72d-afa94f1567ad.png)

   ```bash
   $ git switch -c feature/pay
   ```

<br/>

#### 7.2 원격 저장소 소유권이 없는 경우(Fork & Pull model)

##### 7.2.1 개념

- 오픈소스 프로젝트와 같이 자신의 소유가 아닌 원격 저장소인 경우 사용
- 원본 원격 저장소를 그대로 사용자의 원격 저장소에 복제(`fork`)
- 기능 완성 후 push는 복제한 사용자의 원격 저장소에 진행
- 이후 Pull Request를 통해 원본 원격 저장소에 반영될 수 있도록 요청

##### 7.2.2 작업 흐름

1. 소유권이 없는 원격 저장소를 `fork`를 통해 사용자의 원격 저장소로 복제

   ![image](https://user-images.githubusercontent.com/103157377/168106300-9234310d-16d8-4af2-876e-68fb854dcdc3.png)

   아래와 같이 Fork버튼을 누르면 자동으로 사용자의 원격 저장소에 복제

   ![image](https://user-images.githubusercontent.com/103157377/168106684-f406eb33-c52f-4235-a8d9-52e3bf333978.png)

2. `fork` 후 복제된 사용자의 원격 저장소를 로컬 저장소에 clone받는다.

   ![image](https://user-images.githubusercontent.com/103157377/168106889-79a34d51-7f7a-4d5b-87fc-253550ea12b8.png)

   ```bash
   $ git clone https://github.com/edukyle/kakao_clone.git
   ```

3. 이후에 로컬 저장소와 원본 원격 저장소를 동기화 하기 위해 연결

   ![image](https://user-images.githubusercontent.com/103157377/168107080-a16819f0-999b-4b18-b0cf-661316e21e1f.png)

   ```bash
   # 원본 원격 저장소에 대한 이름은 upstream으로 붙이는 것이 일종의 관례
   $ git remote add upstream https://github.com/AlexKwonPro/kakao_clone.git
   ```

4. 사용자가 작업할 기능에 대한 브랜치 생성, 그 안에서 기능 구현

   ![image](https://user-images.githubusercontent.com/103157377/168190131-7502f996-c2e0-4a85-9a81-3163c8828e38.png)

   ```bash
   $ git switch -c feature/login
   ```

5. 작업이 끝나면, 복제한 원격 저장소(origin)에 해당 브랜치를 `push`

   ![image](https://user-images.githubusercontent.com/103157377/168190200-b0af3c4c-3b20-4e2b-bfca-c0a58c60649a.png)

   ```bash
   $ git push origin feature/login
   ```

6. origin에는 master와 브랜치가 반영됨

   ![image](https://user-images.githubusercontent.com/103157377/168190250-1935370b-01b3-4647-85b7-d32dfdc1b1bf.png)

7. Pull Request를 통해 origin의 브랜치를 upstream의 master에 반영해 달라고 요청, upstream의 관리자가 코드 리뷰를 하고 반영 여부 결정

   ![image](https://user-images.githubusercontent.com/103157377/168190304-aa5fe39d-7379-4000-9f28-64c6f3378524.png)

8. upstream의 master에 브랜치가 병합되면 origin의 브랜치는 삭제, 로컬의 master 브랜치로 이동

   ![image](https://user-images.githubusercontent.com/103157377/168190372-fac9af44-1a9a-4da8-9e27-fb51fad7cf9e.png)

   ```bash
   $ git switch master
   ```

9. 변경된 upstream의 master내용을 로컬로 `pull`, 기존 로컬 브랜치는 삭제(한 사이클 종료)

   ![image](https://user-images.githubusercontent.com/103157377/168190465-626497ea-dda6-41f1-8c92-132d425a9f6e.png)

   ```bash
   $ git pull upstream master
   $ git branch -d feature/login
   ```

<br/>

#### 7.3 Pull Request(PR) 자세히 알아보기

1. 브랜치를 `push`하면 Compare & pull request라는 알림 버튼이 생기는데, 이를 클릭

   ![image](https://user-images.githubusercontent.com/103157377/168190683-236faeff-f930-4513-9700-15964fee1279.png)

2. 혹은 원격 저장소 상단 바에서 Pull requests → New pull request를 통해서도 가능

   ![image](https://user-images.githubusercontent.com/103157377/168190748-1fe3e796-e4e5-4667-b971-c1fbcd6d05cb.png)

3. base: 병합될 대상. master를 base로 둔다.

   compare: 병합할 대상. feature/login 브랜치를 compare로 둔다.

   아래쪽에서 비교 내용 확인, Create pull request 클릭

   ![image](https://user-images.githubusercontent.com/103157377/168196133-b6939b7b-ff15-4f5e-a467-e9b1b9d2b0dc.png)

4. Pull Request에 대한 제목과 내용, 각종 담당자를 지정하는 페이지

   모두 작성 후, Create pull request 눌러서 PR 생성

   ![image](https://user-images.githubusercontent.com/103157377/168196202-cbfc20fa-9f0f-4b3e-b1ee-6178ce63356e.png)

   Reviewer: 현재 PR에 대해 코드 리뷰를 진행해 줄 담당자

   Assigneers: 현재 PR에 대한 작업을 맡고 있는 담당자

5. PR이 생성되면 다음과 같은 화면 생성. 빨간 표시가 된 세 부분 확인

   ![image](https://user-images.githubusercontent.com/103157377/168196365-504a2f19-3a86-490b-b3d3-7fbfcc24e57c.png)

6. Conversation: 아래 Write부분에서 comment를 별도 작성 가능. "Merge pull request"버튼을 누르면 병합 시작.

   ![image](https://user-images.githubusercontent.com/103157377/168208028-7d83b2ce-eff9-4024-948a-8973a2e2051d.png)

7. Commits: PR을 통해 반영될 커밋들을 볼 수 있다.

   ![image](https://user-images.githubusercontent.com/103157377/168208110-f4b56443-2e58-4bda-869b-d31ff3c2df80.png)

8. Files changed: 파일의 변화 내역 확인

   ![image](https://user-images.githubusercontent.com/103157377/168208151-9a1ceaf0-31ec-46f8-9673-bf051757089d.png)

9. 코드리뷰을 원하는 라인에서 "+"를 눌러 해당 라인에 리뷰 남기기 가능. 빨간 사각형 안 작은 아이콘을 누르면 Suggestion 기능을 넣을 수 있다.

   ![image](https://user-images.githubusercontent.com/103157377/168208299-cd6d552b-2202-497f-b1d8-c9c1de50fe4d.png)

10. 코드 리뷰가 끝나면 Finish your review 클릭, 옵션을 선택하고 Submit review 클릭

   ![image](https://user-images.githubusercontent.com/103157377/168208378-43f8106e-82fe-4be4-8cdd-06bd77f915a7.png)

   - Comment: 추가적인 comment 작성
   - Approve: merge를 승인하는 경우 선택
   - Request change: 수정해야 하는 사항이 있을 경우 선택

11. Conversation으로 돌아가면 리뷰가 나타난다.

    ![image](https://user-images.githubusercontent.com/103157377/168208493-38ab02cd-b6dc-47f7-84a2-29e6f0abefcf.png)

12. 병합을 하고 보라색으로 병합이 완료됐다고 나오면 성공

    Delete branch 버튼을 통해 병합된 feature/login 브랜치 삭제 가능(origin에서만 삭제)

    ![image](https://user-images.githubusercontent.com/103157377/168208611-4b5b0c7b-6151-49ca-8e7c-2739aedc878e.png)
    
13. master를 확인하면 feature/login 내용이 master에 병합된 것을 확인할 수 있다.

    ![image](https://user-images.githubusercontent.com/103157377/168410633-12170a38-bcbc-4f12-bd09-c75c78f15b38.png)

14. 이후 로컬 저장소의 master 브랜치에서 git pull을 이용해 로컬과 원격을 동기화.

15. 정리: `fork` → `clone` → 브랜치 생성 → `add` → `commit` → 브랜치 `push` → `pull&request`보내기

