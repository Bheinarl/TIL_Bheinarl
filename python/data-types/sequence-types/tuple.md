# Tuple

[Tuple](#tuple-1)   
[Tuple 표현](#tuple-표현)   
[Tuple의 시퀀스 특징](#tuple의-시퀀스-특징)   
[Tuple의 사용처](#tuple의-사용처)   

---

## Tuple
- 여러 개의 값을 순서대로 저장하는 변경 불가능한 시퀀스 자료형

## Tuple 표현
- 0개 이상의 객체를 포함하며 데이터 목록을 저장

- 소괄호 '()'로 표기

- 데이터는 어떤 자료형도 저장할 수 있음

```python
my_tuple_1 = ()

my_tuple_2 = (1,) #1개면 ,를 꼭 표시해줘야 튜플로 인식. 아니면 int로 인식한다.

my_tuple_3 = (1, 'a', 3, 'b', 5)
```

## Tuple의 시퀀스 특징
- 튜플도 string과 같이 요소의 변경이 불가능하다.

```python
my_tuple = (1, 'a', 3, 'b', 5)

# 인덱싱
print(my_tuple[1])  # a

# 슬라이싱
print(my_tuple[2:4])  # (3, 'b')
print(my_tuple[:3])  # (1, 'a', 3)
print(my_tuple[3:])  # ('b', 5)
print(my_tuple[0:5:2])  # (1, 3, 5)
print(my_tuple[::-1])  # (5, 'b', 3, 'a', 1)

# 길이
print(len(my_tuple))  # 5
```

### Tuple은 변경 불가
```python
my_tuple = (1, 'a', 3, 'b', 5)

my_tuple[1] = 'z'
# TypeError: 'tuple' object does not support item assignment
```

## Tuple의 사용처
- 튜플의 불변 특성을 사용하여 안전하게 여러 개의 값을 전달, 그룹화, 다중 할당 등

- 개발자가 직접 사용하기 보다 파이썬 내부 동작에서 주로 사용됨

```python
x, y = (10, 20) # or x, y = 10, 20  이 또한 튜플로 지정이 된 것이다.
print (x) # 10
print (y) # 20

# 파이썬은 쉼표를 튜플 생성자로 사용하니 괄호는 생략 가능
x, y = 10, 20
```