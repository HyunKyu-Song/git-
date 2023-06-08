> ## git은 버전관리하려고 쓰는 것<br>
<br><br>
> ## 시작할 때
`git init`: repository 생성해줌<br><br><br><br>

> ## 파일 현재상태를 기록해두려면
1. git add로 기록할 파일 고르고
`git add 파일명.확장자`<br><br>
2. 고른파일 기록명령은 git commit
`git commit -m '메모'`<br><br><br><br>

> ## 스테이징
1. 여러 파일 스테이징하려면
`git add 파일1, 파일2`<br><br>
2. 모든 파일 스테이징
`git add .`<br><br><br><br>

> ## 상태창 열기
`git status`<br><br><br><br>

> ## commit 내역 조회
`git log --all --oneline`<br><br><br><br>

> ## 최근 commit VS 현재파일 차이점 보여줌
1. `git diff`<br><br>
2. `git difftool` (:q, :qa 누르면 나가짐)<br><br><br><br>

> ## branch 만들기
`git branch 작명`<br><br><br><br>

> ## branch 이동하기
`git switch branch명`<br><br><br><br>

> ## branch 합치기 1 (merge)
- 기준이 되는 branch로 이동 후 git merge 합칠 branch명
- 같은 줄을 수정했다면 conflict(충돌)이 발생<br><br>
#### 해결법
1. 원하는 코드만 남기고 지움
2. 다시 `git add`
3. 다시 `git commit`<br><br>
#### 📍참고) 
branch 합쳐서 합쳐진 branch들 삭제 안됨
- 삭제하려면
`git branch -d branch명`<br><br>
- merge 안함 branch 삭제는
`git branch -D branch명`<br><br><br><br>

> ## branch 합치기 2 (rebase and merge)
`rebase 쓰는 이유`
: 간단하고 짧은 branch들은 이거 쓰면 깔끔해보임<br>
`단점`
: 브랜치끼리 차이가 너무 많은 경우 rebase하면 충돌이 많이 발생 그거 하나하나 해결하기 귀찮<br>
1. 새로운 branch로 이동해서
2. git rebase 기준이 되는 branch명
3. 기준이 되는 branch로 이동
4. git merge 새로운 branch명<br><br><br><br>

> ## branch 합치기 3 (squash and merge)
git log 깔끔하게 사용하기 위함<br>
`git merge --squash 새로운 branch명`<br><br><br><br>

> ## 파일 복구하는 법
`git restore 파일명`<br>
특정 commit 시점으로 파일 복구하는 법
`git restore --source 커밋아이디 파일명`<br>
staing 취소
`git restore --staged 파일명`<br><br><br><br>

> ## commit 취소하는 법
log 기록은 남지만 내용은 삭제되고 새롭게 commit됨
`git revert 커밋아이디`<br>
#### 📍참고) 
여러 개 취소 가능
`git revert 커밋아이디1 커밋아이디2`<br>
최근 commit 취소가능
`git revert HEAD`<br>
merge commit도 취소가능
이건 필요하면 찾아보자<br><br><br><br>

> ## 과거로 모든걸 되돌리기
`git reset --hard 커밋아이디`
#### 🔥주의
`협업시에 사용금지`<br><br>
리셋인데 변동사항 지우지 말고 스테이징해놓기
`git reset --soft 커밋아이디`<br>
리셋인데 변동사항 지우지 말고 unstage해놓기
`git reset --mixed 커밋아이디`<br><br><br><br>

> ## github에 업로드 하는 법
`git push -u 원격저장소주소 올릴로컬branch명`<br>
github는 기본 branch 이름을 main으로 해야 함
그래서 `git branch -M main`<br>
git push 할때 -u 추가하면 주소 기억하라는 뜻
그럼 다음부터는 git push만 해도 됨<br><br>
근데 github에 이렇게 3줄 나와있음 복붙하셈
`git remote add origin https://github.com/HyunKyu-Song/gittest.git`
`git branch -M main`
`git push -u origin main`<br><br><br><br>

> ## github 협업하기
- 소스코드 다운받는 법
  - 팀원이 vsc에서
  - git clone 저장소주소<br>
- github에서 공동작업자도 등록
  - 내용정리 사진참고<br><br>
#### 📍참고)
- 원격저장소 최신내용이 로컬저장소에 있을 때만 git push 가능<br><br>
- git pull은 git fetch + git merge임 그래서 conflict 발생가능
`git fetch`: 원격저장소 신규 commit 가져오셈
`git merge`: 내 branch에 merge<br><br>
- 원격저장소 -> 로컬저장소
  - 원격저장소(github)에 소스를 로컬저장소에 다운하는 법
  - git pull 원격저장소주소 branch명	// git push 할때 -u 붙였으면 그냥 git pull만 해도 됨
