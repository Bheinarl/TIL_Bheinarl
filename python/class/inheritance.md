# Inheritance

[Inheritance](#inheritance-1)
[상속이 필요한 이유](#상속이-필요한-이유)
[클래스 상속](#클래스-상속)
[상속을 사용한 계층 구조 변경](#상속을-사용한-계층-구조-변경)
[다중 상속](#다중-상속)

[MRO](#mro-method-resolution-order)
[`super()`](#super)
[MRO가 필요한 이유](#mro가-필요한-이유)
[`super()`의 2가지 사용 사례](#super의-2가지-사용-사례)

---
## Inheritance
- 기존 클래스의 속성과 메서드를 물려받아 새로운 하위 클래스를 생성하는 것

## 상속이 필요한 이유
1. 코드 재사용
   - 상속을 통해 기존 클래스의 속성과 메서드를 재사용할 수 있음
   
   - 새로운 클래스를 작성할 때 기존 클래스의 기능을 그대로 활용할 수 있으며, 중복된 코드를 줄일 수 있음

2. 계층 구조
   - 상속을 통해 클래스들 간의 계층 구조를 형성할 수 있음
   
   - 부모 클래스와 자식 클래스 간의 관계를 표현하고, 더 구체적인 클래스를 만들 수 있음

3. 유지 보수의 용이성
   - 상속을 통해 기존 클래스의 수정이 필요한 경우, 해당 클래스만 수정하면 되므로 유지 보수가 용이해짐
   
   - 코드의 일관성을 유지하고, 수정이 필요한 범위를 최소화할 수 있음

## 클래스 상속

### 상속 없이 구현하는 경우

- 학생 / 교수 정보를 나타내기 어려움

```py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):
        print(f'반갑습니다. {self.name}입니다.')


s1 = Person('김학생', 23)
s1.talk() # 반갑습니다. 김학생입니다.

p1 = Person('박교수', 59)
p1.talk() # 반갑습니다. 박교수입니다.
```

- 학생 / 교수 클래스로 분리했지만 메서드가 중복으로 정의됨

```py
class Professor:
    def __init__(self, name, age, department):
        self.name = name # 이름 중복
        self.age = age # 나이 중복
        self.department = department

    def talk(self): # 중복
        print(f'반갑습니다. {self.name}입니다.')

class Student:
    def __init__(self, name, age, gpa):
        self.name = name # 이름 중복
        self.age = age # 나이 중복
        self.gpa = gpa

    def talk(self): # 중복
        print(f'반갑습니다. {self.name}입니다.')
```

## 상속을 사용한 계층 구조 변경

```py
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def talk(self):  # 메서드 재사용
        print(f'반갑습니다. {self.name}입니다.')


class Professor(Person): # (Person) 이 부분이 상속이 일어나는 위치
    def __init__(self, name, age, department):
        self.name = name
        self.age = age
        self.department = department


class Student(Person): # (Person) 이 부분이 상속이 일어나는 위치
    def __init__(self, name, age, gpa):
        self.name = name
        self.age = age
        self.gpa = gpa


p1 = Professor('박교수', 49, '컴퓨터공학과')
s1 = Student('김학생', 20, 3.5)

# 부모 Person 클래스의 talk 메서드를 활용
p1.talk() # 반갑습니다. 박교수입니다.

# 부모 Person 클래스의 talk 메서드를 활용
s1.talk() # 반갑습니다. 김학생입니다.
```

## 다중 상속
- 둘 이상의 상위 클래스로부터 여러 행동이나 특징을 상속받을 수 있는 것

- 상속받은 모든 클래스의 요소를 활용 가능함

- 중복된 속성이나 메서드가 있는 경우 **상속 순서에 
의해 결정**됨

### 다중 상속 예시 1

```py
class Person:
    def __init__(self, name):
        self.name = name

    def greeting(self):
        return f'안녕, {self.name}'


class Mom(Person):
    gene = 'XX'

    def swim(self):
        return '엄마가 수영'


class Dad(Person):
    gene = 'XY'

    def walk(self):
        return '아빠가 걷기'


class FirstChild(Dad, Mom):
    def swim(self):
        return '첫째가 수영'

    def cry(self):
        return '첫째가 응애'


baby1 = FirstChild('아가')
print(baby1.cry()) # 첫째가 응애
print(baby1.swim()) # 첫째가 수영
print(baby1.walk()) # 아빠가 걷기
print(baby1.gene) # XY

"""
FirstChild가 Dad, Mom 순으로 인자를 받으므로,
walk가 없으면 Dad에서 찾고, 없으면 Mom에서 찾는다.
함수의 위치가 아닌 인자의 순서가 중요
"""
```

### 다중 상속 예시 2
- 다이아몬드 문제
  - 두 클래스 B와 C가 A에서 상속되고 클래스 D가 B와 C 모두에서 상속될 때 발생하는 모호함
  
  - B와 C가 재정의한 메서드가 A에 있고 D가 이를 재정의하지 않은 경우라면 D는 B의 메서드 중 어떤 버전을 상속하는가? 아니면 C의 메서드 버전을 상속하는가?

### 파이썬에서의 해결책
- MRO(Method Resolution Order) 알고리즘을 사용하여 클래스 목록을 생성

- 부모 클래스로부터 상속된 속성들의 검색을 깊이 우선으로, 왼쪽에서 오른쪽으로, 계층 구조에서 겹치는 같은 클래스를 두 번 검색하지 않음

- 그래서, 속성이 D 에서 발견되지 않으면, B 에서 찾고, 거기에서도 발견되지 않으면, C 에서 찾고, 이런 식으로 진행됨

```py
class D(B, C):
    pass
```

## MRO Method Resolution Order
- 메서드 결정 순서

- 부모 클래스 순서대로 결정

## `super()`
- 부모 클래스 객체를 반환하는 내장 함수

- 다중 상속 시 MRO를 기반으로 현재 클래스가 상속하는 모든 부모 클래스 중 다음에 호출될 메서드를 결정하여 자동으로 호출

### `super()` 사용 예시 1 (단일 상속)
- 사용 전

```py
class Person:
    def __init__(self, name, age, number, email):
        self.name = name
        self.age = age
        self.number = number
        self.email = email


class Student(Person):
    def __init__(self, name, age, number, email, student_id):
        self.name = name
        self.age = age
        self.number = number
        self.email = email
        self.student_id = student_id
```

- 사용 후

```py
class Person:
    def __init__(self, name, age, number, email):
        self.name = name
        self.age = age
        self.number = number
        self.email = email


class Student(Person):
    def __init__(self, name, age, number, email, student_id):
        # Person의 init 메서드 호출
        super().__init__(name, age, number, email)
        self.student_id = student_id
```

### `super()` 사용 예시 2 (복수 상속)

```py
class ParentA:
    def __init__(self):
        self.value_a = 'ParentA'

    def show_value(self):
        print(f'Value from ParentA: {self.value_a}')


class ParentB:
    def __init__(self):
        self.value_b = 'ParentB'

    def show_value(self):
        print(f'Value from ParentB: {self.value_b}’)


class Child(ParentA, ParentB):
    def __init__(self):
        super().__init__() # ParentA 클래스의 __init__ 메서드 호출
        self.value_c = 'Child’
        ParentB.__init__() # child.value_b를 갖고싶다면. 주로 사용 X

    def show_value(self):
        super().show_value() # ParentA 클래스의 show_value 메서드 호출
        print(f'Value from Child: {self.value_c}')

child = Child()
child.show_value()

"""
작성하는 순간에는 super로 인하여 
A의 show_value인지, B의 show_value인지 알 수 없으므로
잘 생각하면서 코드를 짜야 한다.

A의 show_value는 MRO를 따라서 super를 통해 사용 가능하지만,
B의 show_value는 직접 호출하는 수 밖에 없다.

child는 의 인스턴스는 2개
child.value_a # super(__init__)으로 인하여 ParentA에게 받은 인스턴스
child.vaule_c # class Child의 self.value_c로 인하여 발생한 인스턴스

child.value_b는 아니다.
super(__init__)은 A에게 갔기 때문에 B까지 가지 못했다.
print(child.value_b) 하면 Error 발생
"""
```

### `mro()` 사용 예시

```py
class A:
    def __init__(self):
        print('A Constructor')

class B(A):
    def __init__(self):
        super().__init__()
        print('B Constructor')

class C(A):
    def __init__(self):
        super().__init__()
        print('C Constructor')
          
class D(B, C):
    def __init__(self):
        super().__init__()
        print('D Constructor')

print(D.mro())
# [<class '__main__.D'>, <class '__main__.B'>, <class '__main__.C'>, <class '__main__.A'>, <class 'object'>]
```

## MRO가 필요한 이유
- 부모 클래스들이 여러 번 액세스 되지 않도록,<br />각 클래스에서 지정된 왼쪽에서 오른쪽으로 가는 순서를 보존하고,<br />각 부모를 오직 한 번만 호출하고,<br />부모들의 우선순위에 영향을 주지 않으면서 서브 클래스를 만드는 단조적인 구조 형성

- 프로그래밍 언어의 신뢰성 있고 확장성 있는 클래스를 설계할 수 있도록 도움

- 클래스 간의 메서드 호출 순서가 예측 가능하게 유지되며, 코드의 재사용성과 유지보수성이 향상

## `super()`의 2가지 사용 사례
1. 단일 상속 구조
   - 명시적으로 이름을 지정하지 않고 부모 클래스를 참조할 수 있으므로, 코드를 더 유지 관리하기 쉽게 만들 수 있음
   
   - 클래스 이름이 변경되거나 부모 클래스가 교체되어도 `super()`를 사용하면 코드 수정이 더 적게 필요

2. 다중 상속 구조
   - MRO를 따른 메서드 호출
   
   - 복잡한 다중 상속 구조에서 발생할 수 있는 문제를 방지
