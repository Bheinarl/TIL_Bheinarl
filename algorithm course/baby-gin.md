# Baby Gin

[Baby-gin Game](#baby-gin-game)   
[완전 검색](#완전-검색-exaustive-search)   
[완전 검색을 활용한 Baby-gin](#완전-검색을-활용한-baby-gin)

---
## Baby-gin Game
- 설명
  - 0 ~ 9 사이의 숫자 카드에서 임의의 카드 6장을 뽑았을 때, 3장의 카드가 연속적인 번호를 갖는 경우를 run이라 하고, 3장의 카드가 동일한 번호를 갖는 경우를 triplet이라고 한다.
  
  - 6장의 카드가 run과 triplet로만 구성된 경우를 Baby-gin
  
  - 6자리의 숫자를 입력 받아 Baby-gin 여부를 판단

- 입력 예시
  - 667767은 두 개의 triplet이므로 baby-gin이다. (666, 777)
  
  - 054060은 한 개의 run과 한 개의 triplet이므로 역시 baby-gin이다. (456, 000)
  
  - 101123은 한 개의 triplet이 존재하나, 023이 런이 아니므로 baby-gin은 아니다. <br />
    (111, 023) X, (123, 011) X

## 완전 검색 Exaustive Search
- 완전 검색 방법은 문제의 해법으로 생각할 수 있는 모든 경우의 수를 나열해보고 확인하는 기법

- Brute-force 혹은 generate-and-test 기법이라고도 불리운다

- 모든 경우의 수를 테스트한 후, 최종 해법을 도출

- 모든 경우의 수를 테스트하기 때문에 수행 속도는 느리지만, 해답을 찾아내지 못할 확률이 작음

- 일반적으로 경우의 수가 상대적으로 작을 때 유용함

## 완전 검색을 활용한 Baby-gin
- 고려할 수 있는 모든 경우의 수 생성
  - 6개의 숫자로 만들 수 있는 모든 숫자 나열 (중복 포함)

- 해답 테스트하기
  - 앞의 3자리와 뒤의 3자리를 잘라, run과 triplet 여부를 테스트하고 최종적으로 baby-gin을 판단