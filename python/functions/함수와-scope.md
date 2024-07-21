# 함수와 Scope

[Python의 범위 Scope](#python의-범위scope)   
[범위와 변수 관계](#범위와-변수-관계)   
[Scope 예시](#scope-예시)   

[변수 수명 주기](#변수-수명-주기-lifecycle)   
[이름 검색 규칙](#이름-검색-규칙-name-resolution)   
[`global` 키워드](#global-키워드)   

---

## Python의 범위(Scope)
- 함수는 코드 내부에 `local scope`를 생성하며, 그 외의 공간인 `global scope`로 구분

## 범위와 변수 관계
- scope
  - global scope : 코드 어디에서든 참조할 수 있는 공간

  - local scope : 함수가 만든 scope (함수 내부에서만 참조 가능)

- variable
  - global variable : global scope에 정의된 변수

  - local variable : local scope에 정의된 변수

## Scope 예시
```python
def func():
    num = 20
    print('local', num)  # local 20


func()

print('global', num)  # NameError: name 'num' is not defined
```

- `num`은 local scope에 존재하기 때문에 global에서는 사용할 수 없음

- 이는 변수의 **수명 주기** 연관이 있음

## 변수 수명 주기 (Lifecycle)
- 변수의 수명 주기는 변수가 선언되는 위치와 scope에 따라 결정됨

1. built-in scope
   - 파이썬이 실행된 이후부터 영원히 유지

2. global scope
   - 모듈이 호출된 시점 이후 혹은 인터프리터가 끝날 때까지 유지

3. local scope
   - 함수가 호출될 때 생성되고, 함수가 종료될 때까지 유지

## 이름 검색 규칙 (Name Resolution)
- 파이썬에서 사용되는 이름(식별자)들은 특정한 이름 공간(namespace)에 저장되어 있음

- 아래와 같은 순서로 이름을 찾아 나가며, LEGB Rule이라고 부름
  1. Local scope : 지역 범위 (현재 작업 중인 범위)

  2. Enclosed scope : 지역 범위 한 단계 위 범위

  3. Global scope : 최상단에 위치한 범위

  4. Built-in scope : 모든 것을 담고 있는 범위 (정의하지 않고 사용할 수 있는 모든 것)

- **함수 내에서는 바깥 scope의 변수에 접근 가능하나 수정은 할 수 없음**

### 이름 검색 규칙 예시
- sum 이라는 이름을 global scope에서 사용하게 되면서 기존에 built-in scope에 있던 내장 함수 `sum`을 사용하지 못하게 됨

- sum을 참조 시 LEGB Rule에 따라 global에서 먼저 찾기 때문

```python
print(sum) # <built-in function sum>
print(sum(range(3))) # 3

sum = 5

print(sum) # 5
print(sum(range(3))) # TypeError: 'int' object is not callable
```

```python
a = 1
b = 2


def enclosed():
    a = 10
    c = 3

    def local(c):
        print(a, b, c) # 10 2 500

    local(500)
    print(a, b, c) # 10 2 3


enclosed()
print(a, b) # 1 2

"""
1.
def local(c):
        print(a, b, c)

    local(500)
# local(c)에서 c는 매개변수이므로 c가 입력받을 때 출력
# local(500)일때 출력
"""

"""
2.
def enclosed():
    a = 10
    c = 3

    def local(c):
        print(a, b, c) # 10 2 500

    local(500)
    print(a, b, c) # 10 2 3

# local은 끝났고, enclosed만 본다.
# a = 10, c = 3, b는 없으므로 더 위로 가서 b = 2를 사용
"""
```

## `global` 키워드
- 변수의 scope를 global scope로 지정하기 위해 사용

- 일반적으로 함수 내에서 전역 변수로 수정하려는 경우에 사용

```python
num = 0 # 전역 변수


def increment():
     global num # num를 전역 변수로 선언
     num += 1


print(num) # 0
increment()
print(num) # 1
```

### `global` 키워드 주의사항
- `global` 키워드 선언 전에 참조 불가

```python
num = 0

def increment():
    # SyntaxError: name 'num' is used prior to global declaration
    print(num)
    global num
    num += 1
```

- 매개변수에는 `global` 키워드 사용 불가

```python
num = 0


def increment(num):
    # "num" is assigned before global declaration
    global num
    num += 1
```