# str 

[str](#str-string)   
[문자열 표현](#문자열-표현)   
[중첩 따옴표](#중첩-따옴표)   
[Escape Sequence](#escape-sequence)   
[String Interpolation](#string-interpolation)   
[문자열의 시퀀스 특징](#문자열의-시퀀스-특징)   

---
## str (string)
- 문자열
  
- 문자들의 순서가 있는 변경 불가능한 시퀀스 자료형

## 문자열 표현
- 문자열은 단일 문자나 여러 문자의 조합으로 이루어짐
  
- 작은 따옴표 또는 큰 따옴표에 감싸서 표현

## 중첩 따옴표
- 따옴표 안에 따옴표를 표현할 경우
  
  - 작은 따옴표가 들어있는 경우에는 큰 따옴표로 문자열 생성
  
  - 큰 따옴표가 들어있는 경우에는 작은 따옴표로 문자열 생성


## Escape Sequence
- 역슬래시( backslash, `\` ) 뒤에 특정 문자가 와서 특수한 기능을 하는 문자 조합

- 파이썬의 일반적인 문법 규칙을 잠시 탈출한다는 의미
  

| 예약 문자 | 내용(의미) |
|:--------: | :-------: |
| \\n | 줄 바꿈 |
| \\t | 탭 |
| \\\\ | 백슬래시 |
| \\’ | 작은 따옴표 |
| \\" | 큰 따옴표 |

### Escape Sequence 예시
```python
print('철수야 \\'안녕\\'')
# 철수야 '안녕'

print('이 다음은 엔터\\n입니다.')

#이 다음은 엔터
#입니다
```

## String Interpolation
- 문자열 내에 변수나 표현식을 삽입하는 방법

### f-string
- 문자열에 `f` 또는 `F` 접두어를 붙이고 표현식을 `{expression}로 작성하는 문법
- 문자열에 파이썬 표현식의 값을 삽입할 수 있음

```python
bugs = 'roaches'
counts = 13
area = 'living room'

print(f'Debugging {bugs} {counts} {area}')
# Debugging reaches 13 living room
```

## 문자열의 시퀀스 특징

```python
my_str = 'hello'

# 인덱싱
print(my_Str[1]) # e

# 슬라이싱
print(my_str[2:4]) # ll

# 길이
print(len(my_str)) # 5
```
### 인덱스 (index)
- 시퀀스 내의 값들에 대한 고유한 번호로, 각 값의 위치를 식별하는 데 사용되는 문자
- 예시   

| " | h | e | l | l | o | " |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
| index | 0 | 1 | 2 | 3 | 4 |
| index | -5 | -4 | -3 | -2 | -1 |

### 슬라이싱 (slicing)
- 시퀀스의 일부분을 선택하여 추출하는 작업
- 시작 인덱스와 끝 인덱스를 지정하여 해당 범위의 값을 포함하는 새로운 시퀀스를 생성
- 예시
  ```python
  my_str = 'hello'

    #예시 1
    my_str[2:4] = ll
    #index 2부터 4 미만까지 (index 2, 3)

    #예시 2
    my_str[:3] = hel
    #index 0부터 3미만까지 (index 0, 1, 2)

    #예시 3
    my_str[3:] = lo
    #index 3부터 끝까지 (index 3, 4)

    #step을 지정하여 추출

    #예시 4
    my_str[0:5:2] = hlo
    #index 0부터 5미만까지 2개씩 (퐁당퐁당)

    #예시 5
    my_str[::-1]= olleh
    #index 처음부터 끝까지 -1개씩(음수는 거꾸로 진행)
    ```

### 문자열은 불변 (변경 불가)

```python
my_str = 'hello'

my_str[1] = 'z'
#TypeError: 'str' object does not support item assignment
```