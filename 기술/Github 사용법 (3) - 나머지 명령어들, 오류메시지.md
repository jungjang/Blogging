[0] 간단한 명령어들

git branch -M main (마스터일 경우 main으로 바꿔주기 because 깃헙이 최상위를 main으로 강제해서)<br>
git branch -r : 현재 브랜치 상태 확인해보기<br>
git remote update : 브랜치 구조 새로고침<br>
git switch 브랜치명 : 해당 브랜치로 경로 가기<br>
yarn add react-scripts : 클론한담에 터미널에 쓰면 클론파일에 설치된(팀장님이 설치한) 전체 패키지 한번에 설치해줌

나올 수 있는 오류들<br>
1. fatal: not a git repository 나오면 git init 해야한다는 뜻

2. LF will be replaced by CRLF.. 경고창

* CR (carriage Return)<br>
-현재 커서를 줄 올림 없이 가장 앞으로 옮기는 동작<br>
 LF (Line Feed / 유닉스OS의 줄바꿈방식)<br>
-커서는 그 자리에 둔 상황에서 종이만 한 줄 올려 줄 바꾸는 동작<br>
CRLF(CR+LF / 윈도우OS의 줄바꿈방식)<br>
-한마디로 줄바꿈<br>
즉, OS마다 줄바꿈에 대한 문자열이 다르기때문에 git에서 어느쪽을 선택할지 물어본 것)

해결코드
Window <br>
git config core.autocrlf true (해당 프로젝트에만 적용)<br>
git config --global core.autocrlf true ( 시스템 전체에 적용)<br>
즉 core.autocrlf를 키는 것이해결방법<br>
(ps. 변환기능을 원하지 않고 에러메시지 끄고싶으면 git config --global core.safecrlf false)
