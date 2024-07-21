# Conditional Statement

[Conditional Statement](#conditional-statement-조건문)   
[`if` Statement](#if-statement)   
[복수 조건문](#복수-조건문)    
[중첩 조건문](#중첩-조건문)   

---

## Conditional Statement 조건문
- 주어진 조건식을 평가하여 해당 조건이 참(True)인 경우에만 코드 블록을 실행하거나 건너뜀

### 파이썬 조건문에 사용되는 키워드
- `if`, `elif`, `else`

## `if` Statement
- `if` Statement의 기본 구조

```python
if 표현식:
    코드 블록
elif 표현식:
    코드 불록
else:
    코드 블록
```

### 조건문 예시
```python
a = 5

if a > 3:
    print('3 초과')
else:
    print('3 이하')

print(a)
```

```python
a = 3

if a > 3:
    print('3 초과')
else:
    print('3 이하')

print(a)
```

## 복수 조건문
- 조건식을 동시에 검사하는 것이 아니라 **순차적**으로 비교

```python
dust = 35
    
if dust > 150:
    print('매우 나쁨')
elif dust > 80:
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')
    
# 보통
```

## 중첩 조건문
```python
dust = 480

if dust > 150:
    print('매우 나쁨')
    """
    중첩 조건문
    """
    if dust > 300:
        print('위험해요! 나가지 마세요!')
elif dust > 80:
    print('나쁨')
elif dust > 30:
    print('보통')
else:
    print('좋음')
```
