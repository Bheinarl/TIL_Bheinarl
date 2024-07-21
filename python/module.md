# Module

[Module](#module-1)   
[Module import](#module-import)   
[Module 사용하기](#module-사용하기)    

[`as` 키워드](#as-키워드)   
[Python Standard Library](#python-standard-library-파이썬-표준-라이브러리)
[Package](#패키지)   

## Module
- 한 파일로 묶인 변수와 함수의 모음

- 특정한 기능을 하는 코드가 작성된 파이썬 파일 (`.py`)

### Module 예시
- math 내장 모듈

- 파이썬이 미리 작성해 둔 수학 관련 변수와 함수가 작성된 모듈

```python
import math

print(math.pi)  # 3.141592653589793
    
print(math.sqrt(4))  # 2.0
```

## Module import

### 모듈을 가져오는 방법
- `import`문 사용

```python
import math

print(math.sqrt(4))
```

- `from`절 사용
```python
from math import sqrt

print(sqrt(4))
```

## Module 사용하기
- `. (dot)` 연산자
  - '점의 왼쪽 객체에서 점의 오른쪽 이름을 찾아라'는 의미

```python
# 모듈명.변수명
print(math.pi)

# 모듈명.함수명
print(math.sqrt(4))
```

### Module 주의사항
- 서로 다른 모듈이 같은 이름의 함수를 제공할 경우 문제 발생

- 마지막에 `import`된 이름으로 대체됨

```python
from math import pi, sqrt # 이렇게
from my_math import sqrt  # 충돌이 날 수 있다.
```

```python
# 그래서 모듈 내 모든 요소를 한번에 import 하는 * 표기는 권장하지 않음
    
from math import *
```

## `as` 키워드
- `as` 키워드를 사용하는 별칭(alias)을 부여
  - 두 개 이상의 모듈에서 동일한 이름의 변수, 함수 클래스 등을 가져올 때 발생하는 이름 충돌 해결

```python
from math import sqrt
from my_math import sqrt as my_sqrt
  
sqrt(4)
my_sqrt(4)
```

### 사용자 정의 모듈

#### 직접 정의한 모듈 사용하기
```python
import my_math

print(my_math.add(1, 2))
```

```python
from my_math import add

print(add(1, 2))
```

## Python Standard Library 파이썬 표준 라이브러리
- 파이썬 언어와 함께 제공되는 다양한 모듈과 패키지의 모음

## 패키지
- 연관된 모듈들을 하나의 디렉토리에 모아 놓은 것

### 패키지 사용 목적
- 모듈들의 이름 공간을 구분하여 충돌을 방지

- 모듈들을 효율적으로 관리하고 재사용할 수 있도록 돕는 역할

### 패키지 사용하기
```python
from my_package.math import my_math
# my_package 폴더에 있는 math에서 my_math 추출
from my_package.statistics import tools 
# my_package 폴더에 있는 statistics에서 tools을 추출

print(my_math.add(1, 2))
# my_math에서 add 함수 사용
print(tools.mod(1, 2))
# tools에서 mod 함수 사용
```

### PSL 내부 패키지
- 설치 없이 바로 `import`하여 사용

### 외부 패키지
- `pip`를 사용하여 설치 후 `import` 필요

### pip 파이썬 패키지 관리자
- 외부 패키지들을 설치하도록 도와주는 파이썬의 패키지 관리 시스템

- PyPI(Python Package Index)에 저장된 외부 패키지들을 설치

### requests 외부 패키지 설치 및 사용 예시
```bash
$ pip install requests
```

```python
import requests


url = 'https://random-data-api.com/api/v2/users' # 랜덤 데이터 요청
response = requests.get(url).json()
# requests.get(url)에서 수집하고
#.json()에서 dict 형태로 변환

print(response)
```