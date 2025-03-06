---
태그:
  - 도구
숙련도: 70
---
> [!important] 터미널 명령어로 깃 관리를 생활화하자…

  

> [!important]
> 
> ### 전체 명령어
> 
> > Github 레포 클론하기
> 
> `git clone <github url>`
> 
>   
> 
> > Github 레포 연결하기
> 
> `git remote add origin <github url>`
> 
>   
> 
> > 현재 작업 파일의 변경사항 확인
> 
> `git status`
> 
>   
> 
> > 변경사항을 stage로 옮기기
> 
> `get add`
> 
> `. / -a` → 모든 변경 파일 추가
> 
>   
> 
> > 스테이지 추가된 파일 커밋하기
> 
> `git commit`
> 
> `-m ”…”` → 메시지와 함께 커밋 남기기
> 
> `-am “…”` → 모든 변경파일 stage로 옮기고 한번에 커밋 날리기
> 
>   
> 
> > 로컬의 커밋 내용 리모트로 날리기
> 
> `git push` `origin` `<브랜치 이름>`
> 
>   
> 
> > 리모트의 모든 브랜치에 대한 최신 이력 확인하기
> 
> `git remote update`
> 
>   
> 
> > 리모트의 변경사항 로컬로 가져오기 (merge)
> 
> `git pull origin <브랜치 이름>` → 사실상 fetch와 merge가 합쳐져 있는 명령어
> 
>   
> 
> > 브랜치 종류 확인
> 
> `git branch`
> 
> → 로컬의 브랜치 종류 확인
> 
> `-r` → 리모트의 브랜치 종류 확인
> 
> `-a` → 로컬과 리모트의 모든 브랜치 종류 확인
> 
> `-vv` → 리모트와 비교한 커밋 개수와 최근 커밋 이름 확인
> 
>   
> 
> > 브랜치 삭제
> 
> `git branch -D <브랜치 이름>` → 브랜치 강제 삭제
> 
>   
> 
> > 변경사항 보류
> 
> `git stash`
> 
> `git stash pop` → 보류 해제
> 
>   
> 
> > 브랜치 변경하기
> 
> `git switch <브랜치 이름>` → `checkout`과 달리 브랜치 변경만 가능한 명령어
> 
> `git checkout <로컬 브랜치 이름>` → 브랜치 변경
> 
> `git checkout <``리모트 브랜치 이름``>` → 내용이 저장되지 않는 스냅샷모드로 리모트 브랜치 사용
> 
> `-b <만들 브랜치 이름>` → 현재 브랜치에서 파생되는 브랜치 만들고 변경
> 
> `-b <만들 브랜치 이름> <파생 브랜치 이름>` → 특정 브랜치에서 파생되는 브랜치 만들고 변경
> 
> `-b <만들 브랜치 이름> origin/<리모트 브랜치 이름>` → 리모트 브랜치를 로컬에도 만들고 변경
> 
> `-t origin/<리모트 브랜치 이름>` → 로컬에 같은 이름의 브랜치를 만들고 추적 시작
> 
>   
> 
> > 브랜치 추적하기
> 
> `git branch --set-upstream-to=origin/<리모트 브랜치 이름> <로컬 브랜치 이름>`
> 
>   
> 
> > 현재 작업 브랜치의 커밋 모두 확인
> 
> `git log`
> 
>   
> 
> > 변경사항 비교하기
> 
> `git diff` → 현재 작업물과 스테이징 area 사이의 비교
> 
> `git diff HEAD` → 마지막 커밋과의 차이를 비교
> 
> `git diff <1번 브랜치> <2번 브랜치>` → 두 브랜치의 차이를 비교
> 
>   
> 
> > 커밋 되돌리기(취소하기)
> 
> > [!important] `**reset**` **의 경우에는 되돌리려는 커밋까지의 모든 커밋이 취소됨**
> 
> `git reset HEAD^` → 바로 직전 커밋으로 돌아가기
> 
> `git reset <``커밋 해쉬값``>` → 해당 커밋까지 쭈욱 돌아가기
> 
> `--soft` → 커밋 취소하고, 변경사항은 스테이징 되어있음
> 
> `--mixed`(기본값) → 커밋 취소하고, 변경사항 스테이징 안되어있음
> 
> `--hard` → 커밋 취소하고, 변경사항은 삭제되어 있음
> 
> > [!important] `**revert**` **의 경우에는 특정 커밋만을 취소하는 새로운 커밋을 날림**
> 
> `git revert HEAD` → 바로 직전 커밋을 제거하는 revert 커밋이 커밋됨
> 
> `git revert <커밋 해쉬값>` → 해당 커밋을 제거하는 revert 커밋이 커밋됨
> 
> `—-no-commit <커밋 해쉬값>` → 바로 커밋하지 않고 스테이징에 올려두는 명령어
> 
>   
> 
> > 관계 없는 두 브랜치 병합
> 
> `git merge <끌어오려는 브랜치 이름> --allow-unrelated-histories`

### 상황별 사용례

> [!important]
> 
> - 1. 깃허브 사이트에서 리모트 브랜치를 만들었고 로컬에 연결하고자 할때
>     
>     > 내 작업 내역 커밋해두기
>     
>     `git status`
>     
>     `git commit -am “커밋 메시지”`
>     
>       
>     
>     > 리모트 브랜치 정보 업데이트
>     
>     `git remote update`
>     
>     `git branch -a`
>     
>       
>     
>     > 로컬 브랜치 생성하기
>     
>     `git checkout -b <생성할 브랜치 이름> origin/<리모트 브랜치 이름>`
>     
>     → 로컬로 브랜치가 만들어지고 해당 브랜치로 변경됨
>     
>     `git checkout -t origin/<리모트 브랜치 이름>`
>     
>     → 리모트와 같은 이름으로 로컬에 생성 + 추적까지
>     
>       
>     
>     > 기존에 사용하던 브랜치 삭제
>     
>     `git branch -d <기존 브랜치 이름>`
>     
>     `git branch -D <기존 브랜치 이름>` → 강제 삭제
>     
>     `git push origin -d <로컬 브랜치 이름>` → 리모트에서 삭제
>     

> [!important]
> 
> - 2. 동료의 test 머지 이후 변경사항을 내 작업 브랜치에 가져오기
>     
>     > [!important] 나의 test 머지 때 충돌을 방지하기 위해서는 test 의 변경내용은 변동이 있을때마다 받아 와야함
>     > 
>     > 또한 로컬에서 머지 함으로서 충돌의 영향을 최소화 시킬 수 있음
>     
>       
>     
>     > 내 작업 내역 커밋해두기
>     
>     `git status`
>     
>     `git commit -am “커밋 메시지”`
>     
>       
>     
>     > 리모트 브랜치 정보 업데이트
>     
>     `git remote update`
>     
>     `git branch -a`
>     
>       
>     
>     > 로컬 test 브랜치로 이동해서 변경사항 받기
>     
>     `git checkout test`
>     
>     `git pull origin test`
>     
>       
>     
>     > 내 작업 브랜치로 이동해서 test 브랜치 머지하기
>     
>     `git checkout feat/#21`
>     
>     `git merge test`
>     

> [!important]
> 
> - 3. 작업하던 내용을 PR 하고자 할 때
>     
>     > [!important] **⚠️ 반드시 2번 작업을 통해 test 브랜치의 최신 변경사항을 반영하고 PR 올릴 것**
>     
>       
>     
>     > 내 작업 내역 커밋하기
>     
>     `git status`
>     
>     `git commit -am “커밋 메시지”`
>     
>       
>     
>     > 로컬의 커밋 내용 리모트로 push 하기
>     
>     `git push origin <브랜치 이름>`
>     
>       
>     
>     > 깃허브 사이트로 이동해서 PR 날리기
>     

  

### 참고

[https://velog.io/@hosunghan0821/Git-%EC%8B%A4%EB%AC%B4%EC%97%90%EC%84%9C-%EB%B0%B0%EC%9A%B4-Git-Rebase](https://velog.io/@hosunghan0821/Git-%EC%8B%A4%EB%AC%B4%EC%97%90%EC%84%9C-%EB%B0%B0%EC%9A%B4-Git-Rebase)

