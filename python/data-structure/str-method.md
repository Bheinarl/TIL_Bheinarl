# str Method

[문자열 조회 탐색 및 검증 Method](#문자열-조회--탐색-및-검증-method)   
[`.find(x)`](#findx)   
[`.index(x)`](#indexx)   
[`.isupper(x)` / `.islower(x)`](#isupperx--islowerx)   
[`.isalpha()`](#isalpha)   

[문자열 조작 Method](#문자열-조작-method-새-문자열-반환)   
[`.replace(old, new[,count]`](#replaceold-newcount)   
[`.strip([chars])`](#stripchars)   
[`separator.join(iterable)`](#separatorjoiniterable)   


[기타 문자열 조작 메서드](#기타-문자열-조작-메서드)   

---

## str Method 문자열의 Method
## 문자열 조회 / 탐색 및 검증 Method
| 메서드 | 설명 |
|:-:|:-:|
| `str.find(x)` | x의 첫 번째 위치를 반환. <br />없으면 -1을 반환 |
| `str.index(x)` | x의 첫 번째 위치를 반환. <br />없으면 오류 발생 |
| `str.isupper()` | 대문자 여부 |
| `str.islower()` | 소문자 여부 |
| `str.isalpha()` | 알파벳 문자 여부 <br /> 단순 알파벳이 아닌 유니코드 상 Letter <br />(한국어도 포함)

## `.find(x)`
- x의 첫 번째 위치를 반환

- 없으면 -1을 반환

```python
text = 'banana'

print(text.find('a')) # 1
print(text.find('z')) # -1
```

## `.index(x)`
- x의 첫 번째 위치를 반환

- 없으면 오류 발생

```python
text = 'banana'

print(text.index('a'))  # 1
print(text.index('z'))  # ValueError: substring not found
```

## `.isupper(x)` / `.islower(x)`
- 문자열이 모두 대문자 / 소문자로 이루어져 있는지 확인

```python
string1 = 'HELLO'
string2 = 'Hello'
string3 = 'hello'
print(string1.isupper()) # True
print(string2.isupper()) # False
print(string3.isupper()) # False
print(string1.islower()) # False
print(string2.islower()) # False
print(string3.islower()) # True
```

## `.isalpha()`
- 문자열이 알파벳으로만 이루어져 있는지 확인

```python
string1 = 'Hello'
string2 = '123'
string3 = 'Hello123'
print(string1.isalpha()) # True
print(string2.isalpha()) # False
print(string3.isalpha()) # False
```

## 문자열 조작 Method (새 문자열 반환)

| 메서드 | 설명 |
| :-: | :-: |
| `.replace(old, new[,count])` | 바꿀 대상 글자를 새로운 글자로 바꿔서 반환 |
| `.strip([chars])` | 공백이나 특정 문자를 제거 |
| `.split(sep = None, maxsplit=-1)` | 공백이나 특정 문자를 기분으로 분리 |
| `separator.join(iterable)` | 구분자로 iterable의 문자열을 연결한 문자열을 반환 |
| `.capitalize()` | 가장 첫 번째 글자를 대문자로 변경 |
| `.title()` | 문자열 내 띄어쓰기 기분으로 각 단어의 첫 글자는 대문자로, 나머지는 소문자로 변환 |
| `.upper()` | 모두 대문자로 변경 |
| `.lower()` | 모두 소문자로 변경 |
| `.swapcase()` | 대 ↔ 소문자 서로 변경 |

## `.replace(old, new[,count])`
- 바꿀 대상 글자를 새로운 글자로 바꿔서 변환

```python
text = 'Hello, world!'
new_text = text.replace('world', 'Python')

print(new_text) # Hello, Python!
```

<br />

```python
text = 'Hello, world! world world'
new_text = text.replace('world', 'Python')

print(new_text) # Hello, Python! Python Python
```

<br />

```python
text = 'Hello, world! world world'
new_text = text.replace('world', 'Python', 2)

print(new_text) # Hello, Python! Python world
```

## `.strip([chars])`
- 공백이나 특정 문자를 제거

```python
text = '   Hello, world!   '
new_text = text.strip()
print(new_text) # 'Hello, world!'
```

## `.split(sep = None, maxsplit=-1)`
- 지정한 문자를 구분자로 문자열을 분리하여 문자열의 리스트로 반환

```python
text = 'Hello, world!'
words = text.split(',')  # ','를 기준으로 분리
print(words) # ['Hello', ' world!'] 
# ','를 기준으로 분리하였기 때문에 world 앞에 공백도 포함
```

<br />

```python
text = 'Hello, world!'
words = text.split()  # ' '(띄어쓰기)를 기준으로 분리
print(words) # ['Hello,', 'world!'] 
```

## `separator.join(iterable)`
- 구분자로 iterable의 문자열을 연결한 문자열을 반환

```python
words = ['Hello', 'world!']
text = '-'.join(words)
print(text) # 'Hello-world!'
```

## 기타 문자열 조작 메서드
```python
# capitalize(), title(), upper(), lower(), swapcase()

text = 'heLLo, woRld!'
new_text1 = text.capitalize()
new_text2 = text.title()
new_text3 = text.upper()
new_text4 = text.lower()
new_text5 = text.swapcase()

print(new_text1) # Hello, world! 
# 맨 앞글자만 대문자로 변환
print(new_text2) # Hello, World!
# 맨 앞글자는 대문자로, 나머지는 소문자로 변환
print(new_text3) # HELLO, WORLD!
print(new_text4) # hello, world!
print(new_text5) # HEllo, WOrLD!
```

### 메서드 이어서 사용하기
- 앞 쪽의 반환 값이 존재하고 앞뒤의 데이터 타입이 맞으면, 모든 메서드는 이어서 사용 가능

```python
text = 'heLLo, woRld!'

new_text = text.swapcase().replace('l', 'z')

print(new_text) # HEzzO, WOrLD!

# HEllO, WOrLD! -> HEzzO, WOrLD!
```