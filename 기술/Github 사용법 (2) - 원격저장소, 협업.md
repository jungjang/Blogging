### [2] github 사용법 ( github , 원격레포 )
* github.com은 기본 브랜치 이름을 main으로 강요한다.

---

원격 repository 개념<br>
git : 버전 관리 프로그램<br>
repository(저장소) : git이 파일 히스토리를 저장해두는 장소<br>
-> 그런데 내 컴퓨터 박살나면 자료날라가잖아? 불안하잖아?<br>
-> 따라서 온라인에 repository를 만들어서 안정성 확보한다.<br>

온라인 repository (원격저장소) 만들면<br>
1) 컴퓨터 고장나도 안심<br>
2) 협업이 가능하다.<br>

---

### 1. 깃헙에서 new repository 생성

### 2. 내 코드 올릴 때 ( 즉, 로컬 저장소를 원격 저장소에 백업하기 ( 백업은 깃헙 사용의 1차적 이유 ) )
 1) git init을 통해 로컬 repository 생성
 2) git branch -M main 을 통해 기본 브랜치 이름을 main으로 변경
     (* github.com은 기본 브랜치 이름을 main으로 강요한다.)
 3) 코드 작성, 커밋 후
 4) git remote add origin 원격레포지토리주소 
 5) git push -u 원격저장소주소 올릴로컬브랜치명  
    =>이 명령어을 통해 로컬저장소 내용을 원격저장소에 넣는다. <br>
     (ex. git push -u https://github.com/jungjang/github-prac.git main)<br>
     (원격저장소 주소는 깃헙repository의 code메뉴에 나와있다.)

 
push 할 때마다 깃헙주소 치기 귀찮으니까 git에서 변수문법 써서 주소 단축키 만드는 법<br>
git remote add 변수명 주소 <br>
(ex. git remote add origin https://github.com/jungjang/githup-prac.git) <br>

=> 이렇게 하면 '변수명'이라는 단어에 '주소값'이 할당된다.<br>
=> 그 다음 git push -u origin main 하면 내가 할당한 깃헙 주소에 알아서 저장됨

그런데 처음 git push 할 때 -u 추가하면 깃헙주소, 브랜치 위치 기억하라는 뜻임<br>
그래서 한 번 push 한 다음부터는<br>
git push 만 써도 알아서 원격repo에 백업됨


### 3. 타인과 협업하기 (요약: git push 하기전에 git pull 부터 하자)

*내가 팀장이다 : 소스코드 만들어서 메인브랜치에 업로드 해놓고 팀원들 콜라보레이터 등록해주고 클론해가게 하자.

*내가 팀원이다 :
    소스코드 다운받고 작업 시작해야함(원격저장소를 복제해오고 작업 시작)<br>
git clone 원격저장소주소 원하는폴더이름<br>
(ex. git clone https://github.com/jungjang/github-prac.git week5-todolist) 

=> 이를 통해 소스코드 복제해오고, <br>
명령어 yarn or yarn install 하면 소스코드에 설치된 라이브러리들 한번에 설치됨

그 후 여기서부터 git push 원격레포의원하는브랜치로 원격레포에서 내가 작업할 브랜치 만들고<br>
git branch 원격레포의원하는브랜치 로 나도 로컬레포=원격레포의원하는브랜치와 똑같은 이름의 로컬브랜치 만들고<br>
거기서 작업하고 커밋하고<br>
git push  or git push 주소 원격레포의원하는브랜치 하면 원격에 커밋 적용되어 pull request 하고, <br>그게 협업임<br>
git remote -v : 원격 연결되어있는지 확인하기 명령어<br>
- 그런데 팀원이 git push 하려면(협업하려면) 제한이 있음<br>
 ( github 아이디가 있어야함, 그 팀원의 아이디를 공동작업자 메뉴에 등록해놔야 함 )
그런데 내가 팀원으로써 작업 후 git push를 하고싶어도<br>
원격저장소에 새로운게 생기면 git push 못함<br>
->작업 시작하려면 git pull 먼저 해야함

로컬의 메인 브랜치에서 git pull 하자<br>
 (원격 저장소의 내용을 로컬 저장소로 가져와서 합쳐주라는 뜻)<br>
git pull  / git pull 원격저장소주소 브랜치명<br>
(ex. git pull https://github.com/jungjang/github-prac.git main)<br>
-> 이 명령어를 통해 원격저장소 최신 내용이 로컬저장소에 있을 때만 git push 가능하다.

그리고 로컬에서 내가 작업할 브랜치가 있다면 옮겨서 작업해주고<br>
 없다면 따로 만들어주고 그 브랜치로 옮겨서 작업<br>
( git branch changwon    =>  git switch changwon )<br>
하고 push 하자


* git remote add 변수명 주소<br>
를 통해서 git pull 변수명 브랜치명 (입력해서 특정 브랜치명만 가져올 수 있다.)<br>
* git pull은 사실 git fetch + git merge 임<br>
 (git fetch : 원격저장소 신규 commit 가져오기)<br>
 (git merge : 내 브랜치에 merge 하기 -> 따라서 conflict 가능성 있음 -> 에디터에 뜬거 수정하면됨)


4. 브랜치로 협업하기
프로젝트 진행에 투입된 개발자들이 많아지면 지옥도가 펼쳐진다.<br>
이를 해결하기 위해 각자 브랜치 만들어서 개발하고 merge 하는게 안정적<br>
1) 원격저장소 브랜치 만들기
만드는법1. 깃헙사이트에서 직접 만들기<br>
만드는법2. 로컬저장소에서 원격repository에 브랜치 만들기<br>
git branch 브랜치명 (ex. git branch mining) <br>
=> 이를 통해 만든 브랜치를<br>
git push 원격저장소주소 브랜치명<br>
(ex. git push https://github.com/jungjang/github-prac.git mining)<br>
=> 하여 새로운 원격repo에 새로운 브랜치 생성

* 브랜치 이름 중복되면? - 알아서 피하자 ( 브랜치명을 이름으로 하거나 해서 )

2) 원격저장소 브랜치 merge 하기
합치는법1. 깃헙사이트에서 직접 합치기 👍<br>
합치는법2. 로컬에서 머지한 후 브랜치에 push<br>
=> 그런데 협업에서는 시니어, 동료들의 코드리뷰와 테스트 후 머지하는 경우가 많다.<br>
=> 깃헙사이트에서 머지하는 경우가 많다.

깃헙에서
Pull request -> New pull request -> Create pull request -> Merge pull request
