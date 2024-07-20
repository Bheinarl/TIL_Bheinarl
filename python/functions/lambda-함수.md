# Lambda 함수

[람다 표현식](#람다-표현식-lambda-expressions)   
[람다 함수 구조](#람다-함수-구조)   
[람다 표현식 예시](#람다-표현식-예시)   
[람다 표현식 활용 with `map`](#람다-표현식-활용-with-map-함수)   

---

## 람다 표현식 Lambda Expressions
- 익명 함수를 만드는 데 사용되는 표현식

- 한 줄로 간단한 함수를 정의

- 주로 일회성으로 사용

## 람다 함수 구조
```python
lambda 매개변수: 표현식
```
- `lambda` 키워드
  - 람다 함수를 선언하기 위해 사용되는 키워드

- 매개변수
  - 함수에 전달되는 매개변수들
  
  - 여러 개의 매개변수가 있을 경우 쉼표로 구분

- 표션식
  - 함수의 실행되는 코드 블록으로, 결과값을 반환하는 표현식으로 작성


## 람다 표현식 예시
- 간단한 연산이나 함수를 한 줄로 표현할 때 사용

- 함수를 매개변수로 전달하는 경우에도 유용하게 활용

```python
# 람다 함수 미적용 코드
def addition(x, y):
    return x + y

result = addition(3, 5)
print(result) # 8
```

```python

# 람다 함수 적용 코드
addition = lambda x, y: x + y

result = addition(3, 5)
print(result) # 8
```
## 람다 표현식 활용 (with `map` 함수)
```python
numbers = [1, 2, 3, 4, 5]
def square(x):
    return x**2

# lambda 미사용
squared1 = list(map(square, numbers))
print(squared1)  # [1, 4, 9, 16, 25]

# lambda 사용
squared2 = list(map(lambda x: x**2, numbers))
print(squared2)  # [1, 4, 9, 16, 25]
```