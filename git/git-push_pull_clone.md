# git push_pull_clone

[`git push`](#git-push)   
[pull / clone](#git-push_pull_clone)

---
## `git push`
- `git push origin master`
  - 로컬 저장소에서 원격 저장소로 이동
  - 변경 사항만큼의 commit만 업로드
  - 항상 모든 작업은 로컬에서 이루어져야한다.
    - 단방향으로만 하는 것이 좋다.
- 원격 저장소에는 commit이 올라가는 것
  - commit 이력이 없다면 push할 수 없다.

## pull / clone
- pull은 commit만큼만 받는 것
- clone은 전체를 다 받는 것(다운로드와 유사)
- `git clone 'URL'`
  - 원격 저장소 전체를 복제(다운로드)
  - clone으로 받은 프로젝트는 이미 `git init`이 되어있음