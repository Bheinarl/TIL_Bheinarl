# Template & URLs

[Template System](#template-system)   
[Template 상속](#template-상속)   
[HTML form](#html-form)   
[Django 변수와 URLs](#django-변수와-urls)   
[APP과 URL](#app과-url)   
[URL 이름 지정](#url-이름-지정)   
[참고](#참고)   

---

## Template System

- 데이터 **표현**을 제어하면서, **표현**과 관련된 부분을 담당

### Django Template Language  (DTL)

- Template에서 조건, 반복, 변수 등의 프로그래밍적 기능을 제공하는 시스템

### DTL Syntax

1. Variable
2. Filters
3. Tags
4. Comments

### DTL Variable

- render 함수의 세 번째 인자로 딕셔너리 데이터를 사용

- 딕셔너리 key에 해당하는 문자열이 template에서 사용 가능한 변수명이 됨

- dot ( . )을 사용하여 변수 속성에 접근할 수 있음

```html
{{ variable }}
{{ variable.attribute }}
```

### DTL Filter

- 표시할 변수를 수정할 때 사용 (변수 + ‘|’ + 필터)

- chained(연결)이 가능하며 일부 필터는 인자를 받기도 함

- 약 60개의 built-in-template filters를 제공

```html
{{ variable|filter }}
{{ name|truncatewords:30 }}
```

### DTL Tags

- 반복 또는 논리를 수행하여 제어 흐름을 만듦

- 일부 태그는 시작과 종료 태그가 필요

- 약 24개의 built-in-template tags를 제공

```html
{% tag %}
{% if %} {% endif %}
{% for item in items %} {% endfor %}
```

### DTL Comments

- DTL에서의 주석

```html
<h1> Helo, {# name #} </h1>

{% comment %}
...
{% endcomment %}
```

## Template 상속

### 기본 템플릿 구조의 한계

- 모든 템플릿에 bootstrap 적용

- 모든 템플릿에 bootstrap CDN 작성

### 템플릿 상속 Template Inheritance

- **페이지의 공통요소를 포함**하고, **하위 템플릿이 재정의할 수 있는 공간**을 정의하는 기본 ‘skeleton 템플릿’을 작성하여 상속 구조를 구축

- 파이썬의 class와 비슷한 느낌

### 상속 구조 만들기

- skeleton 역할을 하게 되는 상위 템플릿(base.html) 작성

```html
{% extends 'articles/base.html' %}

"""
이렇게 하면 html의 윗부분, 설정, 언어, head 등등이 다 생략할 수 있다.
상속처럼 꺼내다가 사용할 수 있다.
동일한 정보를 가져오는 것
"""
```

```html
{% block 블록이름 %}
...
{% endblock 블록이름 %}
```

### `'extends'` tag

- 자식(하위) 템플릿이 부모 템플릿을 확장한다는 것을 알림

- 반드시 자식 템플릿 최상단에 작성되어야 함

- 2개 이상은 불가능하다.

- `{% extends 'path' %}`

### `‘block’` tag

- 하위 템플릿에서 재정의할 수 있는 블록을 정의

- 상위 템플릿에 작성하며 하위 템플릿이 작성할 수 있는 공간을 지정

- `{% block name %}`

- `{% endblock name %}`

## HTML form

### 요청과 응답

- 데이터를 보내고 가져오기 Sending and Retrieving form data
    - HTML ‘form’ element를 통해 사용자와 애플리케이션 간의 상호작용 이해하기
    
    - HTML ‘form’은 HTTP 요청을 서버에 보내는 가장 편리한 방법

### ‘form’ element

- 사용자로부터 할당된 데이터를 서버로 전송

- 웹에서 사용자 정보를 입력하는 여러 방식(text, password, checkbox 등)을 제공

- `<form action='#' method='GET'> </form>`

### ‘action’ & ‘method’

- form의 핵심 속성 2가지

- 데이터를 어디(action)로 어떤 방식(method)으로 요청할지

### ‘action’

- 입력 데이터가 전송될 URL을 지정 (목적지)

- 만약 이 속성을 지정하지 않으면 데이터는 현재 form이 있는 페이지의 URL로 보내짐

### ‘method’

- 데이터를 어떤 방식으로 보낼 것인지 정의

- 데이터의 HTTP request methods (GET, POST)를 지정

### ‘input’ element

- 사용자의 데이터를 입력받을 수 있는 요소

- type 속성 값에 따라 다양한 유형의 입력 데이터를 받음

- 핵심 속성 - ‘name’

### ‘name’ attribute

- input의 핵심 속성

- 사용자가 입력한 데이터에 붙이는 이름(key)

- 데이터를 제출했을 때 서버는 name 속성에 성정된 값을 통해서만 사용자가 입력한 데이터에 접근할 수 있음

### Query String Parameters

- 사용자의 입력 데이터를 URL 주소에 파라미터를 통해 서버로 보내는 방법

- 문자열은 앰퍼샌드(’&’)로 연결된 key = value 쌍으로 구성되며, 기본 URL과는 물음표(’?’)로 구분됨

- 예시
    - http://host:port/path?key1=value1&key2&value2

### 사용자 입력 데이터를 받아 그대로 출력하는 서버 만들기

1. throw 로직 생성

2. catch 로직 생성
    - throw 페이지에서 요청한 사용자 입력 데이터는 request에 존재

### HTTP Request 객체

- form으로 전송한 데이터 뿐만 아니라 Django로 들어오는 모든 요청 관련 데이터가 담겨 있음

- view 함수의 첫 번째 인자로 전달됨

### request 객체에서 form 데이터 추출

```html
request.GET.get('message')
```

- `request.GET`에는 `<QueryDict: {'message':['안녕!']}>`

- `get(’message’)`
    - 딕셔너리의 get 메서드를 사용해 키의 값을 조회

### throw - catch 간 요청과 응답 순서

1. throw/ 로 요청 (web → django)

2. throw/ 문자열과 일치하는 urls.py의 path 함수 호출 (django)

3. throw view 함수 호출 (django)

4. throw view 함수가 응답 객체를 반환 (django)

5. 응답 객체 전달 (django → web)

6. 응답 객체 해석 후 화면 출력 (web)

<br>

1. throw 페이지에서 form 데이터 작성 후 제출 (form 요소의 action 속성 값으로 요청) (web)

2. catch/ 로 요청 (+ 사용자 입력 데이터와 함께) (web → django)

3. catch/ 문자열과 일치하는 urls.py의 path 함수 호출 (django)

4. catch view 함수 호출 (django)

5. catch view 함수에서 사용자가 보낸 form 데이터 추출 후 응답 객체를 반환 (django)

6. 응답 객체 전달 (django → web)

7. 응답 객체 해석 후 화면 출력 (web)

## Django 변수와 URLs

### URL dispatcher

- URL 패턴을 정의하고 해당 패턴이 일치하는 요청을 처리할 view 함수를 연결 (mapping)

### 현재 URL 관리의 문제점

- 템플릿의 많은 부분이 중복되고, URL의 일부만 변경되는 상황이라면 계속해서 비슷한 URL과 템플릿을 작성

### Variable Routing

- URL 일부에 변수를 포함시키는 것

- 변수는 view 함수의 인자로 전달할 수 있음
  

```html
<path_converter : variable_name>
```

### Path Converters

- URL 변수의 타입을 지정

- str, int 등 5가지 타입 지원

## App과 URL

### App URL mapping

- 각 앱에 URL을 정의하는 것

- 프로젝트와 각 앱이 URL을 나누어 관리를 편하게 하기 위함

### 2번째 앱 pages 생성 후 발생할 수 있는 문제

- view 함수 이름이 같거나 같은 패턴의 URL 주소를 사용하게 되는 경우

- 아래 코드와 같이 해결해 볼 수 있으나 더 좋은 방법이 필요

- URL을 각자 app에서 관리

- include를 통해서 각자의 url로 경로를 연결시켜준다.

### `include()`

- 프로젝트 내부 앱들의 URL을 참조할 수 있도록 매핑하는 함수

- URL의 일치하는 부분까지 잘라내고, 남은 문자열 부분은 후속 처리를 위해 include된 URL로 전달

- include 괄호 안에는 문자열 형태

```python
from django.urls import path, include

urlpatterns = [
	path('articles/', include('articles.urls'))
]
```

## URL 이름 지정

### URL 구조 변경에 따른 문제점

- 기존 ‘articles/’ 주소가 ‘articles/index/’로 변경됨에 따라 해당 url을 사용하는 모든 위치를 찾아가 변경해야 함

### Naming URL patterns

- URL에 이름을 지정하는 것

- path 함수의 name 인자를 정의해서 사용

```html
예시)

path('index/', views.index, name='index')
```

### URL 표기 변화

- url을 작성하는 모든 곳에서 변경

- a 태그의 href 속성 값 뿐만 아니라 form의 action 속성 등도 포함

```html
<a href="{% url 'hello' %}hello</a>
```

### ‘url’ tag

```html
{% url 'url name' arg1 arg2 %}
```

- 주어진 URL 패턴의 이름과 일치하는 절대 경로 주소를 반환

### URL 이름 지정 후 남은 문제

- articles 앱의 url 이름과 pages 앱의 url 이름이 같음

- 단순히 이름만으로는 완벽하게 분리할 수 없음

- 이름을 key로 이용

### ‘app_name’ 속성 지정

- app_name 변수 값 설정

- `path('index/', views.index, name='index')`

```python
app_name = 'articles'
urlpatterns = [
	...,
]
```

### URL tag의 최종 변화

- 마지막으로 url 태그가 사용하는 모든 곳의 표기 변경하기

```html
{% url 'app_name:path_name' %}

{% url 'articles:index' %}
```

## 참고

### 추가 템플릿 경로 지정

- 템플릿 기본 경로 외 커스텀 경로 추가하기

- 프로젝트 -> setting

```html
Templates = [
...
'DIRS' : [ 여기에 추가 ]
```

- 기본 경로에 추가 경로를 설정하는 것

### BASE_DIR

- settings에서 경로 지정을 편하게 하기 위해 최상단 지점을 지정해 둔 변수

### DTL 주의사항

- Python처럼 일부 프로그래밍 구조 (if, for 등)을 사용할 수 있지만 명칭을 그렇게 설계했을 뿐이지 **Python 코드로 실행되는 것이 아니며 Python과는 관련 없음**

- 프로그래밍적 로직이 아니라 표현을 위한 것임을 명심하기

- 프로그래밍적 로직은 되도록 view 함수에서 작성 및 처리할 것

### URL의 Trailing Slaches

- Django는 URL 끝에 ‘/’가 없다면 자동으로 붙임

- “기술적인 측면에서, ‘foo.com/bar’와 ‘foo.com/bar/’는 서로 다른 URL

- 검색 엔진 로봇이나 웹 트래픽 분석 도구에서는 이 두 주소를 서로 다른 페이지로 보기 때문

- Django는 검색 엔진이 혼동하지 않게 하기 위해 무조건 붙이는 것을 선택한 것

- 모든 프레임워크가 이와 같은 방식은 아님

- 프레임워크 각자만의 방식이 존재