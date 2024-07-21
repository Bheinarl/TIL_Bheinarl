# 문자열에 포함된 문자들의 유형을 판별하는 Method

- `isdecimal()`
  - 문자열이 모두 숫자 문자 (0 ~ 9)로만 이루어져 있어야 True

- `isdigit()`
  - `isdecimal()`과 비슷하지만, 유니코드 숫자도 인식 ('①’ 도 숫자로 인식)

- `isnumeric()`
  - `isdigit()`과 유사하지만, 몇 가지 추가적인 유니코드 문자들을 인식
  
  - 분수, 지수, 루트 기호도 숫자로 인식

- `isdecimal()` $\subseteq$ `isdigit()` $\subseteq$ `isnumeric()`

| `isdecimal()` | `isdigit()` | `isnumeric()` | 예시 |
| :-: | :-: | :-: | :-: |
| True | True | True | "038", "੦੩੮", "０３８” |
| False | True | True | "⁰³⁸", "🄀⒊⒏", "⓪③⑧” |
| False | False | True | "⅛⅘", "ⅠⅢⅧ", "⑩⑬㊿", "壹貳參” |
| False | False | False | "abc", "38.0", "-38” |

