# set

[set](#set-집합-자료형)   
[set 표현](#set-표현)   
[set의 집합 연산](#set의-집합-연산)   


---

## set (집합 자료형)
- 순서와 중복이 없는 변경 가능한 자료형

## set 표현
- 수학에서 집합과 동일한 연산 처리 가능

- 중괄호 {}로 표기

- 순서가 존재하지 않아 몇 번째 요소라는 것이 존재하지 않는다.

```python
my_set_1 = set()
my_set_2 = {1, 2, 3}
my_set_3 = {1, 1, 1}

print(my_set_1)  # set()
print(my_set_2)  # {1, 2, 3}
print(my_set_3)  # {1}
```

## set의 집합 연산

```python
my_set_1 = {1, 2, 3}
my_set_2 = {3, 6, 9}

#합집합
print(my_set_1 | my_set_2) # {1, 2, 3, 6, 9}

#차집합
print(my_set_1 - my_set_2) # {1, 2}

# 교집합
print(my_set_1 & my_set_2) # {3}
```

- 장점 : set으로 변경하면 중복을 제거할 수 있다.
- 단점 : set으로 변경하면 set은 순서가 없어 배치가 섞이기 때문에 순서는 다시 재배치 해야 된다.