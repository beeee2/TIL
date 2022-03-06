## 네 가지 핵심 키워드

#### 클라이어트

- 웹 브라우저가 클라이언트의 역할

#### 요청과 응답

#### 서버

- 서버를 구축하는 프레임워크로 장고를 배울 것

---

### Static web page(정적 웹 페이지)

- 서버가 정적 웹 페이지에 대한 요청을 받은 경우 서버는 추가적인 처리 과정 없이 클라이언트에게 응답을 보냄
- **모든 상황에서 모든 사용자에게 동일한 정보를 표시**
- 일반적으로 HTML, CSS, JavaScript로 작성됨
- flat page라고도 함



### Dynamic web page(동적 웹 페이지)

- 웹 페이지에 대한 요청을 받은 경우 서버는 추가적인 처리 과정 이후 클라이언트에게 응답을 보냄
- 동적 웹 페이지는 방문자와 상호작용하기 때문에 페이지 내용은 그때 그때 다름
- 서버 사이드 프로그래밍언어(Python, Java, C++등) 사용되며, 파일을 처리하고 데이터베이스와의 상호작용이 이루어진다.



### Framework

- 프로그래밍에서 특정 운영 체제를 위한 응용 프로그램 표준 구조를 구현하는 클래스와 라이브러리 모임
- 재사용할 수 있는 수많은 코드를 프레임워크로 통합함으로써 개발자가 새로운 애플리케이션을 위한 표준 코드를 다시 작성하지 않아도 같이 사용할 수 있도록 도움
- Application framework라고도 한다.



### Web framework

- **웹 페이지를 개발하는 과정에서 겪는 어려움을 줄이는 것이 주 목적**
- 데이터베이스 연동, 템플릿 형태의 표준, 세션 관리, 코드 재사용 등의 기능을 포함
- 동적인 웹 페이지나 웹 에플리케이션, 웹 서비스 개발 보조용으로 만들어지는 애플리케이션 프레임워크의 일종



### Django를 사용해야 하는 이유

- 검증된 Python 언어 기반 Web framework
- 대규모 서비스에도 안정적이며 오랫동안 세계적인 기업들에 의해 사용됨



### Framework Architectur

- **MVC Design Pattern(model -view-controller)**
- 소프트웨어 공학에서 사용되는 디자인 패턴 중 하나
- 사용자 인터페이스로부터 프로그램 로직을 분리하여 애플리케이션의 시각적 요소나 이면에서 실행되는 부분을 서로 영향 없이 쉽게 고칠 수 있는  애플리케이션을 만들 수 있음
- Django는 **MTV Pattern**이라고 한다.



### MTV Pattern

- **Model**
  - 응용 프로그램의 데이터 구조를 정의하고 데이터베이스의 기록을 관리(추가, 수정, 삭제)
- **Template**(MVC에서는 **View**에 해당한다.)
  - 파일의 구조나 레이아웃을 정의
  - 실제 내용을 보여주는 데 사용(presentation)
- **View**(MVC에서는 **Control**)
  - HTTP 요청을 수신하고 HTTP 응답을 반환
  - Model을 통해 요청을 충족시키는 데 필요한 데이터에 접근
  - Template에게 응답의 서식 설정을 맡김

#### Logic

해당 로직 그림을 그려서 외울 것 

- HTTP Request > (사용자(클라이언트)로부터 요청이 들어온다.)
- URLS(urls.py) > 어떤 요청인지 주소를 분석한다.
- View(views.py) > 경로를 분석해 할 일을 파악한다.
- Model(models.py) > DB에 데이터 확인하기
- Template > 검색데이터와 문서를 합쳐서 
- HTTP Response 클라이언트에게 응답한다.



#### Django 시작하기

``` bash
$ pip install django==3.2.12
$ python -m venv venv
$ source venv/Scripts/activate
$ pip freeze > requirements.txt
$ django-admin startproject <프로젝트명> .
```

- venv 뒤에오는 것은 가상환경의 이름 
- 가상환경은 git으로 관리하지 않는다.
- pip freeze 로 requirements.txt 텍스트 파일을 만들어 목록으로 관리한다.
- $ django-admin startproject <프로젝트명> . 
  - 현재 경로에서 프로젝트를 생성한다.
  - Python이나 Django에서 사용중인 키워드를 사용할 수 없다.





#### 프로젝트 구조

- settings.py, urls.py, manage.py 사용할 예정
- manage.py
  - Django 프로젝트와 다양한 방법으로 상호작용하는 커맨드라인유틸리티

- articles 내에서 admin.py models.py views.py 만 건드린다.



### Project & Application (시험문제, 차이점)

#### Project

- Project(이하 프로젝트)는 Application의 집합
- 프로젝트에는 여러 앱이 포함될 수 있음

#### Application

- 앱은 실제 요청을 처리하고 페이지를 보여주고 하는 등의 역할을 담당
- 하나의 프로젝트는 여러 앱을 가짐
- 일반적으로 앱은 하나의 역할 및 기능 단위로 작성함

#### 앱등록시 주의사항

- 순서를 지키지 않아도 수업과정에서는 문제가 없지만, 추후 advanced 한 내용을 대비하기 위해 지키는 것을 권장한다. 
- 로딩 순서
  - Local apps > Third party apps > Django apps

---



# 순서

url > View > Template

## 가상





---

### Templates



---

### 추가 설정(1/2)

#### Language_code

- 모든 사용자에게 제공되는 번역을 결정
- 이 설정이 적용되려면 USE_I18N이 활성화되어 있어야 한다.
- 디버깅을 위해서 영어로 다시 변경하는 게 좋다.
- 

---

### Django Template Language(DTL)



for문 필수



- 



---

### DTL Syntax(3/4) - Tags













wkdrhd 



시험문제

장고어드민은 프로젝트 생성때만 쓰인다 





프로젝트랑 어플리케이션 



마지막 슬래슁 무조건 붙이기



종료태그 필요하다(for if 범위지정해야하는 것들은 모두 종료 태그가 필요하다.)

![image-20220302174547188](template and View and Routing.assets/image-20220302174547188.png)

시험단골

![image-20220302174624656](template and View and Routing.assets/image-20220302174624656.png)



### 시험문제

- DTL
- 코드의 작성 순서
- 



---

# 0303 내용 정리

### 🧶 장고 PJT 기본준비단계

1. 가상환경 생성 및 실행

   ```bash
   $ python -m venv venv
   $ source venv/Scripts/activate
   ```

2. 장고 3.2 LTS 버전 설치 및 가상환경 패키지의 목록을 저장한 텍스트 파일 생성

   ``` bash
   $ pip install django==3.2
   $ pip freeze > requirements.txt
   ```

   

3. Project 생성

   ``` bash
   $ django-admin startproject config .
   $ ls #manage.py가 바로 확인되어야 한다.
   ```

   

4. app 생성 및 등록

   ``` bash
   $ python manage.py startapp articles # 복수형으로 생성할 것
   # settings.py에 INSTALLED_APPS에 등록
   ```

   

5. 프로젝트 폴더 바로 아래에 'templates'라는 폴더 생성 후 settings에 DIRS 등록할 것

   ``` python
   EMPLATES = [
       {
           'BACKEND': 'django.template.backends.django.DjangoTemplates',
           'DIRS': [BASE_DIR / 'templates'],
           'APP_DIRS': True,
           'OPTIONS': {
               'context_processors': [
                   'django.template.context_processors.debug',
                   'django.template.context_processors.request',
                   'django.contrib.auth.context_processors.auth',
                   'django.contrib.messages.context_processors.messages',
               ],
           },
       },
   ]
   ```

   

6. base.html는 공통사용 템플릿

   ``` python
   <!DOCTYPE html>
   <html lang="en">
   <head>
     <meta charset="UTF-8">
     <meta http-equiv="X-UA-Compatible" content="IE=edge">
     <meta name="viewport" content="width=device-width, initial-scale=1.0">
     <title>Document</title>
     <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">
   </head>
   <body>
   
     <div class="container">
       {% block content%}
       {% endblock content%}
     </div>
     
     <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
   </body>
   </html>
   ```

   

7. settings.py에 TEMPLATES 에 있는 DIRS 리스트에 'templates'경로 등록

   - DIRS, BASE_DIR / 'templates'

8. base.html을 생성하고 꾸민다

9. urls.py > views.py 순으로 경로를 지정하고 작성한다.

   ``` python
   #urls.py
   from django.contrib import admin
   from django.urls import path
   from articles import views
   
   urlpatterns = [
       path('admin/', admin.site.urls),
       path('greeting/', views.greeting),
   ]
   
   ```

   ```python
   #views.py
   from django.shortcuts import render
   
   # Create your views here.
   def greeting(request):
       context = {
           'name' : 'Sueun',
       }
       return render(request, 'greeting.html', context)
   ```

   

10. articles 하위에 templates 폴더 생성, templates 내에 작성하고 싶은 html파일을 생성한다.

11. base.html을 상속받아 사용한다.

    ``` python
    {% extends 'base.html' %}
    {% block content %}
      <h1>안녕하세요 {{ name }}님의 방문을 환영합니다.</h1>
    {% endblock content %}
    ```

12. 서버를 실행하여 확인한다.

    ``` bash
    $ python manage.py runserver
    ```

    



---

# HTML Form

###  HTML 'form' element

- 사용자로부터 입력받은 데이터를 서버로 전송하는 역할을 담당
- **핵심속성**(중요)
  - **action** : 입력데이터가 전송될 URL 지정, 전달될 서버주소가 입력된다.
  - **method** : 입력데이터 전달 방식 지정

### HTML 'Input' element

- 사용자로부터 데이터를 입력 받기 위해 사용
- type 속성에 따라 동작 방식이 달라짐
- 핵심 속성
  - **name**(반드시 입력해야 한다.)
    - name에 들어가는 값이 변수명이라고 볼 수 있다.
  - 중복 가능, 양식을 제출했을 때 name이라는 이름에 설정된 값을 넘겨서 값을 가져올 수 있음
  - 주요 용도는  GET/POST 방식으로 서버에 전달하는 피라미터로 ?key=value&key=value 형태로 전달된다.



### HTML 'label' element

- label을 input 요소와 연결하여 사용한다.



### HTTP

- HpyerText Transfer Protocol
- 웹에서 이루어지는 모든 데이터 교환의 기초
- 주어진 리소스가 수행할 작업을 나타내는 request methods를 정의
- GTTP request method 종류
  - **GET, POST**, PUT, DELETE ..
  - 기본적으로 장고는 GET과 POST만 지원한다.

### HTTP request method - 'GET'

-  서버로부터 **정보를 조회**하는데 사용(중요)
- 데이터를 **가져올 때만 사용**해야 함(중요)
- 데이터를 서버로 전송할 때 body가 아닌 Query String Parameters 를 통해전송
  -  Query String Parameters란? URL에 적힌 분분
  - 'search?q=mdn&msp'와 같이 주소로 전달된다.
  - 물음표뒤에 key=value 형태로 전달된다.
- 우리는 서버에 요청을 하면 HTML 문서 파일 한 장을 받는데, 이 때 사용하는 요청의 방식이 GET



### 실습 Throw & Catch

- throw 통해 요청이 오면 html 문서를 만들어 전달한다.



---

# URL

### Django URLs

- Dispatcher



### Naming 

### URL Template Tag

DRY 원칙을 위반하지 않으면서도

---

## Check

- Variable Routing
  - 꺽쇠이용하기, 타입, 받을 이름
  - views.py에 해당 값을 기재해야 한다.
- App URL mapping