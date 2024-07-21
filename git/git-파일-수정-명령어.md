# git 파일 수정 명령어

[이미 삭제한 commit 복구](#이미-삭제한-commit-복구)   
[파일 내용을 수정 전으로 되돌리기](#파일-내용을-수정-전으로-되돌리기)   
[Staging Area에 올라간 파일을 Unstage하기](#staging-area에-올라간-파일을-unstage-하기)   
[바로 직전에 생성한 commit 수정](#바로-직전에-생성한-commit-수정)   

---
## 이미 삭제한 commit 복구
- `git reflog`
  - HEAD가 이전에 가리켰던 모든 commit을 보여줌
  
  - `git reset`의 `--hard` 옵션을 통해 지워진 commit도 `reflog`로 조회하여 복구 가능   

```python
git reflog
git reset --hard <commit id> 
#복구하고자하는 commit의 id
```

## 파일 내용을 수정 전으로 되돌리기
- `git restore`
  - Modified 상태의 파일 되돌리기
  
  - Working Directory에서 파일을 수정한 뒤, 파일의 수정 사항을 취소하고, 원래 모습대로 되돌리는 작업
  
  ```python
  #파일을 수정하고 `git add`하기 전 단계
  git restore <file명>
  ```

- `git restore --staged`
  - `git add`한 후 되돌리기
    ```python
     #이미 commit들을 앞에서 등록한 상태
    #`git add`를 한 후, `git   commit`하기 전 단계
    git restore -staged <file명>
    #`git add`하기 전으로 되돌리기
    ```

- 원래 파일로 덮어쓰는 원리이기 때문에 수정한 내용은 전부 사라짐

- 수정 취소 후 해당 내용을 복원할 수 없음

## Staging Area에 올라간 파일을 Unstage 하기
- `git rm --cached`
  - Staging Area에서 Working Directory로 되돌리기
  
  - git 저장소에 commit이 없는 경우에 사용
  ```python
  #아직 `git commit`을 한 번도 하지 않은 상태
  #`git add`를 한 후, `git commit` 하기 전 단계
  git rm --cached <file명>
  #git add하기 전으로 되돌리기
  ```

## 바로 직전에 생성한 commit 수정
### commit 메세지 수정
```python
git add .
git commit -m "A"
git commit --amend #VIM으로 진입
`i` #입력모드
commit 메세지 변경
`esc`#명령모드
`shift`+`;` #명령 입력
wq #write & quit
```
### commit 내용 수정
```python
git add a.txt
git commit -m "A"
git add b.txt
git commit --amend #VIM으로 진입 (메세지도 수정가능)
`shift` + `;` #명령 입력
wq #write & quit
```
- 언제 사용하느냐에 따라 메세지 수정 or 전체 수정

- 협업 시에는 사용 불가

- 불필요한 commit을 생성하지 않고, 직전 commit을 수정할 수 있기 때문에 git에서 꼭 필요한 기능 중에 하나