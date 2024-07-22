# List Method

[리스트 값 추가 및 삭제 메서드](#리스트-값-추가-및-삭제-메서드)   
[`.append(x)`](#appendx)   
[`.extend(iterable)`](#extenditerable)   
[`.insert(i, x)`](#inserti-x)   
[`.remove(x)`](#removex)   
[`.pop(i)`](#popi)   
[`.clear()`](#clear)   

[리스트 탐색 및 정렬 메서드](#리스트-탐색-및-정렬-메서드)   
[`.index(x)`](#indexx)   
[`.count(x)`](#countx)   
[`.reverse()`](#reverse)   
[`.sort()`](#sort)   

---

## 리스트 값 추가 및 삭제 메서드

| 메서드 | 설명 |
|:-:|:-:|
| `.append(x)` | 리스트 마지막에 항목 x를 추가 |
| `.extend(iterable)` | iterable m의 모든 항목들을 리스트 끝에 추가<br />(+= 와 같은 기능) |
| `.insert(i, x)` | 리스트 인덱스 i에 항목 x를 삽입 |
| `.remove(x)` | 리스트 가장 왼쪽에 있는 항목(첫 번째) x를 제거<br />항목이 존재하지 않을 경우 ValueError  |
| `.pop()` | 리스트 가장 오른쪽에 있는 항목(마지막)을 반환 후 제거 |
| `.pop(i)` | 리스트의 인덱스 i에 있는 항목을 반환 후 제거 |
| `.clear()` | 리스트의 모든 항목 삭제 |

## `.append(x)`
- 리스트 마지막에 항목 x를 추가

```python
my_list = [1, 2, 3]
my_list.append(4)
print(mylist) # [1, 2, 3, 4]
```

<br />

```python
my_list = [1, 2, 3]
print(mylist.append(4)) # None
```

## `.extend(iterable)`
- 리스트에 다른 반복 가능한 객체의 모든 항목을 추가

```python
my_list = [1, 2, 3]
my_list.extend([4, 5, 6])
print(my_list) # [1, 2, 3, 4, 5, 6]
my_list.extend(5)
print(my_list) # Error / # 5는 int로 iterable 하지 않아 불가능
```

<br />

```python
my_list = [1, 2, 3]
my_list.extend([4], [5])
print(my_list) # Error / # extend는 한 개의 값만 추가 가능
```

## `.insert(i, x)`
- 리스트의 지정한 인덱스 i 위치에 항목 x를 삽입

```python
my_list = [1, 2, 3]
my_list.insert(1, 5)
print(my_list) # [1, 5, 2, 3]
```

## `.remove(x)`
- 리스트에서 첫 번째로 일치하는 항목을 삭제

```python
my_list = [1, 2, 3]
my_list.remove(2)
print(my_list)  # [1, 3]
```

## `.pop(i)`
- 리스트에서 지정한 인덱스의 항목을 **제거**하고 **반환**

- 제거하면 리스트의 길이는 감소함

- `i`를 작성하지 않을 경우, 마지막 항목을 제거

```python
my_list = [1, 2, 3, 4, 5]
    
item1 = my_list.pop()
item2 = my_list.pop(0)
    
print(item1) # 5
print(item2) # 1
print(my_list) # [2, 3, 4]
```

## `.clear()`
- 리스트의 모든 항목을 삭제

```python
my_list = [1, 2, 3]
my_list.clear()
print(my_list) # []
```

## 리스트 탐색 및 정렬 메서드

| 메서드 | 설명 |
|:-:|:-:|
| `.index(x)` | 리스트에 있는 항목 중 가장 왼쪽에 있는 항목 x의 인덱스를 반환 |
| `.count(x)` | 리스트에서 항목 x의 개수를 반환 |
| `.reverse()` | 리스트의 순서를 역순으로 변경 (정렬 X) |
| `.sort()` | 리스트를 정렬 (매개변수 이용가능) |

## `.index(x)`
- 리스트에서 첫 번째로 일치하는 항목의 인덱스를 반환

```python
my_list = [1, 2, 3]
index = my_list.index(2)
print(index)  # 1
```

## `.count(x)`
- 리스트에서 항목 x가 등장하는 횟수를 반환

```python
my_list = [1, 2, 2, 3, 3, 3]
count = my_list.count(3)
print(count)  # 3
```

## `.reverse()`
- 리스트의 순서를 역순으로 변경 (정렬 X)

```python
my_list = [1, 3, 2, 8, 1, 9]
my_list.reverse()

print(my_list.reverse()) # None 
# 원본을 역순으로 변경하였기 때문에 반환 값은 없다.

print(my_list)  # [9, 1, 8, 2, 3, 1]
```

## `.sort()`
- 원본 리스트를 오름차순으로 정렬

```python
my_list = [3, 2, 1]
my_list.sort()
print(my_list)  # [1, 2, 3]

# 내림차순
my_list.sort(reverse=True)
print(my_list)  # [3, 2, 1]
```