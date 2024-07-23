# dict Method

[dict](#dict)
[dict Method](#dict-method-1)
[`.clear()`](#clear)
[`.get(key[,default])`](#getkeydefault)
[`.keys()`](#keys)
[`.values()`](#values)
[`.items()`](#items)
[`.pop(key[,default])`](#popkeydefault)
[`.setdefault(key[,default])`](#setdefaultkeydefault)
[`.update([other])`](#updateother)


---

## dict
- 고유한 항목(키)들의 정렬되지 않은(순서 X) 컬렉션

## dict Method

|메서드|설명|
|:-:|:-:|
|`.clear()`|dict의 모든 키 / 값 쌍을 제거|
|`.get(k)`|k에 연결된 값을 반환 (키가 없으면 None을 반환)|
|`.get(k, v)`|k에 연결된 값을 반환하거나 키가 없으면 기본 값으로 v를 반환|
|`.keys()`|dict의 키를 모은 객체를 반환|
|`.values()`|dict의 값을 모은 객체를 반환|
|`.items()`|dict의 키 / 값 쌍을 모은 객체를 반환|
|`.pop(k)`|dict에서 키 k를 제거하고 연결됐던 값을 반환 (없으면 오류)|
|`.pop(k, v)`|dict에서 키 k를 제거하고 연결됐던 값을 반환 (없으면 v를 반환)
|`.setdefault(k)`|dict에서 키 k와 연결된 값을 반환|
|`.setdefault(k, v)`|dict에서 키 k와 연결된 값을 반환<br />k가 D의 키가 아니면 값 v와 연결한 키 k를 D에 추가하고 v를 반환|
|`.update(other)`|other 내 각 키에 대해 dict에 있는 키면, dict에 있는 그 키의 값을 other에 있는 값으로 대체.<br />other에 있는 각 키에 대해 dict에 없는 키면 키 / 값 쌍을 dict에 추가|

## `.clear()`
- dict의 모든 키 / 값 쌍을 제거

```python
person = {'name': 'Alice', 'age': 25}
person.clear()
print(person)  # {}
```

## `.get(key[,default])`
- 키 연결된 값을 반환하거나 키가 없으면 **None** 혹은 **기본 값**을 반환

- 오류 발생 X

- 아래 예시에서 `person.get('country')`와 `person['country']`는 같으나, 전자는 오류가 발생하지 않고 후자는 오류가 발생

- 이 점을 이용하여 용도에 맞게 사용

```python
person = {'name': 'Alice', 'age': 25}

print(person.get('name'))  # Alice
print(person.get('country'))  # None
print(person.get('country', 'Unknown'))  # Unknown
```

## `.keys()`
- dict 키를 모은 객체를 반환

```python
person = {'name': 'Alice', 'age': 25}
print(person.keys())  # dict_keys(['name', 'age’]) 
# 키가 모아지는 데이터 형태. list와 비슷

for k in person.keys():
    print(k)

"""
name
age
"""
```

## `.values()`
- dict 값을 모은 객체를 반환

```python
person = {'name': 'Alice', 'age': 25}
print(person.values())  # dict_values(['Alice', 25])
# 값이 모아지는 데이터 형태
# list와 비슷

for v in person.values():
    print(v)
    
"""
Alice
25
"""
```

## `.items()`
- dict 키 / 값 쌍을 모은 객체를 반환

```python
person = {'name': 'Alice', 'age': 25}
    
print(person.items()) # dict_items([('name', 'Alice'), ('age', 25)])
# tuple 형태로 나온다.

for key, value in person.items():
    print(key, value)
    
    print(key)
    print(value)

"""
name Alice
age 25

name
Alice
age
25
"""
```

## `.pop(key[,default])`
- 키를 제거하고 그 키에 연결됐던 값을 반환

- 해당 키가 없으면 에러 발생 or default 값 반환

```python
person = {'name': 'Alice', 'age': 25}
    
print(person.pop('age'))  # 25
print(person)  # {'name': 'Alice'}
print(person.pop('country', None)) # None
# 'country'가 없으면 'None'을 반환

print(person.pop('country'))  # KeyError
```

## `.setdefault(key[,default])`
- 키와 연결된 값을 반환
- 키가 있다면 `.get(key[,default])`와 비슷
- 키가 없다면 default와 연결한 키를 dict에 추가하고 default를 반환

```python
person = {'name': 'Alice', 'age': 25}

print(person.setdefault('country', 'KOREA'))  # KOREA
print(person)  # {'name': 'Alice', 'age': 25, 'country': 'KOREA'}
# 'country' 키가 없으니 {'country' : 'KOREA'} 추가
```

## `.update([other])`
- other가 제공하는 키 / 값 쌍으로 dict를 갱신

- 중복된 키는 존재할 수 없으므로 기존 키는 덮어씀

```python
person = {'name': 'Alice', 'age': 25}
other_person = {'name': 'Jane', 'gender': 'Female'}

person.update(other_person)
print(person)  # {'name': 'Jane', 'age': 25, 'gender': 'Female'}
# 'name'이 겹처서 'Alice' -> 'Jane' 으로 갱신
# 'gender'는 없어서 새로 추가
     

person.update(age=50)
print(person)  # {'name': 'Jane', 'age': 50, 'gender': 'Female'}
# 'age'가 겹쳐서 25 -> 50 으로 갱신

person.update(country='KOREA')
print(person)  # {'name': 'Jane', 'age': 50, 'gender': 'Female', 'country': 'KOREA'}
# 'country'가 없어서 {'country' : 'KOREA'} 추가
```

### 다양한 dict 메서드
자세한 내용은 [파이썬 자습서 dict Method 링크](https://docs.python.org/3/library/stdtypes.html#dict)에서 참고