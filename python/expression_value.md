# Expression & Value


---
## 표현식 (Expression)
- 값으로 평가될 수 있는 코드 조각

## 값 (Value)
- 표현식이 평가된 결과

## 평가 (Evaluate)
- 표현식을 실행하여 값을 얻는 과정
- 표현식을 순차적으로 평가하여 프로그램의 동작을 결정

## 문장 (Statement)
- 실행 가능한 동작을 기술하는 코드 (조건문, 반복문 , 함수 정의 등)

## 타입 (Type)
- 변수나 값이 가질 수 있는 데이터의 종류를 의미
- 어떤 종류의 데이터인지, 어떻게 해석되고 처리되어야 하는지를 정의
- 타입은 2가지 요소로 이루어짐
  - '값'과 '값에 적용할 수 있는 연산 (연산자)'

## 할당문

```python
degrees = 36.5
```
- "변수 degrees에 값 36.5를 **할당**했다."
- 하나의 문장으로 취급

<br />

```python
degrees = 'abc'
```
- "변수 degrees에 값 'abc'를 재할당했다.
- "변수 degrees를 36.5에서 'abc'로 재할당했다."

<br />


```python
variable = expression
```
1. 할당 연산자 (=) 오른쪽에 있는 표현식을 평가해서 값(메모리 주소)을 생성

2. 값의 메모리 주소를 '=' 왼쪽에 있는 변수에 저장

<br />

- 존재하지 않는 변수라면
  - 새 변수를 생성

- 기존에 존재했던 변수라면
  - 기존 변수를 재사용해서 변수에 들어 있는 메모리 주소를 변경

## 변수명 규칙
- 영문 알파벳, 언더스코어( _ ), 숫자로 구성
- 숫자로 시작할 수 없음
- 대소문자를 구분
- 아래 키워드는 파이썬의 내부 예약어로 사용할 수 없음
```python
['False', 'None', 'True', '__peg_parser__', 'and', 'as', 'assert', 'async', 'await', 
'break', 'class', 'continue', 'def', 'del', 'elif', 'else', 'except', 'finally', 'for', 
'from', 'global', 'if', 'import', 'in', 'is', 'lambda', 'nonlocal', 'not', 'or', 
'pass', 'raise', 'return', 'try', 'while', 'with', 'yield']
```

## 변수, 값 그리고 메모리
- 메모리의 모든 위치에는 그 위치를 고유하게 식별하는 메모리 주소가 존재
- 객체 (Object)
  - 타입을 갖는 메모리 주소 내 값
- 변수는 그 변수가 참조하는 객체의 메모리 주소를 가짐