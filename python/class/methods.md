# Method

[Method 종류](#method-종류)   

[Instance Method](#instance-method-인스턴스-메서드)   
[인스턴스 메서드 구조](#인스턴스-메서드-구조)   
[self 동작 원리](#self-동작-원리)   

[Constructor Method](#constructor-method-생성자-메서드)   
[생성자 메서드 구조](#생성자-메서드-구조)   

[Class Method](#class-method-클래스-메서드)   
[클래스 메서드](#클래스-메서드-구조)   

[Static Method](#static-method-스태틱정적-메서드)   
[스태틱 메서드 구조](#스태틱-메서드-구조)   

[메서드 정리](#메서드-정리)   
[누가 어떤 메서드를 사용해야 할까](#누가-어떤-메서드를-사용해야할까)   
[클래스가 할 수 있는 것](#클래스가-할-수-있는-것)   
[인스턴스가 할 수 있는 것](#인스턴스가-할-수-있는-것)   

[매직 메서드](#매직-메서드)   

[데코레이터](#데코레이터)   

---

## Method 종류
- 인스턴스 메서드 Instance Method

- 클래스 메서드 Class Method

- 정적 메서드 Static Method

<div align='center'>

![Method종류_1](./images/메서드종류_1.png)

</div>

## Instance Method 인스턴스 메서드
- 클래스로부터 생성된 각 인스턴스에서 호출할 수 있는 메서드

- 인스턴스의 상태를 조작하거나 동작을 수행

## 인스턴스 메서드 구조
- 클래스 내부에 정의되는 메서드의 기본

- 반드시 첫 번째 매개변수(첫 번째 위치인자)로 **인스턴스 자신**(self)을 전달받음

- **self는 매개변수 이름일 뿐이며 다른 이름으로 설정 가능하지만, 다른 이름을 사용하지 않을 것을 강력히 권장**

```py
class MyClass:

    def instance_method(self, arg1, ...):
        pass
```

## self 동작 원리
- upper 메서드를 사용해 문자열 'hello'를 대문자로 변경하기

```py
'hello'.upper()
```

- 하지만 실제 파이썬 내부 동작은 다음과 같이 진행됨

```py
str.upper('hello') # 클래스(str)가 메서드(upper)를 호출하고 'hello'(self)가 작동
```

- str 클래스가 upper 메서드를 호출했고, 그 첫번째 인자로 문자열 인스턴스가 들어간 것

- **인스턴스 메서드의 첫번째 매개변수가 반드시 인스턴스 자기 자신인 이유**

- `'hello'.upper()` 은 `str.upper('hello')`를 객체 지향 방식의 메서드로 호출하는 표현 (단축형 호출)

- 'hello'라는 문자열 객체가 단순히 어딘가의 함수로 들어가는 인자가 아닌 객체 스스로 메서드를 호출하여 코드를 동작하는 객체 지향적 표현

## Constructor Method 생성자 메서드
- 인스턴스 객체가 생성될 때 자동으로 호출되는 메서드

- 인스턴스 변수들의 초기값을 설정

## 생성자 메서드 구조

```py
class Person:
    def __init__(self, name):
        self.name = name 
# 왼쪽 name : 인스턴스 변수 name
# 오른쪽 name : 함수의 매개변수 이름
# 아무 관련 없다.
        print('인스턴스가 생성되었습니다.')

    def greeting(self):
        print(f'안녕하세요. {self.name}입니다.') # 인스턴스 변수 name 출력

person1 = Person('지민')  # 인스턴스가 생성되었습니다.
person1.greeting()  # 안녕하세요. 지민입니다.
```

## Class Method 클래스 메서드
- 클래스가 호출하는 메서드

- 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행

## 클래스 메서드 구조
- `@classmethod` 데코레이터를 사용하여 정의

- 데코레이터는 원본은 유지한 채로 함수의 기능을 추가하는 함수

- 호출 시, 첫번째 인자로 호출하는 클래스(`cls`)가 전달됨

- **cls는 매개변수 이름일 뿐이며 다른 이름으로 설정 가능 하지만 다른 이름을 사용하지 않을 것을 강력히 권장**

```py
class MyClass:
        
    @classmethod
    def class_method(cls, arg1, ...):
        pass
```

### 클래스 메서드 예시

```py
class Person:
    count = 0

    def __init__(self, name):
        self.name = name
        Person.count += 1

    @classmethod
    def number_of_population(cls):
        print(f'인구수는 {cls.count}입니다.')
# 이 상황의 cls는 모른다.
#아직 number_of_population을 호출한 적이 없기 때문에 정해지지 않았다.

# cls.count == Person.count는 아니다. 지금 상황에서는 맞을 수 있어도,
# 후에 상속(하위 클래스)가 생길 수 있기 때문에 항상 맞는 것은 아니다.

person1 = Person('iu')
person2 = Person('BTS')

Person.number_of_population() # 인구수는 2입니다.
# 클래스 메서드이기 때문에 클래스 Person이 호출해야 한다.
```

## Static Method 스태틱(정적) 메서드
- 클래스와 인스턴스 상관없이 독립적으로 동작하는 메서드

- 주로 클래스와 관련이 있지만 인스턴스와 상호작용이 필요하지 않은 경우에 사용

## 스태틱 메서드 구조
- `@staticmethod` 데코레이터를 사용하여 정의

- 호출 시 필수적으로 작성해야 할 매개변수가 없음

- 즉, 객체 상태나 클래스 상태를 수정할 수 없으며 단지 기능(행동)만을 위한 메서드로 사용

- 우리가 일반적으로 사용했던 함수와 비슷함

```py
class MyClass:
        
    @staticmethod
    def static_method(arg1, ...):
        pass
```

### 스태틱 메서드 예시
- 단순히 문자열을 조작하는 기능을 제공하는 메서드 예시

```py
class StringUtils:

		def __init__(self):
				pass
				
    @staticmethod
    def reverse_string(string):
        return string[::-1]
# 문자열 뒤집기

    @staticmethod
    def capitalize_string(string):
        return string.capitalize()
# 첫 문자를 대문자로 변경

# 스태틱 메서드는 클래스 변수나 인스턴스 변수 만들지 않고, 단순 로직만

text = 'hello, world'

reversed_text = StringUtils.reverse_string(text)
print(reversed_text) # dlrow ,olleh

capitalized_text = StringUtils.capitalize_string(text)
print(capitalized_text) # Hello, world

# 스태틱 메서드 호출은 클래스가 호출한다.

# 인스턴스 메서드는 인스턴스가 하고, 클래스 메서드와 스태틱 메서드는 클래스가 호출
```

## 메서드 정리
- 인스턴스 메서드 ‘@’
  - 인스턴스의 상태를 변경하거나, 해당 인스턴스의 특정 동작을 수행

- 클래스 메서드
  - 인스턴스의 상태에 의존하지 않는 기능을 정의
  
  - 클래스 변수를 조작하거나 클래스 레벨의 동작을 수행

- 스태틱 메서드 ‘@’
  - 클래스 및 인스턴스와 관련이 없는 일반적인 기능을 수행

## 누가 어떤 메서드를 사용해야할까
- 클래스가 사용해야 할 것
  - 클래스 메서드
  
  - 스태틱 메서드

- 인스턴스가 사용해야 할 것
  - 인스턴스 메서드

- 예시 클래스로 클래스와 인스턴스가 각각 모든 메서드를 호출해보기

```py
class MyClass:

    def instance_method(self):
        return 'instance method', self
            
    @classmethod
    def class_method(cls):
        return 'class method', cls

    @staticmethod
    def static_method():
        return 'static method'
```

## 클래스가 할 수 있는 것
- 클래스는 모든 메서드를 호출할 수는 있음

- 하지만 **클래스는 클래스 메서드와 스태틱 메서드만 사용하도록 한다.**

## 인스턴스가 할 수 있는 것
- 인스턴스는 모든 메서드를 호출할 수는 있음

- 하지만 **인스턴스는 인스턴스 메서드만 사용하도록 한다.**

### 할수 있다 != 써도 된다
- 각자의 메서드는 OOP 패러다임에 따라 명확한 목적에 맞게 설계된 것이기 때문에 클래스와 인스턴스 각각 올바른 메서드만 호출하여 사용한다.

## 매직 메서드
- 특별한 인스턴스 메서드

- 특정 상황에 자동으로 호출되는 메서드

- Double underscore( __  )가 있는 메서드는 특수한 동작을 위해 만들어진 메서드
  - 스페셜 메서드 혹은 매직 메서드라고 불림

```py
__str__(self)
__len__(self)__
__lt__(self, other)
__le__(self, other)
__eq__(self, other)
__gt__(self, other)
__ge__(self, other)
__ne__(self, other)
```

### 매직 메서드 예시
- `__str__(self)`
  - 내장 함수 print에 의해 호출되어 객체 출력을 문자열 표현으로 변경

```py
class Circle:
    def __init__(self, r):
        self.r = r

    def __str__(self):
        return f'원의 반지름: {self.r}'
    
c1 = Circle(10)
c2 = Circle(1)

print(c1) # 원의 반지름: 10
print(c2) # 원의 반지름: 1
```

## 데코레이터
- 다른 함수의 코드를 유지한 채로 수정하거나 확장하기 위해 사용되는 함수

### 데코레이터 정의

```py
def my_decorator(func):
    def wrapper():
        # 함수 실행 전에 수행할 작업
        print('함수 실행 전')
        # 원본 함수 호출
        result = func()
        # 함수 실행 후에 수행할 작업
        print('함수 실행 후')
        return result
    return wrapper
```

### 데코레이터 사용

```py
@my_decorator
def my_function():
    print('원본 함수 실행') 
my_function()

"""
함수 실행 전
원본 함수 실행
함수 실행 후
"""
```