# Method

[Method](#method-메서드)
[Method 특징](#method-특징)
[Method 호출 방법](#method-호출-방법)

---

## Method 메서드
- 객체에 속한 함수

- 객체의 상태를 조작하거나 동작을 수행

## Method 특징
- 메서드는 클래스(class) 내부에 정의되는 함수

- 클래스는 파이썬에서 '타입을 표현하는 방법'이며 이미 은연중에 사용해왔음

- 예를 들어 `help` 함수를 통해 str을 호출해보면 class 였다는 것을 확인 가능

```python
"""
Help on class str in module builtins:

class str(object)
 |  str(object='') -> str
 |  str(bytes_or_buffer[, encoding[, errors]]) -> str
 |
 |  Create a new string object from the given object. If encoding or
 |  errors is specified, then the object must expose a data buffer
 |  …
"""
```

- 메서드는 어딘가(클래스)에 속해 있는 **함수**이며, 각 데이터 타입 별로 다양한 기능을 가진 메서드가 존재

## Method 호출 방법
```python
데이터 타입 객체.메서드()
```

```python
'hello'.capitalize()
```

### Method 호출 예시
```python
# 문자열 메서드 예시
print('hello'.capitalize()) # Hello
```

```python
# 리스트 메서드 예시
numbers = [1, 2, 3]
numbers.append(4)

print(numbers)  # [1, 2, 3, 4]
```