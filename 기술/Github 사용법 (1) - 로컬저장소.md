(작업폴더 열고 ex.githubprac열고)

### 1. 시작
작업폴더에서 git 쓰고 싶으면<br>
git init 입력<br>
-> 깃이 작업폴더를 감시 시작(코드작성, 파일생성 등 인지)

git branch -M main 을 통해 기본 브랜치 이름을 main으로 변경<br>
     (* github.com은 기본 브랜치 이름을 main으로 강요한다.)

* 이 아래 방법은 터미널에서 진행하는 가장 원시적 방법,<br>
  기억만 해두고 gitlens같은 확장파일을 쓰는게 편하다.<br>
 ( 단 git init은 항상 터미널에서 해주고 시작해야한다.)


### 2. 코드 맘에들어서 파일 현재 상태 기록해두려면<br>
1) git add 파일명
(ex. git add app.txt / git add App.js)<br>
// 기록할 파일 고르기('스테이징 한다' 라고 표현)<br>
// 이 단계를 거치면 기록할 파일이 'staging area'로 넘어간다.

2) git commit -m '적고싶은 메시지' <br>
(ex. git commit -m 'aaaa추가') <br>
// 고른파일 기록저장소에 옮긴다.
// 이 단계를 거치면 기록할 파일이 'repository(저장소)'로 넘어간다.

---

요즘방법

요즘 터미널에다가 직접 깃 명령어 입력 안한다.<br>
에디터들에 내장되어있다.<br>
vscode는 왼쪽의 소스제어항목<br>

파일 수정 후 저장이 일어나면 자동으로 소스제어항목에<br>
Changes가 추가됨 -> 마우스 호버 하면 버튼들 나옴<br>
+ (stage changes) : [git add 해당파일명] 의 역할을 한다.<br>
- (staged changes) : 스테이징 된 파일을 스테이징 취소하는 역할을 한다.

* 스테이징 한 후에 위에 메시지 적고 체크표시로 커밋 누르면 커밋 완료

---

### 3. 브랜치 만드는 법
원본에다가 코드 짜다가 망하면 안되니까 브랜치(커밋의 복사본) 만들어서 거기서 먼저 코드 작성<br>
git branch 작명 : 브랜치 생성 , '작명'이라는 이름으로 프로젝트 복사본을 만든 것<br>
git switch 작명 : 브랜치 위치 바꾸기, '작명'이라는 이름의 브랜치로 이동<br>
git status : 현재 브랜치 위치 확인하기<br>

만들어서 이동한 브랜치에서 작업, 커밋 시작

git log --all --oneline --graph 하면 선으로 보여줌


### 4. 브랜치 합치는 법
브랜치를 합친다 : '머지'한다.<br>
1) 일단 기준이 되는 브랜치로 이동한다. (ex. git switch master)
2) git merge 합칠 브랜치 명 (ex. git merge coupon)

충돌이 날 경우 원하는 코드만 남기고<br>
git add, git commit <br>
혹은 <br>
vscode 는 위에 메뉴가 나온다.

* 브랜치 기능은 협업시에도 유용하다.<br>
10명이서 각각 브랜치를 만들어서 미리 개발을 한 뒤 잘되면 합치는 식으로 진행한다.


### 5. 브랜치 삭제하는 법
git branch -d 브랜치명 : 다 사용한 브랜치 삭제 가능<br>
따라서, 머지하고나면 브랜치를 삭제한다.<br>
머지 안한 브랜치를 삭제하려면 git branch -D 브랜치명

추가) 다양한 머지 방법들<br>
3-way merge : git merge 머지하고싶은브랜치 : 흔히 우리가 아는 머지 방법<br>
fast-forward merge : 메인브랜치에 커밋내용이 없고, 신규브랜치에만 커밋이 있다면 걍 바로 합쳐버림<br>
rebase and merge : 머지 그래프 간단히 만들어주지만 충돌 많이 일어난다.<br>
squash and merge : git merge --squash 머지하고싶은브랜치 <br>
 -> 3way-merge 많이하면 머지그래프 더러워짐 
 -> 따라서 짜잘한 커밋내용이 master브랜치의 커밋로그에 안나오게하기위해 진행(비주얼적 이유)


### 6. git 버전관리하는 법
잘 안쓰는 명령어들이니까 이런게있네 하고 넘어가고 나중에 필요하면찾아보자.<br>
git restore : 파일 되돌리려면 쓰는 명령어<br>
git revert : 커밋 되돌리려면 쓰는 명령어<br>
-> vscode에서 기본적으로 제공해준다.

---

추가) 유용한 명령어

1) 여러 파일 스테이징 하려면<br>
git add 파일1 파일2 (ex. git add app.txt prac.txt)<br>
한 후에 git commit -m '메시지' 로 커밋 내용 정리

2) 모든 파일 스테이징 하려면<br>
git add .   -> 모든 파일 스테이징 해줘라<br>
한 후에 git commit -m '메시지' 로 커밋 내용 정리

3) 상태창열기
git status   -> 지금 내가 어떤 파일들을 스테이징해놨는지 볼 수 있음

4) 커밋한 내역 조회<br>
git log --all --oneline

5) 현재 파일과 최근 커밋 차이점 확인하려면 터미널에<br>
git diff : 최근 커밋과 현재 파일의 차이점 보여줌
-> 구리다 
-> 확장프로그램 설치해서 쓰는게 편하다. (ex. gitlens)
