# git revert

[git revert](#git-revert-1)   
[git revert 작동 원리](#git-revert-작동-원리)   
[git revert 명령어 예시](#git-revert-명령어-예시)   
[git revert 특징](#git-revert-특징)   
[git revert 추가 명령어](#git-revert-추가-명령어)   

---

## `git revert`
- 특정 commit을 없었던 일로 만드는 작업
```python
git revert <commit id>
# commit id는 key 값과 같은 난수 값
```

## `git revert` 작동 원리
- '재설정'

- 단일 commit을 실행 취소하는 것

- 프로젝트 기록에서 commit을 없었던 일로 처리 후 그 결과를 새로운 commit으로 추가함

- 없었던 일로 하는 것이지 commit을 삭제하는 것은 아님

## `git revert` 명령어 예시
```python
git log --oneline #commit 목록 확인
git revert <commit id> #실행하면 VIM이 켜짐

i #입력모드 진입
Revet "commit message" # ""칸에 commit message 수정
esc # 명령모드 진입
[shift] + [;] # 명령모드에서 command 입력 가능
:wq # w : 쓰기 / q : 나가기
```

- commit의 개수는 유지

- '입력모드'와 '명령모드' 2가지가 존재
  - 입력모드는 `i`
  
  - 명령모드는 `esc`

- 명령모드에서 `shift` + `;` 후, `:wq`
  - 쓰고 종료하기

## `git revert` 특징
- 변경 사항을 안전하게 실행 취소할 수 있도록 도와주는 순방향 실행 취소 작업

- commit 기록에서 commit을 삭제하거나 분리하는 대신, 지정된 변경 사항을 반전시키는 새 commit을 생성

- git에서 기록이 손실되는 것을 방지하며 기록의 무결성과 협업의 신뢰성을 보임

## `git revert` 추가 명령어
- 공백을 사용해 여러 commit을 한꺼번에 실행 취소 가능
```python
git revert <commit id 1> <commit id 2> <commit id 3>
```
- ..을 사용하여 범위를 지정하여 여러 commit을 한꺼번에 실행 취소 가능
```python
git revert <commit id 1>..<commit id 5>
```
- commit 메세지 작성을 위한 편집기를 열지 않음 (자동으로 commit 진행)
```python
git revert --no-edit <commit id>
```
- 자동으로 commit 하지 않고, Staging Area에만 올림 (이후에 직접 commit해야 함)
  - 이 옵션은 여러 commit을 revert할 때, 하나의 commit으로 묶는 것이 가능
```python
git revert --no-commit <commit id>
```
