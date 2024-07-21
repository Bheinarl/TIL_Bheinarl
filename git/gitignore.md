# gitignore

## gitignore
- git에서 특정 파일이나 디렉토리를 추적하지 않도록 설정하는 데 사용되는 텍스트 파일

- '.gitignore' 파일 생성(확장자 없음) 후 '.gitignore' 안에 숨길 파일 작성

- gitignore.io 사이트에서 숨길 파일 작성을 도움

- 주로 windows와 visualstudiocode는 숨긴다.

- 주의 사항
  - 이미 git의 관리를 받은 이력이 있는 파일이나 디렉토리는 나중에 gitignore에 작성해도 적용되지 않음
  
  - `git rm --cached` 명령어를 통해 git 캐시에서 삭제 필요