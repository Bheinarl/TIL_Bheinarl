# Type Conversion

[Type Conversion](#type-conversion형변환)   
[Implicit Type Conversion](#implicit-type-conversion-암시적-형변환)   
[Explicit Type Conversion](#explicit-type-conversion-명시적-형변환)   
[컬렉션 간 형변환 정리](#컬렉션-간-형변환-정리)   

---
## Type Conversion(형변환)
- 한 데이터 타입을 다른 데이터 타입으로 변환하는 과정

- 암시적 형변환 / 명시적 형변환으로 나뉨

## Implicit Type Conversion (암시적 형변환)
- 파이썬이 자동으로 수행하는 형변환

### 예시
- 정수와 실수의 연산에서 정수가 실수로 변환됨

- Boolean과 Numeric Type에서만 가능

```python
print( 3 + 5.0 ) # 8.0

print ( True + 3) # 4

print ( True + False) # 1
```

## Explicit Type Conversion (명시적 형변환)
- 프로그래머가 직접 지정하는 형변환

- 암시적 형변환이 아닌 경우를 모두 포함

### 예시
- str -> integer : 형식에 맞는 숫자만 가능

```python
print(int('1')) # 1

#ValueErrot : invalid literal for int() with base 10: '3.5'
print(int('3.5'))

print(int(3.5))  # 3
print(float('3.5'))  # 3.5
```

- integer -> str : 모두 가능
```python
print(str(1) + '등') # 1등
```

## 컬렉션 간 형변환 정리

| |str|list|tuple|range|set|dict|
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|
|str| |O|O|X|O|X|
|list|O| |O|X|O|X|
|tuple|O|O| |X|O|O|
|range|O|O|O| |O|X|
|set|O|O|O|X| |X|
|dict|O|O (key만)|O (key만)|X|O (key만)| |