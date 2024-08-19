# 웹 스타일링

[CSS](#css)   
[CSS Selectors](#css-selectors)   
[명시도](#명시도)   
[상속](#상속)   

---
## CSS
### CSS Cascading Style Sheet
- 웹 페이지의 **디자인**과 **레이아웃**을 구성하는 언어

### CSS 구문

```html
h1 {
	color: red;
	font-size: 30px;
}
```

- 선택자 - h1 : 속성을 설정하는 대상

- 선언 - { } : 속성을 설정

- 속성 - color, font-size

- 값 - red, 30px

> `;` : 문장의 종료를 의미

### CSS 적용 방법

1. 인라인(Inline) 스타일

2. 내부(Internal) 스타일 시트

3. 외부(External) 스타일 시트

### 인라인(Inline) 스타일

- HTML 요소 안에 style 속성 값으로 작성

- 점점 쌓일수록 너무 많아지고 찾기 어려워지기 때문에 잘 권장하지 않는다.

### 내부(Internal) 스타일 시트

- head 태그 안에 style 태그에 작성

### 외부(External) 스타일 시트

- 별도 CSS 파일 생성 후 HTML link 태그를 사용해 불러오기

## CSS Selectors

### CSS Selectors

- HTML 요소를 선택하여 스타일을 적용할 수 있도록 하는 선택자

### CSS Selectors 종류

- 기본 선택자
    - 전체 선택자 (*)
        - HTML 모든 요소를 선택
    
    - 요소(tag) 선택자
        - 지정한 모든 태그를 선택
    
    - 클래스(class) 선택자 (’ . ‘ (dot))
        - 주어진 클래스 속성을 가진 모든 요소를 선택
        
        - 주로 많이 사용
    
    - 아이디(id) 선택자 (’#’)
        - 주어진 아이디 속성을 가진 요소 선택
        
        - 문서에서 주어진 아이디를 가진 요소가 하나만 있어야 함
    
    - 속성(attr) 선택자
    
    - …

- 결합자(Combinators)
    - 자손 결합자 (” “ (space) )
        - 첫 번째 요소의 자손 요소들 선택
        
        - 예) p span은 <p> 안에 있는 모든 <span>를 선택 (하위 레벨 상관 없이)
    
    - 자식 결합자 (”>”)
        - 첫 번쨰 요소의 직계 자식만 선택
        
        - 예) ul < li은 <ul>안에 있는 모든 <li>를 선택 (한 단계 아래 자식들만)

## 명시도

### Specificity 명시도

- 결과적으로 요소에 적용할 CSS 선언을 결정하기 위한 알고리즘

- CSS Selector에 가중치를 계산하여 어떤 스타일을 적용할지 결정

- 동일한 요소를 가리키는 2개 이상의 CSS 규칙이 있는 경우 가장 높은 명시도를 가진 Selector가 승리하여 스타일이 적용됨

### CSS Cascading Style Sheet

- 웹 페이지의 디자인과 레이아웃을 구성하는 언어

### Cascade (계단식)

- 한 요소에 동일한 가중치를 가진 선택자가 적용될 때 CSS에서 마지막에 나오는 선언이 사용됨

### 명시도가 높은 순

1. Importance
    - !important

2. Inline 스타일

3. 선택자
    - id 선택자 > class 선택자 > 요소 선택자

4. 소스 코드 선언 순서

> 선택자는 주로 class 선택자만 이용.   
> 
> why? 여러 선택자를 쓰면 계속 우선순위를 고려해야 함.   
> 
> 하나만 써서 선택자 우선순위에 대한 생각을 버릴 수 있음.   
> 
> id 선택자는 의미가 부여되어 있어서 선택자를 하나만 사용한다.   


### !important

- 다른 우선순위 규칙보다 우선하여 적용하는 키워드

- **Cascade의 구조를 무시하고 강제로 스타일을 적용하는 방식이므로 사용을 권장하지 않음**

## 상속

### CSS 상속

- 기본적으로 CSS는 상속을 통해 부모 요소의 속성을 자식에게 상속해 재사용성을 높임

### CSS 속성 2가지 분류

- 상속되는 속성
    - Text 관련 요소 (font, color, text-align)
    
    - opacity
    
    - visibility
    
    - …

- 상속되지 않는 속성
    - Box model  관련 요소 (width, height, border, box-sizing … )
    
    - position 관련 요소 (position, top/right/bottom/left, z-index …)
    
    - …

### CSS 상속 여부 확인

- MDN의 각 속성별 문서 하단에서 상속 여부를 확인 가능