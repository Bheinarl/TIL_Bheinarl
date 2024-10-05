# Authentication System
   
[Cookie](#cookie--session)   
[Session](#세션-session)   
[Authentication System](#authentication-system)   
[Custom User Model](#custom-user-model)   
[Login](#login)   
[Logout](#logout)   
[Template with Authenticatino Data](#template-with-authentication-data)   
[회원 가입](#회원-가입)   
[회원 탈퇴](#회원-탈퇴)   
[회원 정보 수정](#회원-정보-수정)   
[비밀번호 변경](#비밀번호-변경)   
[인증된 사용자에 대한 접근 제한](#인증된-사용자에-대한-접근-제한)   
[참고](#참고)   

---

## Cookie & Session

### HTTP

- 우리가 웹 페이지를 둘러볼 때 우리는 서버와 서로 연결되어 있는 상태가 아니다.

- HTML 문서와 같은 리소스들을 가져올 수 있도록 해주는 규약

- 웹 WWW에서 이루어지는 모든 데이터 교환의 기초

### HTTP 특징

1. 비 연결 지향 (Connectionless)
    - 서버는 요청에 대한 응답을 보낸 후 연결을 끊음

2. 무상태(Stateless)
    - 연결을 끊는 순간 클라이언트와 서버 간의 통신이 끝나며 상태 정보가 유지되지 않음

### 쿠키 Cookie

- 서버가 사용자의 웹 브라우저에 전송하는 작은 데이터 조각

- 서버가 제공하여 클라이언트 측에서 저장되는 작은 데이터 파일

- 사용자 인증, 추적, 상태 유지 등에 사용되는 데이터 저장 방식

### 쿠키 동작 예시

1. 브라우저가 웹 서버에 웹 페이지를 요청

2. 웹 서버는 요청된 페이지와 함께 쿠키를 포함한 응답을 브라우저에게 전송

3. 브라우저는 받은 쿠키를 저장소에 저장
    - 쿠키의 속성(만료 시간, 도메인, 주소 등)도 함께 저장됨

4. 이후 브라우저가 같은 웹 서버에 웹 페이지를 요청할 때, 저장된 쿠키 중 해당 요청에 적용 가능한 쿠키를 포함하여 함께 전송

5. 웹 서버는 받은 쿠키 정보를 확인하고, 필요에 따라 사용자 식별, 세션 관리 등을 수행

6. 웹 서버는 요청에 대한 응답을 보내며, 필요한 경우 새로운 쿠키를 설정하거나 기존 쿠키를 수정할 수 있음

### 쿠키의 작동 원리와 활용

1. 쿠키 저장 방식
    - 브라우저(클라이언트)는 쿠키는 KEY-VALUE의 데이터 형식으로 저장
    
    - 쿠키에는 이름, 값 외에도 만료 시간, 도메인, 경로 등의 추가 속성이 포함됨

2. 쿠키 전송 과정
    - 서버는 HTTP 응답 헤더의 Set-Cookie 필드를 통해 클라이언트에게 쿠키를 전송
    
    - 브라우저는 받은 쿠키를 저장해 두었다가, 동일한 서버에 재요청 시 HTTP 요청
    
    - Header의 Cookie 필드에 저장된 쿠키를 함께 전송

3. 쿠키의 주요 용도
    - 두 요청이 동일한 브라우저에서 들어왔는지 아닌지를 판단할 때 주로 사용됨
    
    - 이를 이용해 사용자의 로그인 상태를 유지할 수 있음
    
    - 상태가 없는(Stateless) HTTP 프로토콜에서 상태 정보를 기억시켜 주는 역할
    
    - 서버에게 “나 로그인된 사용자야!” 라는 인증 정보가 담긴 쿠키를 매 요청마다 계속 보내는 것

### 쿠키 사용 목적

1. 세션 관리(Session Management)
    - 로그인, 아이디 자동완성, 공지 하루 안보기, 팝업 체크, 장바구니 등의 정보 관리

2. 개인화 (Personalizaion)
    - 사용자 선호 설정 (언어 설정, 테마 등) 저장

3. 트래킹 (Tracking)
    - 사용자 행동을 기록 및 분석

## 세션 Session

### 세션 Session

- 서버 측에서 생성되어 클라이언트와 서버 간의 상태를 유지

- 상태 정보를 저장하는 데이터 저장 방식

- 쿠키에 세션 데이터를 저장하여 매 요청시마다 세션 데이터를 함께 보냄

### 세션 작동 원리

1. 클라이언트가 로그인 요청 후 인증에 성공하면 서버가 session 데이터를 생성 후 저장

2. 생성된 session 데이터에 인증할 수 있는 session id를 발급

3. 발급한 session id를 클라이언트에게 응답 (데이터는 서버에 저장, 열쇠만 주는 것)

4. 클라이언트는 응답 받은 session id를 쿠키에 저장

5. 클라이언트가 다시 동일한 서버에 접속하면 요청과 함께 쿠키(session id가 저장된)를 서버에 전달

6. 쿠키는 요청 때마다 서버에 함께 전송되므로 서버에서 session id를 확인해 로그인되어있다는 것을 계속해서 확인하도록 함

### 세션 과정

- 서버 측에서는 세션 데이터를 생성 후 저장하고 이 데이터에 접근할 수 있는 세션 ID를 생성

- 이 ID를 클라이언트 측으로 전달하고, 클라이언트는 쿠키에 이 ID를 저장

- 이후 클라이언트가 같은 서버에 재요청 시마다 저장해두었던 쿠키도 요청과 함께 전송

- 예를 들어 로그인 상태 유지를 위해 로그인 되어있다는 사실을 입증하는 데이터를 매 요청마다 계속해서 보내는 것

### 쿠키와 세션의 목적

- 클라이언트와 서버 간의 상태 정보를 유지하고 사용자를 식별하기 위해 사용

## Django Authentication System

### Django Authentication System

- 사용자 인증과 관련된 기능을 모아 놓은 시스템

### Authentication 인증

- 사용자가 자신이 누구인지 확인하는 것

- 신원 확인

### 사전 준비

- 두 번째 app **accounts** 생성 및 등록

- `auth`와 관련한 경로나 키워드들을 django 내부적으로 accounts라는 이름으로 사용하고 있기 때문에 되도록 ‘accounts’로 지정하는 것을 권장
    
    ![authentication인증_1](./images/authentication인증_1.png)
    
    ![authentication인증_2](./images/authentication인증_2.png)
    

## Custom User Model

### 기본 User Model의 한계

- 우리는 지금까지 별도의 User 클래스 정의 없이 내장된 auth 앱에 작성된 User 클래스를 사용했음

- Django의 기본 User 모델은 username, password 등 제공되는 필드가 매우 제한적

- 추가적인 사용자 정보 (예 : 생년월일, 주소, 나이 등)과 필요하다면 이를 위해 기본 User Model을 변경하기 어려움
    - 별도의 설정 없이 사용할 수 있어 간편하지만, 개발자가 직접 수정하기 어려움

### 내장된 auth 앱

![내장된_auth_앱](./images/내장된_auth_앱.png)

### User Model 대체의 필요성

- 프로젝트의 특정 요구사항에 맞춰 사용자 모델을 확장할 수 있음

- 예를 들어 이메일을 username으로 사용하거나, 다른 추가 필드를 포함시킬 수 있음

### Custom User Model로 대체하기

- AbstractUser 클래스를 상속받는 커스텀 User 클래스 작성

- 기존 User 클래스도 AbstractUser를 상속받기 때문에 **커스텀 User 클래스도 기존 User 클래스와 완전히 같은 모습을 가지게 됨**
    
    ![custom_user_model_대체1](./images/custom_user_model_대체1.png)
    
- Django 프로젝트에서 사용하는 기본 User 모델을 우리가 작성한 User 모델로 사용할 수 있도록 AUTH_USER_MODEL 값을 변경
    - 수정 전 기본 값은 ‘auth.User’
        
    ![custom_user_model_대체2](./images/custom_user_model_대체2.png)
        
- admin site에 대체한 User 모델 등록
    - 기본 User 모델이 아니기 때문에 등록하지 않으면 admin 페이지에 출력되지 않기 때문

### AUTH_USER_MODEL

- Django 프로젝트의 User를 나타내는 데 사용하는 모델을 지정하는 속성

- 프로젝트 중간에 AUTH_USER_MODEL을 변경할 수 없음

- 이미 프로젝트가 진행되고 있을 경우 데이터베이스 초기화 후 진행

### 사용하는 User 테이블의 변화

![사용하는_user_테이블의_변화](./images/사용하는_user_테이블의_변화.png)

### 프로젝트를 시작하며 반드시 User 모델 대체

- Django는 새 프로젝트를 시작하는 경우 비록 기본 User 모델이 충분하더라도 커스텀 User 모델을 설정하는 것을 **강력하게 권장**하고 있음

- 커스텀 User 모델은 **기본 User 모델과 동일하게 작동**(1)하면서도 **필요한 경우 나중에 맞춤 설정**(2)할 수 있기 때문

- 단, User 모델 대체 작업은 프로젝트의 모든 migrations 혹은 첫 migrate를 실행하기 전에 이 작업을 마쳐야 함

## Login

### Login

- 로그인은 Session을 Create하는 과정

### AuthenticationForm()

- 로그인 인증에 사용할 데이터를 입력 받는 built-in form

### 로그인 페이지 작성

![login_1](./images/login_1.png)

![login_2](./images/login_2.png)

![login_3](./images/login_3.png)

![login_4](./images/login_4.png)

### 로그인 로직 작성

![로그인_로직_작성](./images/로그인_로직_작성.png)

### `login(request, user)`

- AuthenticatinoForm을 통해 인증된 사용자를 로그인하는 함수
    - 로그인 → 세션 데이터 생성

### `get_user()`

- AuthenticationForm의 인스턴스 메서드

- 유효성 검사를 통과했을 경우 로그인한 사용자 객체를 반환

### 세션 데이터 확인

1. 로그인 후 발급받은 세션 확인
    - django_session 테이블에서 확인
        
        ![세션_데이터_확인1](./images/세션_데이터_확인1.png)
        
2. 브라우저에서 확인
    - 개발자도구 - Application - Cookies
        
        ![세션_데이터_확인2](./images/세션_데이터_확인2.png)
        

### 로그인 링크 작성

- 메인 페이지에 로그인 페이지로 갈 수 있는 링크 작성
    
    ![로그인_링크_작성](./images/로그인_링크_작성.png)
    

## Logout

### Logout

- 로그아웃은 Session을 Delete하는 과정

### Logout(request)

1. DB에서 현재 요청에 대한 Session Data를 삭제

2. 클라이언트의 쿠키에서도 Session ID를 삭제

### 로그아웃 로직 작성

![로그아웃_로직_작성1](./images/로그아웃_로직_작성1.png)

![로그아웃_로직_작성2](./images/로그아웃_로직_작성2.png)


![로그아웃_로직_작성3](./images/로그아웃_로직_작성3.png)


- 로그아웃 진행 및 세션 데이터 삭제 확인
    
    ![로그아웃_로직_작성4](./images/로그아웃_로직_작성4.png)
    

## Template with Authentication Data

### Template with Authentication Data

- 템플릿에서 인증 관련 데이터를 출력하는 방법

### 현재 로그인 되어있는 유저 정보 출력하기

- user라는 context 데이터를 사용할수 있는 이유
    - django가 미리 준비한 context 데이터가 존재하기 때문
    
    - context processors

### Context Processors

- 템플릿이 렌더링될 때 호출 가능한 컨텍스트 데이터 목록

- 작성된 컨텍스트 데이터는 기본적으로 템플릿에서 사용 가능한 변수로 포함됨

- Django에서 자주 사용하는 데이터 목록을 미리 템플릿에 로드해 둔 것

![context_processors1](./images/context_processors1.png)

## 회원 가입

### 회원 가입

- User 객체를 Create하는 과정

`UserCreationForm()`

- 회원 가입시 사용자 입력 데이터를 받는 built-in ModelForm

### 회원 가입 페이지 작성

![회원가입_페이지_작성1](./images/회원가입_페이지_작성1.png)

![회원가입_페이지_작성2](./images/회원가입_페이지_작성2.png)

![회원가입_페이지_작성3](./images/회원가입_페이지_작성3.png)

- 회원 가입 페이지 확인
    
    ![회원가입_페이지_작성4](./images/회원가입_페이지_작성4.png)
    

### 회원 가입 로직 작성

![회원가입_로직_작성1](./images/회원가입_로직_작성1.png)

### 회원 가입 로직 에러

- 회원 가입 시도 후 에러 페이지 확인

- Manager isn’t available; ‘auth.User’ has been swapped for ‘accounts.User’

![회원가입_로직_에러1](./images/회원가입_로직_에러1.png)

- 회원 가입에 사용하는 UserCreationForm이 대체한 커스텀 유저 모델이 아닌 과거 Django의 기본 유저 모델로 인해 작성된 클래스이기 때문

![회원가입_로직_에러2](./images/회원가입_로직_에러1.png)

### 커스텀 유저 모델을 사용하려면 다시 작성해야 하는 Form

- UserCreawtionForm

- UserChangeForm

- 두 Form 모두 `class Meta : model = User` 가 작성된 Form이기 때문에 재작성 필요

### UserCreationForm과 UserChangeForm 커스텀

- Custom User Model을 사용할 수 있도록 상속 후 일부분만 재작성

![usercreationform과_userchangeform_커스텀1](./images/usercreationform과_userchangeform_커스텀1.png)

### `get_user_model()`

- “현재 프로젝트에서 활성화된 사용자 모델(active user model)”을 반환하는 함수

### User 모델을 직접 참조하지 않는 이유

- `get_user_model()`을 사용해 User 모델을 참조하면 커스텀 User 모델을 자동으로 반환해주기 때문

- Django는 필수적으로 User 클래스를 직접 참조하는 대신 `get_user_model()` 을 사용해 참조해야 한다고 강조하고 있음

### 회원 가입 로직 완성

- CustomUserCreationForm으로 변경

![회원가입_로직_완성1](./images/회원가입_로직_완성1.png)

## 회원 탈퇴

### 회원 탈퇴

- User 객체를 Delete하는 과정

### 회원 탈퇴 로직 작성

![회원_탈퇴_로직_작성1](./images/회원_탈퇴_로직_작성1.png)

![회원_탈퇴_로직_작성2](./images/회원_탈퇴_로직_작성2.png)

![회원_탈퇴_로직_작성3](./images/회원_탈퇴_로직_작성3.png)

- 회원 탈퇴 진행
    
    ![회원_탈퇴_로직_작성4](./images/회원_탈퇴_로직_작성4.png)
    

## 회원 정보 수정

### 회원 정보 수정

- User 객체를 Update하는 과정

### `UserChangeForm()`

- 회원 정보 수정 시 사용자 입력 데이터를 받는 built-in **ModelForm**

### 회원 정보 수정 페이지 작성

![회원_정보_수정_페이지_작성1](./images/회원_정보_수정_페이지_작성1.png)

![회원_정보_수정_페이지_작성2](./images/회원_정보_수정_페이지_작성2.png)

![회원_정보_수정_페이지_작성3](./images/회원_정보_수정_페이지_작성3.png)

![회원_정보_수정_페이지_작성4](./images/회원_정보_수정_페이지_작성4.png)

![회원_정보_수정_페이지_작성5](./images/회원_정보_수정_페이지_작성5.png)

- 회원 정보 수정 페이지 확인

![회원_정보_수정_페이지_작성6](./images/회원_정보_수정_페이지_작성6.png)

### UserChangeForm 사용 시 문제점

- User 모델의 모든 정보들(fields)까지 모두 출력됨

- 일반 사용자들이 접근해서는 안되는 정보는 출력하지 않도록 해야 함

- CustomUserChangeForm에서 출력 필드를 다시 조정하기

### CustomUserChangeForm 출력 필드 재정의

- User Model의 필드 목록 확인

![customuserchangeform_출력_필드_재정의1](./images/customuserchangeform_출력_필드_재정의1.png)

- 회원 정보 수정 페이지 확인

![customuserchangeform_출력_필드_재정의2](./images/customuserchangeform_출력_필드_재정의2.png)

### 회원 정보 수정 로직 완성

![회원_정보_수정_로직_완성1](./images/회원_정보_수정_로직_완성1.png)

## 비밀번호 변경

### 비밀번호 변경

- 인증된 사용자의 Session 데이터를 Update하는 과정

### `PasswordChangeForm()`

- 비밀번호 변경 시 사용자 입력 데이터를 받는 built-in **Form**

### 비밀번호 변경 페이지 작성

- Django는 비밀번호 변경 페이지를 회원 정보 수정 form 하단에서 별도 주소로 안내

- /user_pk/password/

![비밀번호_변경_페이지_작성1](./images/비밀번호_변경_페이지_작성1.png)

![비밀번호_변경_페이지_작성2](./images/비밀번호_변경_페이지_작성2.png)

![비밀번호_변경_페이지_작성3](./images/비밀번호_변경_페이지_작성3.png)

![비밀번호_변경_페이지_작성4](./images/비밀번호_변경_페이지_작성4.png)

- 비밀번호 변경 페이지 확인

![비밀번호_변경_페이지_작성5](./images/비밀번호_변경_페이지_작성5.png)

### 비밀번호 변경 로직 완성

![비밀번호_변경_로직_완성1](./images/비밀번호_변경_로직_완성1.png)

### 암호 변경 시 세션 무효화

- 비밀번호가 변경되면 기존 세션과의 회원 인증 정보가 일치하지 않게 되어버려 로그인 상태가 유지되지 못하고 로그아웃 처리됨

- 비밀번호가 변경되면서 기존 세션과의 회원 인증 정보가 일치하지 않기 때문

### `update_session_auth_hash(request, user)`

- 암호 변경 시 세션 무효화를 막아주는 함수

- 암호가 변경되면 새로운 password의 Session Data로 기존 session을 자동으로 갱신

### update_session_auth_hash 적용

![update_session_auth_hash_적용1](./images/update_session_auth_hash_적용1.png)

## 인증된 사용자에 대한 접근 제한

### 로그인 사용자에 대해 접근을 제한하는 2가지 방법

1. `is_authenticated` 속성

2. `login_required` 데코레이터

### `is_authenticated`

- 사용자가 인증되었는지 여부를 알 수 있는 User Model의 속성

- 모든 User 인스턴스에 대해 항상 True인 읽기 전용 속성

- 비인증 사용자에 대해서는 항상 False

### `is_authenticated` 적용하기

- 로그인과 비로그인 상태에서 화면에 출력되는 링크를 다르게 설정하기

![is_authenticated_적용하기1](./images/is_authenticated_적용하기1.png)

- 인증된 사용자라면 로그인 / 회원가입 로직을 수행할 수 없도록 하기

![is_authenticated_적용하기2](./images/is_authenticated_적용하기2.png)

### `login_required`

- 인증된 사용자에 대해서만 view 함수를 실행시키는 데코레이터

- 비인증 사용자의 경우 /accounts/login/ 주소로 redirect 시킴

### `login_required` 적용하기

- 인증된 사용자만 게시글을 작성 / 수정 / 삭제 할 수 있도록 수정

![login_required_적용하기1](./images/login_required_적용하기1.png)

- 인증된 사용자만 로그아웃 / 탈퇴 / 수정 / 비밀번호 변경할 수 있도록 수정

![login_required_적용하기2](./images/login_required_적용하기2.png)


## 참고

### 쿠키 종류별 수명

1. Session Cookie
    - 현재 세션(Current Session)이 종료되면 삭제됨
    
    - 브라우저 종료와 함께 세션이 삭제됨

2. Persistent Cookies
    - Expires 속성에 지정된 날짜 혹은 Max-Age 속성에 지정된 기간이 지나면 삭제됨

### 쿠키의 보안 장치

- 제한된 정보
    - 쿠키에는 보통 중요하지 않은 정보만 저장.
    
    - 사용자 ID나 세션 번호 같은 것

- 암호화
    - 중요한 정보는 서버에서 암호화해서 쿠키에 저장

- 만료 시간
    - 쿠키에는 만료 시간을 설정
    
    - 시간이 지나면 자동으로 삭제

- 도메인 제한
    - 쿠키는 특정 웹사이트에서만 사용할 수 있도록 설정할 수 있음

### 쿠키와 개인정보 보호

- 많은 국가에서 쿠키 사용에 대한 사용자 동의를 요구하는 법규를 시행

- 웹사이트는 쿠키 정책을 명시하고, 필요한 경우 사용자의 동의를 얻어야 함

### 세션 in Django

- Django는 ‘database-backed sessions’ 저장 방식을 기본 값으로 사용

- session 정보는 DB의 django_session 테이블에 저장

- Django는 요청안에 특정 session id를 포함하는 쿠키를 사용해서 각각의 브라우저와 사이트가 연결된 session 데이터를 알아냄

- Django는 우리가 session 메커니즘에 대부분을 생각하지 않게끔 많은 도움을 줌

### ‘AbstractUser’ class

- 관리자 권한과 함께 완전한 기능을 가지고 있는 User Model을 구현하는 추상 기본 클래스

### Abstract Base Classes 추상 기본 클래스

- 몇 가지 공통 정보를 여러 다른 모델에 넣을 때 사용하는 클래스

- 데이터베이스 테이블을 만드는 데 사용되지 않으며, 대신 다른 모델의 기본 클래스로 사용되는 경우 해당 필드가 하위 클래스의 필드에 추가됨

### User Model 상속 관계

![user_model_상속_관계](./images/user_model_상속_관계.png)

### User Model 대체하기 TIP

- User Model을 대체하는 순서를 숙지하기 어려울 경우 해당 공식문서를 보며 순서대로 진행하는 것을 권장


### `is_authenticated` 속성 코드

- 메서드가 아닌 속성 값임을 주의

![is_authenticated_속성_코드1](./images/is_authenticated_속성_코드1.png)

### 회원가입 후 로그인까지 이어서 진행하려면

- 회원가입 성공한 user 객체를 활용해 login 진행
    
    ![회원가입_후_로그인까지_이어서_진행1](./images/회원가입_후_로그인까지_이어서_진행1.png)
    
- UserCreationForm의 save 메서드
    
    ![회원가입_후_로그인까지_이어서_진행2](./images/회원가입_후_로그인까지_이어서_진행2.png)
    

### 탈퇴와 함께 기존 사용자의 Session Data 삭제 방법

- 사용자 객체 삭제 이후 로그아웃 함수 호출

- 단, **‘탈퇴(1) 후 로그아웃(2)’의 순서가 바뀌면 안됨**

- 먼저 로그아웃이 진행되면 해당 요청 객체 정보가 없어지기 때문에 탈퇴에 필요한 유저 정보 또한 없어지기 때문

![탈퇴와_함께_기존_사용자의_session_date_삭제_방법1](./images/탈퇴와_함께_기존_사용자의_session_date_삭제_방법1.png)

### PasswordChangeForm의 인자 순서

- PasswordChangeForm이 다른 Form과 달리 user 객체를 첫 번째 인자로 받는 이유

- 부모 클래스인 SetPasswordForm의 생성자 함수 구성을 따르기 때문