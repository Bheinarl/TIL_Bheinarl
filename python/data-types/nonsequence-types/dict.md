# dict

[dict](#dict딕셔너리)   
[dict 표현](#dict-표현)   
[dict 사용](#dict-사용)   

---

## dict(딕셔너리)
- key - value 쌍으로 이루어진 순서와 중복이 없는 **변경 가능**한 자료형

- key는 변경이 불가능하고, value만 변경 가능하다.

- 일반적으로 API 소통에 사용

- 순서가 없어서 몇 번째 요소라는 것이 존재하지 않는다.

- 순서가 없기 때문에 index가 존재하지 않는다.


## dict 표현
- key는 변경 불가능한 자료형만 사용 가능 (str, int, float, tuple, range)

- value는 모든 자료형 사용 가능

- 중괄호 {}로 표시

- { key : value } 형태

- dict는 키에 접근하여 값을 얻어내는 방식

```python
my_dict_1 = {}
my_dict_2 = {'key': 'value'}
my_dict_3 = {'apple': 12, 'list': [1, 2, 3]}

print(my_dict_1)  # {}
print(my_dict_2)  # {'key': 'value'}
print(my_dict_3)  # {'apple': 12, 'list': [1, 2, 3]}
```

## dict 사용
- key를 통해 value에 접근

```python
my_dict = {'apple': 12, 'list': [1, 2, 3]}
print(my_dict['apple'])  # 12
print(my_dict['list'])  # [1, 2, 3]

# 추가
my_dict['banana'] = 50
print(my_dict) # {'apple': 12, 'list': [1, 2, 3], 'banana': 50}

# 변경
my_dict['apple'] = 100
print(my_dict) # {'apple': 100, 'list': [1, 2, 3], 'banana': 50}
```