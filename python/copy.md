# Copy

[Copy](#copy-복사)   
[변경 가능한 데이터 타입의 복사](#변경-가능한-데이터-타입의-복사)   
[변경 불가능한 데이터 타입의 복사](#변경-불가능한-데이터-타입의-복사)   
[복사 유형](#복사-유형)   
[할당](#할당-assignment)   
[얕은 복사](#얕은-복사-shallow-copy)   
[깊은 복사](#깊은-복사-deep-copy)   

---

## Copy 복사
- 파이썬에서는 데이터 분류에 따라 복사가 달라짐

- '변경 가능한 데이터 타입'과 '변경 불가능한 데이터 타입'을 다르게 다룸

## 변경 가능한 데이터 타입의 복사

```python
a = [1, 2, 3, 4]
b = a
b[0] = 100

print(a)  # [100, 2, 3, 4]
print(b)  # [100, 2, 3, 4]
```

![변경 가능한 데이터 타입의 복사 이미지](./images/변경가능한데이터타입의복사_1.png)

## 변경 불가능한 데이터 타입의 복사

```python
a = 20
b = a
b = 10

print(a)  # 20
print(b)  # 10
## b가 20으로 재할당 받은 것
```

![변경 불가능한 데이터 타입의 복사 이미지](./images/변경불가능한데이터타입의복사_1.png)

## 복사 유형
1. 할당 (Assignment)

2. 얕은 복사 (Shallow Copy)

3. 깊은 복사 (Deep Copy)

## 할당 Assignment
- 리스트 복사 예시
  - 할당 연산자(=)를 통한 복사는 해당 객체에 대한 객체 참조를 복사

```python
original_list = [1, 2, 3]
copy_list = original_list
print(original_list, copy_list)  # [1, 2, 3] [1, 2, 3]

copy_list[0] = 'hi'
print(original_list, copy_list)  # ['hi', 2, 3] ['hi', 2, 3]
```

## 얕은 복사 Shallow Copy
## 깊은 복사 Deep Copy
