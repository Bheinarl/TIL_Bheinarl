# Hash Table

[Hash Table](#hash-table-해시-테이블)   
[Hash Table 원리](#hash-table-원리)   
[Hash](#hash-해시)   

[Hash Function](#hash-function-해시-함수)   
[set의 요소 & dict의 키와 Hash Table 관계](#set의-요소--dict의-키와-hash-table-관계)   
[Python에서의 Hash Function](#python에서의-hash-function)   

[Hashable](#hashable)   
[Hashable과 불변성 간의 관게](#hashable과-불변성-간의-관계)   
[가변형 객체가 Hashable하지 않은 이유](#가변형-객체가-hashable하지-않은-이유)   
[Hashable 객체가 필요한 이유](#hashable-객체가-필요한-이유)   

---

## Hash Table 해시 테이블
- 해시 함수를 사용하여 변환한 값을 index로 삼아 키(key)와 값(value)을 저장하는 자료 구조

- 데이터를 효율적으로 저장하고 검색하기 위해 사용

## Hash Table 원리
- 키를 해시 함수를 통해 해시 값을 변환하고, 이 해시 값을 인덱스로 사용하여 데이터를 저장하거나 검색
  - 데이터 검색이 매우 빠르게 이루어짐

- 파이썬을 재실행하면 해시 함수도 재실행되어 초기화됨

<div align='center'>

![Hash Table 원리](./images/hashtable원리_1.PNG.png)

</div>

## Hash 해시
- **임의의 크기를 가진 데이터**(key)를 **고정된 크기의 고유한 값**(index)으로 변환하는 것

- 이렇게 생성된 고유한 값은 주로 해당 데이터를 식별하는 데 사용될 수 있음
  - 일종의 ‘지문’과 같은 역할
  
  - 데이터를 고유하게 식별

- 파이썬에서는 해시 함수(hash function)를 사용하여 데이터를 해시(hash) 값으로 변환하며, 이 해시(hash) 값은 정수로 표현됨

## Hash Function 해시 함수
- 임의의 길이의 데이터를 입력 받아 고정된 길이의 데이터(hash 값)를 출력하는 함수

- 주로 hash table 자료 구조에 사용되며, 매우 빠른 데이터 검색을 위한 컴퓨터 소프트웨어에서 유용하게 사용

## set의 요소 & dict의 키와 Hash Table 관계
- 파이썬에서 set의 요소와 dict의 키는 hash table을 이용하여 중복되지 않는 고유한 값을 저장함

- set 내의 각 요소는 hash function를 통해 hash 값으로 변환되고, 이 hash 값을 기반으로 hash table에 저장됨

- 마찬가지로 dict의 키는 고유해야 하므로, 키를 hash function를 통해 hash 값으로 변환하여 hash table에 저장
  - 따라서 dict의 키는 매우 빠른 탐색 속도를 제공하며, 중복된 값을 허용하지 않음

## Python에서의 Hash Function
- Python에서 hash function의 동작 방식은 객체의 타입에 따라 달라짐

- 정수와 문자열은 서로 다른 타입이며, 이들의 hash 값을 계산하는 방식도 다름

### Python에서의 Hash Function - 정수
- 정수 값 자체가 곧 hash 값

- 같은 정수는 항상 같은 hash 값을 가짐

- hash table에 정수를 저장할 때 효율적인 방법

- 예를 들어, hash(1)과 hash(2)는 항상 서로 다른 hash 값을 갖지만, hash(1)은 항상 동일한 hash 값을 갖게 됨

```python
print(hash(1)) # 1
print(hash(1)) # 1
```

### Python에서의 Hash Function - 문자열
- 반환 값이 매번 다름

- 문자열은 가변적인 길이를 가지고 있고, 문자열에 포함된 각 문자들의 유니코드 코드 포인트 등을 기반으로 hash 값을 계산

- 이로 인해 문자열의 hash 값은 실행 시마다 다르게 계산됨

```python
print(hash('a')) # 실행시마다 다름
print(hash('a')) # 위의 값과 또 다름
```

## set의 pop 메서드의 결과와 Hash Table의 관계
- set의 pop()에서 임의의 요소를 제거하고 반환

- 실행할 때마다 다른 요소를 얻는다는 의미에서 '무작위'가 아니라<br />**'임의'라는 의미에서 무작위**
  - By ‘arbitrary’ the docs don’t mean ‘random’

- Hash Table에 나타나는 순서대로 반환하는 것
  - Hash Table에 배치되는 것이 순서가 없어서 순서가 없다고 판단

## hashable
- hash() 함수의 인자로 전달해서 결과를 반환 받을 수 있는 객체

- 대부분의 불변형 데이터 타입은 hashable

- 단, tuple의 경우 불변형이지만 hash 불가능한 객체를 참조할 때는 tuple 자체도 hash 불가능해짐

```python
print(hash(1))
print(hash(1.0))
print(hash('1'))
print(hash((1, 2, 3)))

print(hash((1, 2, [3, 4]))) # TypeError: unhashable type: 'list'
```

## hashable과 불변성 간의 관계
- hash table의 키는 불변해야 함
  - 객체가 생성된 후에 그 값을 변경할 수 없어야 함

- 불변 객체는 hash 값이 변하지 않으므로 동일한 값에 대해 일관된 hash 값을 유지할 수 있음

- 단, “hash 가능하다 != 불변하다”

## 가변형 객체가 hashable하지 않은 이유
- 값이 변경될 수 있기 때문에 동일한 객체에 대한 hash 값이 변경될 가능성이 있음

- Hash Table의 무결성 유지 불가

- 가변형 객체가 변경되면 hash 값이 변경되기 때문에, 같은 객체에 대한 서로 다른 hash 값이 반환될 수 있음

- hash 값의 일관성 유지 불가

```python
print(hash([1, 2, 3])) # TypeError: unhashable type: 'list'

my_set = {[1, 2, 3], 1, 2, 3, 4, 5} # TypeError: unhashable type: 'list'

my_dict = {{3, 2}: 'a'} # TypeError: unhashable type: 'list'
```

## hashable 객체가 필요한 이유
1. Hash Table 기반 자료 구조 사용
   - set, dict의 key
   
   - 중복 값 방지
   
   - 빠른 검색과 조회

2. 불변성을 통한 일관된 hash 값

3. 안정성과 예측 가능성 유지