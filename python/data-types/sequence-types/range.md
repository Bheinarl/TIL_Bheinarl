# range

[range](#range-1)   
[range 표현](#range-표현)   
[range 특징](#range-특징)   


---

## range
- 연속된 정수 시퀀스를 생성하는 변경 불가능한 자료형

## range 표현
- range (시작 값, 끝 값, 증가 값)

- range(n)
  - 0 부터 n-1 까지의 숫자 시퀀스

- range(n,m)
  - n 부터 m-1 까지의 숫자 시퀀스

```python
my_range_1 = range(5)
my_range_2 = range(1, 10)

print(my_range_1)  # range(0, 5)
print(my_range_2)  # range(1, 10)
```

- 주로 반복문과 함께 사용 예정
```python
# 리스트로 형 변환 시 데이터 확인 가능
print(list(range(5)))   # [0, 1, 2, 3, 4]
print(list(range(1, 10)))  # [1, 2, 3, 4, 5, 6, 7, 8, 9]

# 반복문과 함께 활용
for i in range(1, 10):
    print(i)  # 1 2 3 4 5 6 7 8 9
for i in range(1, 10, 2):
    print(i)  # 1 3 5 7 9
```

## range 특징
- 증가 값이 없으면 1씩 증가
- 증가 값이 음수이면 감소 / 증가 값이 양수이면 증가
- 증가 값이 0이면 에러
- 증가 값이 음수이면 시작 값이 끝 값보다 커야 함
- 증가 값이 양수이면 시작 값이 끝 값보다 작아야 함

```python
my_range_1 = range(5)
my_range_2 = range(1, 10)

print(my_range_1)  # range(0, 5)
print(my_range_2)  # range(1, 10)

print(list(my_range_1)) # [0, 1, 2, 3, 4]
print(list(my_range_2)) # [1, 2, 3, 4, 5, 6, 7, 8, 9]
```