# Greedy Algorithm

[greedy algorithm](#greedy-algorithm-탐욕-알고리즘)   
[탐욕 알고리즘의 동작 과정](#탐욕-알고리즘의-동작-과정)   
[탐욕 알고리즘 baby-gin 구현](#탐욕-알고리즘-baby-gin-구현)   

---
## Greedy Algorithm 탐욕 알고리즘
- 탐욕 알고리즘은 최적해를 구하는 데 사용되는 근시안적인 방법

- 여러 경우 중 하나를 결정해야 할 때마다 그 순간에 최적이라고 생각되는 것을 선택하여 나가는 방식으로 진행하여 최종적인 해답에 도달

- 각 선택의 시점에서 이루어지는 결정은 지역적으로는 최적이지만, 그 선택들을 계속 수집하여 최종적인 해답을 만들었다고 하여, 그것이 최적이라는 보장은 없다.

- 일반적으로, 머릿속에 떠오르는 생각을 검증없이 바로 구현하면 Greedy 접근이 된다.

## 탐욕 알고리즘의 동작 과정
- 해 선택
  - 현재 상태에서 부분 문제의 최적 해를 구한 뒤, 이를 부분해 집합(Solution Set)에 추가

- 실행 가능성 검사
  - 새로운 부분해 집합이 실행 가능한지를 확인
  
  - 문제의 제약 조건을 위반하지 않는지 검사

- 해 검사
  - 새로운 부분해 집합이 문제의 해가 되는지 확인

  - 아직 전체 문제의 해가 완성되지 않았다면 1단계 해 선택부터 다시 시작

## 탐욕 알고리즘 baby-gin 구현

```python
num = 456789 # Babygin 확인할 6자리 수
c = [0] * 12 # 6자리 수로부터 각 자리 수를 추출하여 개수를 누적할 리스트

for _ in range(6) # 
	c[num % 10] += 1 # 숫자를 쓰고 다 쓴 숫자는 바로 날려버림
	num //= 10 # 숫자 할당
	
i = 0
tri = run = 0
while i < 10:
	if c[i] >= 3 # triplet 조사 후 데이터 삭제
		c[i] -= 3
		tri += 1
		continue
	if c[i] >= 1 and c[i+1] >= 1 and c[i+2] >= 1: # run 조사 후 데이터 삭제
		c[i] -= 1
		c[i+1] -= 1
		c[i+2] -= 1
		run += 1
		continue
	i += 1

if run + tri == 2:
	print("Baby gin")
else:
	print("Lose")
```