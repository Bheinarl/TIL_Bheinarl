# git 초기 설정

[git init](#git-init)   
[git add](#git-add)   
[git commit](#git-commit)   
[git remote](#git-remote)   
[순서](#순서)   

---
## `git init`
- 로컬 저장소 설정 (초기화)

- git의 버전 관리를 시작할 디렉토리에서 진행

- 아래와 같이 'master'가 표시된다면 Git의 영역에 들어간 것이다.

<div align='center'>
<img src="https://file.notion.so/f/f/fea5dfb6-d382-44f8-881d-de09359f06f1/9d304354-c920-488c-896f-438336615c54/Untitled.png?id=4ac12673-c813-4c68-8026-9f770c01af44&table=block&spaceId=fea5dfb6-d382-44f8-881d-de09359f06f1&expirationTimestamp=1721116800000&signature=LoJVnqKPRg-_iYE7brqjlZHc64mHC-ivJPE9KdnaKzw&downloadName=Untitled.png">
</div>

- `git init`한 디렉토리의 하위 디렉토리는 모두 git의 영역에 포함된다.

- `git init`한 디렉토리의 하위 디렉토리에서 `git init`을 한다면, 상위 디렉토리에서는 하위 디렉토리가 무의 영역에 들어간 것으로 취급

- 실수하였을 경우, 아래와 같은 숨겨진 폴더를 삭제하면 복구가 된다.

<div align='center'>
<img src="https://file.notion.so/f/f/fea5dfb6-d382-44f8-881d-de09359f06f1/9d776105-1061-4065-b4bf-b9295acabbac/Untitled.png?id=2252a49b-e6bd-47a3-8564-59bfdeb6129e&table=block&spaceId=fea5dfb6-d382-44f8-881d-de09359f06f1&expirationTimestamp=1721116800000&signature=gyZuJXyDQHOn98NWuqnv14WcwT-kOW0RxB_tZJsdbyU&downloadName=Untitled.png">
</div>

## `git add`
- 변경 사항이 있는 파일을 Staging Area에 추가

- '파일을 추가'하는 것이 아닌, '파일이 추가되었다는 사실'을 기록

- `git add .`
  - 현재 위치에 있는 모든 변경 사항을 Staging Area에 등록

## `git commit`
- Staging Area에 있는 파일들을 저장소에 기록

- 해당 시점의 버전을 생성하고 변경 이력을 남기는 것

- 뒤에 옵션이 붙는다
  - 예시
  
  - `git commit -m "메세지(버전 이름)"`
    - 메세지는 파일이름이나 버전이 아닌 사람에게 남기는 기록
    
    - 메세지는 중복되어도 상관 없다.

## `git remote`
- 현재 프로젝트에 등록된 리모트 저장소를 확인

- `git remote add '닉네임' "URL"`
  - 해당 URL의 Repository에 해당 닉네임을 부여
  
  - 닉네임은 단순히 내가 사용할 이름
  
  - origin이 가장 초기 닉네임으로, 보편적으로 사용한다.

- `git remote -v`
  - 현재 등록된 원격 저장소 이름과 URL을 확인

## 순서
```python
git init
git remote add 닉네임 URL
#여기까지가 처음 해야할 작업

git add
git commit -m "메세지"
git push 닉네임 master
#or
git pull URL
#or
git clone URL
```

>'Add a README file'을 체크하고 Repository를 만든다면 제일 먼저 `pull` 또는 `clone`을 하고 시작해야한다.