# set Method

[set](#set-세트)   
[set Method](#set-method-세트-메서드)   
[`.add(x)`](#addx)   
[`.clear()`](#clear)   
[`.remove(x)`](#removex)   
[`.discard()`](#discard)   
[`.update(iterable)`](#updateiterable)   
[set의 집합 메서드](#set의-집합-메서드)   
   
---
## set 세트
- 고유한 항목들의 정렬되지 않은 컬렉션

- 중복 X, 순서 X

- 빈 set 생성은 `a = set()`

- `b = { }` 이렇게 만들면 b는 tuple

## set Method 세트 메서드
|메서드|설명|
|:-:|:-:|
|`.add(x)`|set에 항목 x를 추가.<br />이미 x가 있다면 변화 없음|
|`.clear()`|set의 모든 항목을 제거|
|`.remove(x)`|set에서 항목 x를 제거.<br />항목 x가 없을 경우 Key Error|
|`.pop()`|set에서 랜덤하게 항목을 반환하고, 해당 항목을 제거|
|`.discard(x)`|set에서 항목 x를 제거|
|`.update(iterable)`|set에 다른 iterable 요소를 추가|


## `.add(x)`
- set에 x를 추가

- `.append`와 비슷함

```python
my_set = {'a', 'b', 'c', 1, 2, 3}

my_set.add(4)
print(my_set)  # {1, 'b', 3, 2, 'c', 'd', 'a’, 4}
    
my_set.add(4)
print(my_set)  # {1, 'b', 3, 2, 4 'c', 'd', 'a’}
    
# 중복 X, 순서 X
```

## `.clear()`
- set의 모든 항목을 제거

```python
my_set = {'a', 'b', 'c', 1, 2, 3}
    
my_set.clear()
print(my_set) # set()
              # 빈 set는 항상 이렇게 표시
              # 절대 { } 아님
```

## `.remove(x)`
- set에서 항목 x를 제거

```python
my_set = {'a', 'b', 'c', 1, 2, 3}
    
my_set.remove(2)
print(my_set)  # {'b', 1, 3, 'c', 'a'}
    
my_set.remove(10)
print(my_set)  # KeyError
```

## `.discard()`
- set에서 항목 x를 제거

- remove와 달리 Error 없음

```python
my_set = {1, 2, 3}
    
my_set.discard(2)
print(my_set)  # {1, 3, 'a', 'c', 'b’}
   
my_set.discard(10) # 아무 일도 일어나지 않음
```

## `.pop()`
- 세트에서 **임의의** 요소를 제거하고 **반환**

- 규칙 X

```python
my_set = {'a', 'b', 'c', 1, 2, 3}
    
element = my_set.pop()
print(element)  # 1
print(my_set)  # {2, 3, 'b', 'a', 'c'}
```

## `.update(iterable)`
- set에서 다른 iterable 요소를 추가

- `.extend`와 비슷함

```python
my_set = {'a', 'b', 'c', 1, 2, 3}
    
my_set.update([1, 4, 5])
print(my_set)  # {1, 2, 3, 'c', 4, 5, 'b', 'a'}
```

## set의 집합 메서드
|메서드|설명|연산자|
|:-:|:-:|:-:|
|set1.difference(set2)|set1에는 들어있지만 set2에는 없는 항목으로 세트를 생성 후 반환|set1 - set2|
|set1.intersection(set2)|set1과 set2 모두 들어있는 항목으로 세트를 생성 후 반환|set1 & set2|
|set1.issubset(set2)|set1의 항목이 모두 set2에 들어있으면 True를 반환|set1 <= set2|
|set1.issuperset(set2)|set1가 set2의 항목을 모두 포함하면 True를 반환|set1 >= set2|
|set1.union(set2)|set1 또는 set2에 (혹은 둘 다) 들어있는 항목으로 세트를 생성 후 반환| set1 \| set2 |

### set의 집합 메서드 예시

```python
set1 = {0, 1, 2, 3, 4}
set2 = {1, 3, 5, 7, 9}
set3 = {0, 1}

print(set1.difference(set2))  # {0, 2, 4}
                              # set1 - set2
print(set1.intersection(set2))  # {1, 3}
                                # set1 교집합 set2
print(set1.issubset(set2))  # False
                            # 함수가 is--- 이므로 True / False 로 반환
print(set3.issubset(set3))  # True
print(set1.issuperset(set2))  # False
                              # 함수가 is--- 이므로 True / False 로 반환
print(set1.union(set2))  # {0, 1, 2, 3, 4, 5, 7, 9}
                         # 정렬 X
                         # set1 합집합 set2

```