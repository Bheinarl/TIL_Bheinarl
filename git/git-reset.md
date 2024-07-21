# git reset

[git reset](#git-reset-1)   
[git reset 명령어](#git-reset-명령어)   
[git reset 작동 원리](#git-reset-작동-원리)   
[git reset의 옵션](#git-reset의-옵션)   

---
## `git reset`
- 특정 commit으로 되돌아가는 작업

## `git reset` 명령어
```python
git reset [옵션] <commit id>
```

## `git reset` 작동 원리
- '되돌리기'

- 시계를 마치 과거로 돌리는 듯한 행위

- 특정 commit으로 되돌아갔을 때, 되돌아간 commit 이후의 commit은 모두 삭제
  - 1234에서 2로 되돌아갔다면 3, 4는 삭제

- 협업할 때는 잘 사용하지 않음

## `git reset`의 옵션
- 삭제되는 commit들의 기록(내용물)을 어떤 영역에 남겨둘 것인지 선택

1. `--soft`
   - 삭제된 commit의 기록을 Staging Area에 남김
   
   - 명령어
    ```python
     git reset --soft <commit id>
     ```

2. `--mixed` (기본 옵션 값)
   - 삭제된 commit의 기록을 working directory에 남김
     - `git status`로 확인 가능
   
   - 남아있는 행동들은 `git add`로 추가 가능
   
   - 명령어
    ```python
    git reset --mixed <commit id>
    ```

3. `--hard`
   - 삭제된 commit의 기록을 남기지 않음
   
   - 완전히 삭제됨
   
   - `git status`에서 검색 불가
   
   - 명령어
    ```python
    git reset --hard <commit id>