# Git commands
> How to use git commands
>
---
### 커밋 기록 확인
**Log**
- commit 내역을 확인하는 기초
```bash
단순 사용
git log
# --oneline : 1 줄 단위로 출력
# -n : 갯수 지정
git log --oneline -n 3
```
---
### Commit 되돌리기
**Revert**
- commit을 취소한 이력을 남긴다.
- commit hash를 통해 중간 commit을 롤백할 수 있다.
``` bash
# 특정 Commit Revert
# --no-edit  세부 옵션 Skip
git revert --no-edit <commitHash>
# 바로 commit하지 않고 사유 추가
git revert --no-commit <commitHash>
git commit -m "Why do you revert?"
git push ...
# 여러개 revert
git commit <commitHash>..<commitHash>
```
<br>\
**Reset**
- commit을 취소한 이력을 남기지 않는다.
  - local에 commit이 머물렀을 경우 reset 사용
- 최대한 사용을 지양한다.
    - reset 한 commit이 프로젝트를 진행하는 팀원의 branch에 여전히 존재한다.
- HEAD^ : 하나 당 하나의 commit 기록을 뜻한다
- HEAD~\<number\> : number개 만큼의 commit

``` bash
# 최근 commit 하나 삭제
git reset HEAD^
# 여러 개의 commit 삭제
git reset HEAD~<amount>
# 취소한 변경 이력 모두 삭제
git reset --hard <commitHash>
# 변경 이력은 삭제하지만 내용은 유지
git reset --mixed <commitHash>
# stage, 변경 내용을 유지하며 변경 이력만 삭제한다.
git reset --soft <commitHash>
```

##### References
[Reset & Revert 01](https://kyounghwan01.github.io/etc/git/git-reset-revert/#reset)

[Reset & Revert 02](https://tekken5953.tistory.com/4)
