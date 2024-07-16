# List

[list](#list-1)   
[list 표현](#list-표현)   
[list의 시퀀스 특징](#list의-시퀀스-특징)   
[중첩된 list 접근](#중첩된-list-접근)   


---

## List
- 여러 개의 값을 순서대로 저장하는 **변경 가능**한 시퀀스 자료형

## List 표현
- 0개 이상의 객체를 포함하며 데이터 목록을 저장

- 대괄호 ( [ ] )로 표기

- 데이터는 어떤 자료형도 저장할 수 있음

```python
my_list_1 = []

my_list_2 = [1, 'a', 3, 'b', 5]

my_list_3 = [1, 2, 3, 'Python', ['hello', 'world', '!!!']]
```

- String과는 다르게 요소의 값을 변경 가능

## List의 시퀀스 특징

```python
my_list = [1, 'a', 3, 'b', 5]

# 인덱싱
print(my_list[1])  # a

# 슬라이싱
print(my_list[2:4])  # [3, 'b']
print(my_list[:3])  # [1, 'a', 3]
print(my_list[3:])  # ['b', 5]
print(my_list[0:5:2])  # [1, 3, 5]
print(my_list[::-1])  # [5, 'b', 3, 'a', 1]

# 길이
print(len(my_list))  # 5
```

### List는 변경 가능
```python
my_list = [1, 2, 3]
my_list[0] = 100

print(my_list)  # [100, 2, 3]
```

## 중첩된 List 접근

```python
my_list = [1, 2, 3, 'Python', ['hello', 'world', '!!!']]

print(len(my_list))  # 5

print(my_list[4][-1])  # !!!

print(my_list[-1][1][0])  # w
```
