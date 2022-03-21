# Django 문제집

## 📕 Web Framework

1. Web이란? (O, X)

   World Wide Web의 줄임말로 인터넷에 연결된 컴퓨터를 통해 정보를 공유할 수 있는 전 세계적인 정보 공간이다. 

   > 정답 : (O)

2. Static web page(정적 웹 페이지)는 모든 상황에서 모든 사용자에게 동일 정보를 표시하나, 동적 웹 페이지는 방문자와 상호작용하기 때문에 페이지의 내용이 그때그때 다르다. (O,X)

   > 정답 : O

3. Framework Architecture인 MVC Design Pattern(Model-view-controller)는 Django에서 __ ___ 이라고 한다. 

   > 정답 : MTV Pattern

4. 위 정답과 MVC Pattern을 관련있는 것 끼리 연결하시오.

   > 정답 : 
   >
   > MVC Pattern : Model, View, Controller
   >
   > MTV Pattern : Model, Template, View
   >
   > (좌 MVC, 우 MTV) Model <-> Model, View <->Template, Controller <-> View

- MTV Pattern
  - Model > Model
    - 응용프로그램의 데이터 구조를 정의하고 데이터베이스의 기록을 관리(추가, 수정, 삭제)
  - Template > View
    - 파일의 구조나 레이아웃을 정의
    - 실제 내용을 보여주는 데 사용(presentation)
  - View > Controller
    - HTTP 요청을 수신하고 HTTP 응답을 반환한다.
    - Model을 통해 요청을 충족시키는데 필요한 데이터에 접근한다.
    - template에게 응답의 서식 설정을 맡긴다.



## 📙 Django Intro



### 📑 Django 시작하기

1. 가상환경만들기

   ``` v
   python -m venv venv
   ```

2. 가상환경 활성화하기

   ``` bash
   source venv/Scripts/activate
   ```

3. 가상환경이 정상적으로 실행되었는지 확인한다.

   ``` bash
   pip list
   ```

   - 방금 생성되었고 정상적인 상태라면 pip list에는 2개(pip, setuptools)만 있다.

4. 장고 프로젝트를 생성한다.

   - 프로젝트 폴더를 미리 생성하여 내부에 manage.py 파일을 만들고 싶을 때

     ``` bash
     django-admin startproject 프로젝트명 .
     ```

     

   - 폴더를 생성하고 싶은 경우

     ``` bash
     django-admin startproject 프로젝트명
     ```

5. manage.py 위치를 확인한다.

   - ls 명령어를 이용하여 manage.py의 존재 여부를 확인하고 없다면 해당 파일이 있는 곳으로 이동한다.

6.  어플리케이션을 생성한다.

   ``` bash
   python manage.py startapp 애플리케이션명
   ```

7. 어플리케이션을 settings.py에 등록한다.

   - INSTALLED_APP 에 생성한 어플리케이션을 등록한다.
   - 이 때 콤마를 빠트리지 않도록 한다.

8. settings.py와 같은 곳에 위치한 urls.py를 먼저 수정한다.

   - 주석을 확인하여 include를 import 한다.
   - urlpatterns 리스트에
     - path('경로/', include('앱이름.urls')), 를 추가한다.
     - 경로는 보통 앱 이름으로 작성한다.

9. 만든 앱 폴더 내부에 urls.py 파일을 새로 생성한다.

   - 기본 구조를 다음과 같이 작성한다.

     ``` python
     from django.urls import path
     from . import views
     
     app_name = '앱이름'
     urlpatterns = [
         
     ]
     ```

10. 공통으로 사용하는 템플릿 파일을 만든다.

    - 위치는 manage.py와 같은 곳에 templates라는 폴더를 생성한다.
    - 생성한 templates 폴더 내부에 base.html파일을 생성한다.

11. 위에서 생성한 templates 폴더의 위치를 settings.py에 등록한다.

    - 아래와 같이 DIRS에 BASE_DIR / 'templates'를 리스트 내부에 추가한다.

      ``` python
      TEMPLATES = [
          {
              ...
              'DIRS' : [BASE_DIR / 'templates'],
              ...
          }
      ]
      ```

12. base.html을 작성한다.

    - DTL ) block tag를 반드시 추가한다.

    - block 위치에 다른 template들이 위치하게 된다.

      ``` html
      <body>
          {% block content %}
      	{% endblock content %}
      </body>
      ```

- 이후 urls.py > views.py > template(html) 작성 순으로 개발을 하면 된다.

13. 서버활성화하기

    ``` bash
    python manage.py runserver
    ```

    



Q1. 프로젝트 이름으로 쓰일 수 없는 것들을 고르시오.

- Django, class, django-test, text

  > 정답:
  >
  > 프로젝트 이름에는 Python이나 Django에서 사용중인 키워드를 피해야 한다. '-'(하이픈)도 사용할 수 없다.
  >
  > 모두 다 사용할 수 없다. 

Q2. 프로젝트 구조 내 파일에 관한 설명이다. 알맞게 연결하시오.

- __ init __.py , settings.py, urls.py, manage.py

- 설명

  1) Python에게 이 디렉토리를 하나의 Python 패키지로 다루도록 지시한다.
  2) 애플리케이션의 모든 설정을 포함한다.
  3) Django 프로젝트와 다양한 방법으로 상호작용하는 커맨드라인 유틸리티
  4) 사이트의 url과 적절한 views의 연결을 지정한다.

  > 정답:
  >
  > (1) : __ init __.py
  >
  > (2) : settings.py
  >
  > (3) : manage.py
  >
  > (4) : urls.py

Q3. 일반적으로 Application명은 복수형으로 하는 것을 권장한다.(O, X)	

> 정답:
>
> (O)

Q4. Application 구조 내 파일에 관한 설명이다. 알맞게 연결하시오.

- admin.py,  apps.py, models.py, tests.py, views. py
- 설명
  - 관리자용 페이지를 설정하는 곳
  - 앱의 정보가 작성된 곳
  - 앱에서 사용하는 Model을 정의하는 곳
  - 프로젝트의 테스트 코드를 작성하는 곳
  - view 함수들이 정의되는 곳



### 📑 Project & Application

- Project
  - Project(이하 프로젝트)는 Application(이하 앱)의 집합(collection of apps)
  - 프로젝트에는 여러 앱이 포함될 수 있다.
  - 앱은 여러 프로젝트에 있을 수 있다.
- Application
  - 앱은 실제 요청을 처리하고 페이지를 보여주고 하는 등의 역할을 담당한다.
  - 하나의 프로젝트는 여러 앱을 가진다.
  - 일반적으로 **앱은 하나의 역할 및 기능 단위**로 작성한다.



Q5. 프로젝트에서 앱을 사용하기 위해 반드시 해야할 것은?

> 정답:
>
> INSTALLED_APPS 리스트에 추가해야한다.
>
> INSTALLED_APPS는 Django installation에 활성화된 모든 앱을 지정하는 문자열 목록이다.

Q6. INSTALLED_APPS에 먼저 앱을 등록하고 앱을 생성하는 것과 앱을 생성하고 등록하는 것과 서로 차이가 없다. (O, X)

> 정답 :
>
> X, 
>
> INSTALLED_APPS에 먼저 작성(등록)하고 생성하려면 앱이 생성되지 않는다. 반드시 생성하고 등록한다.





## 📒 요청과 응답

Q1. 다음 설명과 관련된 단어를 골라 연결하시오. 

- URLs, View,  Templates
- 설명
  - (1) HTTP요청(request)을 알맞은 view로 전달한다.
  - (2) HTTP 요청을 수신하고 HTTP 응답을 반환하는 함수를 작성한다. 
  - (3) Model을 통해 요청에 맞는 필요 데이터에 접근한다.
  - (4) Template에게 HTTP 응답 서식을 맡긴다.
  - (5) 실제 내용을 보여주는데 사용되는 파일이다.
  - (6) 파일의 구조나 레이아웃을 정의한다.
  - (7) **Template 파일 경로의 기본 값**은 **app 폴더 안의 templates 폴더**로 지정되어 있다.

Q2. LANGUAGE_CODE에서 설정한 값이 적용되려면 ___이 활성화되어 있어야 한다.

> 정답 :
>
> USE_I18N이 활성화되어 있어야 한다.
>
> USE_I18N은 Django의 번역 시스템을 활성화해야 하는지 여부를 지정한다.

Q3. 한국어와 서울시간대로 바꾸기 위해 LANGUAGE_CODE와 TIME_ZONE의 값을 어떻게 변경해야 하는가?

> 정답 :
>
> LANGUAGE_CODE = 'ko-kr'
>
> TIME_ZOME = 'Asia/Seoul'



## 📗 Template

### 📑 Django Template Language(DTL) : Variable, Filters, Tags, Comments

- Django template에서 사용하는 built-in template system
- 조건, 반복, 변수 치환, 필터 등의 기능을 제공한다.
- 단순히 Python이 HTML에 포함된 것이 아니라, 프로그래밍적 로직이 **프레젠테이션을 표현하기 위한 것**
- Python처럼 일부 프로그래밍 구조(if, for등)를 사용할 수 있지만, 이것은 **해당 Python 코드로 실행되는 것이 아니다**.
- Variable, Filters, Tags, Comments



Q1. Variable의 변수명에 관한 규칙이다. 변수명은 숫자와 밑줄의 조합으로 구성될 수 있으나 밑줄로는 시작할 수 없다.(O, X)

> 정답 :
>
> O

Q2. Variable의 변수명으로 공백이나 구두점 문자 또한 사용할 수 없다.(O, X)

> 정답 :
>
> O

Q3. ___ 을 사용하여 변수 속성에 접근할 수 있다. 

> 정답 :
>
> dot(.)

Q4. render()의 세번째 인자로 {'key':value}와 같이 딕셔너리 형태로 넘겨주며, 여기서 정의한 key에 해당하는 문자열이 template에서 사용가능한 변수명이 된다. (O, X)

> 정답 :
>
> O

Q5. DTL의 filters에서 사용하는 기호는 |이다. (O, X)

> 정답 :
>
> O,
>
> EX) 
>
> - {{ name|lower }} : name변수를 모두 소문자로 출력한다.
> - {{ variable|truncatewords:30 }} : chainde가 가능하며 일부 필터는 인자를 받기도 한다.

Q6. 출력 텍스트를 만들거나, 반복 또는 논리를 수행하여 제어 흐름을 만드는 등 변수보다 복잡한 일들을 수행하는 DTL의 Syntax는 무엇인가.

> 정답 :
>
> Tags이다. **일부** 태그는 시작과 종료 태그가 필요하다.
>
> ex) {% if %}{% endif %}

Q7. 주석을 표현하기 위해 사용하는 {# #}는 줄바꿈이 허용된다. (O, X)

> 정답 :
>
> X, 여러 줄 주석은 {% comment %}{% endcomment %} 사이에 입력한다.

Q8. 자식(하위)템플릿이 부모 템플릿을 확장한다는 것을 알리는 태그로 반드시 템플릿 최상단에 작성되어야 한다.

> 정답 :
>
> {% extends ' ' %}

Q9. 하위 템플릿에서 재정의(overriden)할 수 있는 블록을 정의하는 데 사용하는 태그는 무엇인가.

> 정답 :
>
> {% block content %}{% endblock %}

Q10. 템플릿을 로드하고 현재 페이지로 렌더링하는 태그이며 템플릿 내에 다른 템플릿을 "포함(including)"하는 방법으로 사용되는 태그는?

> 정답 : 
>
> {% include ' ' %}



## 📘 HTML Form

Q1. for 속성의 값과 일치하는 id를 가진 문서의 첫 번째 요소를 제어한다. (O, X)

> 정답 :
>
> O
>
> label 요소와 연결할 수 있는 요소로는 button, input(not hidden type, select, textarea)

Q2. HTTP request method의 종류로 GET, POST, PUT, DELETE..가 있다. (O,X)

> 정답:
>
> O

Q3. HTTP request method의 하나로 서버로부터 정보를 조회하는데 사용하는 방법은 무엇인가. 데이터를 서버로 전송할 때 body가아닌 Query String Parameters를 통해 전송한다.

> 정답 :
>
> GET



## 📓 URL

Q1. URL 주소를 변수로 사용하는 것을 무엇이라 하는가?

> 정답 :
>
> Variable Routing이라한다.
>
> URL의 일부를 변수로 지정하여 view 함수의 인자로 넘길 수 있다. 즉, 변수 값에 따라 하나의 path()에 여러 페이지를 연결시킬 수 있다.
>
> - ex)
>   - path('accounts/user/<ing:user_pk>', ///)
>
> 



### 📑 URL Path converters

- str
  - '/'를 제외하고 비어있지 않은 모든 문자열과 배치
  - 작성하지 않을 경우 기본 값

- int
  - 0 또는 양의 정수와 매치
- slug
  - ASCII 문자 또는 숫자, 하이픈 및 밑줄 문자로 구성된 모든 슬러그 문자열과 매치 



Q3. 프로젝트의 urls.py가 아닌 각 app에 urls.py를 작성하게 되는 이유를 서술하시오.

> 정답 :
>
> app의 view 함수가 많아지면서 사용하는 path() 또한 많아지고, app 또한 더 많이 작성되기 때문에 프로젝트의 urls.py에서 모두 관리하는 것을 프로젝트 유지보수성에 좋지 않다. 이제는 각 app에 urls.py를 작성하게된다.





## 📕 Model

Q1.  Django는 ___ 를 통해 웹 애플리케이션의 **데이터를 구조화하고 조작**한다.

> 정답 :
>
> Model

Q2. 데이터베이스에서 자료의 구조, 표현 방법, 관계 등을 정의한 구조를 가리키는 용어는?

> 정답 :
>
> 스키마(Schema)

Q3. 열을 다른 말로 속성, 행을 다른 말로 튜플이라고 한다.(O, X)

> 정답 :
>
> O 

Q4. 각 열에는 고유한 데이터 형식이 지정된다.(INTEGER, TEXT, NULL등) (O,X)

> 정답 : 
>
> O 



- Database의 기본 구조 중 하나로 PK(기본키)가 있다. PK는 각 행(레코드)의 고유 값으로 Primary Key로 불린다.  
  - 반드시 설정해야하여야 하며, 데이터베이스관리 및 관계 설정시 주요하게 활용된다.



## 📙 ORM(Object-Relational Mapping)

- ORM
  - 객체 지향 프로그래밍 언어를 사용하여 호환되지 않는 유형의 시스템간에 (Django-SQL) 데이터를 변환하는 프로그래밍 기술
  - OOP 프로그래밍에서 RDBMS을 연동할 때, 데이터베이스와 객체 지향 프로그래밍 언어 간의 호환되지 않는 데이터를 변환하는 프로그래밍 기법
  - Django는 내장 Django ORM을 사용한다.
  - **DB를 객체로 조작하기 위해 ORM을 사용**한다.
- ORM의 장점과 단점
  - 장점
    - SQL을 잘 알지 못해도 DB조작이 가능
    - SQL의 절차적 접근이 아닌 객체 지향적 접근으로 인한 높은 **생산성**
    - 현대 웹 프레임워크의 요점은 웹 개발의 속도를 높이는 것, 즉 생산성에 있다.
  - 단점
    - ORM만으로 완전한 서비스를 구현하기 어려운 경우가 있다.



Q1. 모델필드의 하나인 CharField를 사용할 때의 필수 인자를 기술하시오

> 정답 :
>
> max_length, 필드의 최대 길이(문자)를 지정해줘야 한다. 길이의 제한이 있는 문자열을 넣을 때 사용한다.

Q2. TextField에서 max_length 옵션 작성시 모델과 데이터베이스에 적용된다(O, X)

> 정답 :
>
> X, max_length 옵션 작성시 자동 양식 필드인 textarea 위젱에 반영은 되지만 모델과 데이터베이스 수준에는 적용되지 않는다. max_length 사용은 CharField에서 사용해야 한다.



## 📒 Migrations

- Migrations
  - Django가 model에 생긴 변화를 반영하는 방법이다.
  - Migraton 실행 및 DB스키마를 다루기 위한 명령어로 makemigrations, migrate, sqlmigrate, showmigrations가 있다.

Q1. model을 변경한 것에 기반한 새로운 마이그레이션(설계도)를 만들 때 사용하는 명령어는?

> 정답 :
>
> makemigrations

Q2. 마이그레이션을 DB에 반영하기 위해 사용하는 것은?

> 정답 :
>
> migrate

Q3. 설계도를 실제 DB에 반영하는 과정에 쓰이는 명령어는?

> 정답 :
>
> migrate

Q4. 모델에서의 변경사항들과 DB의 스키마가 동기화를 이루기 위해 사용하는 명령어는?

> 정답 :
>
> migrate

Q5. 마이그레이션에 대한 SQL 구문을 보기 위해 사용하는 명령은?

> 정답 :
>
> sqlmigrate

Q6. 프로젝트 전체의 마이그레이션 상태를 확인하기 위해 사용하는 명령어는?

> 정답:
>
> showmigrations

Q7. 마이그레이션이 SQL문으로 어떻게 해석되어서 동작할 지 미리 확인할 수 있는 명령어는?

> 정답 :
>
> sqlmigrate

Q8. 마이그레이션 파일들이 migrate 됐는지 안됐는지 여부를 확인할 수 있는 명령어는?

> 정답 :
>
> showmigrations



``` bash
$ python manage.py makemigrations
# migrations/0001_initial.py 생성확인
$ python manage.py migrate
# 0001_initial.py 설계도를 실제 DB에 반영한다.
$ python manage.py sqlmigrate app_name 0001
# 해당 migrations 설계도가 sql문으로 어떻게 해석되어서 동작할지 미리 확인할 수 있다.
$ python manage.py showmigrtaions
# migrations 설계도들이 migrate됐는지 안됐는지 여부를 확인할 수 있다.
```



Q9. DateField's options 중 하나로 Django ORM이 최초 insert(테이블에 데이터 입력)시에만 현재 날짜와 시간으로 갱신하게 하는 옵션은 무엇인가? 

> 정답
>
> auto_now_add, 최초 생성일자(테이블에 어떤 값을 최초로 넣을 때)

Q10. DateField's options 중 하나로 Django ORM이 save를 할 때마다 현재 날짜와 시간으로 갱신되는 옵션은?

> 정답 :
>
> auto_now, 최종 수정일자를 기반으로 한다.



-  반드기 기억해야 할 migration의 3단계
  1. models.py
     - model 변경사항 발생 시
  2. $ python manage.py makemigrations
     - migrations 파일 생성
  3. $ python manage.py migrate
     - DB반영(모델과 DB의 동기화)



## 📗 Database API

Q1. 쿼리를 만들 때 순서를 기재하시오. (QuerySet API,  Class Name, Manager)

> 정답 :
>
> ClassName.Manager.QuerySetAPI
>
> ex) Aricle.objects.all()
>
> - Manager
>   - Django 모델에 데이터베이스 query 작업이 제공되는 인터페이스
>   - 기본적으로 모든 Django 모델 클래스에 objects라는 Manager를 추가
> - QuerySet
>   - 데이터베이스로부터 전달받은 객체 목록
>   - queryset 안의 객체는 0개, 1개 혹은 여러 개일 수 있음
>   - 데이터베이스로부터 조회, 필터, 정렬등을 수행할 수 있다.

Q2. 일반 Python Shell을 통해 장고 프로젝트 환경에 접근한다. (O, X)

> 정답 : X
>
> 장고 프로젝트 설정이 load 된 Python shell, Django Shell을 활용해서 DB API 구문테스트를 진행할 수 있다.
>
> ``` bash
> $ pip install ipython
> $ pip install django-extensions
> ```
>
> ``` python
> #settings.py
> INSTALLED_APPS =[
>     ....,
>     'django_extensions',
>     ...,
> ] # 앱을 등록한다.
> ```
>
> ``` bash
> $ python manage.py shell_plus
> ```
>
> 



## 📘 CRUD	

- CRUD
  - 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리기능인 Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말

Q1. 주어진 loopup 매개변수와 일치하는 객체를 반환하는 메서드는?

> 정답 : 
>
> .get()

Q2. 위 메서드는 객체를 찾을 수 없으면 (A) 예외를 발생시키고, 둘 이상의 객체를 찾으면 (B) 예외를 발생시킨다.

> 정답 :
>
> A : DoesNotExist
>
> B : MultipleObjectsReturned
>
> 위와 같은 특징을 가지고 있기에 primary key와 같이 고유성을 보장하는 조회에서 사용해야 한다.

Q3. delete()은 QuerySet의 모든 행에 대해 SQL 삭제 쿼리를 수행하고, 삭제된 객체 수와 객체 유형당 삭제 수가 포함된 딕셔너리를 반환한다.(O, X)

> 정답 :
>
> O





## 📕 Admin Site

- Automatic admin interface

  - 사용자가 아닌 서버의 관리자가 활용하기 위한 페이지

  - Model class를 admin.py에 등록하고 관리한다.

  - django.contrib.auth 모듈에서 제공된다.

  - record 생성 여부 확인에 매우 유용하며, 직접 record를 삽입할 수도 있다. 

    ``` bash
    $ python manage.py createsuperuser
    ```

  - 관리자 계정 생성 후 서버를 실행한 다음 '/admin'으로 가서 관리자 페이지에 로그인한다.

  - 내가 만든 Model을 보기 위해서는 admin.py에 작성하여 Django 서버에 등록한다.

    ``` python
    # articles/admin.py
    from django.contrib import admin
    from .models import Article
    
    class ArticleAdmin(admin.ModelAdmin):
        list_display = ('pk', 'title', 'content', 'created_at', 'updated_at')
    
    #admin site에 register 하겠다는 의미.
    admin.stie.register(Article)
    ```

  - admin.py는 관리자 사이트에 Article 객체가 관리자 인터페이스를 가지고 있다는 것을 알려주는 것이다.

  - models.py에 정의한 __ str__의 형태로 객체가 표현된다.

  - list_display를 이용하여 models.py에서 정의한 각각의 속성들의 값을 admin 페이지에 출력하도록 설정한다.



## 📗 CRUD with views

Q1. HTTP Method에 관한 내용이다. GET과 POST 중 적절하게 연결하시오.

1) 반드시 데이터를 가져올 때만 사용해야 한다.

2) 리소스를 생성/변경하기 위해 데이터를 HTTP body에 담아 전송한다.

3) DB에 변화를 주지않는다.

4) 서버에 변경사항을 만든다.

5) CRUD에서 C/U/D 역할을 담당한다.

6) CRUD에서 R역할을 담당한다.

   > 정답
   >
   > 1,3, 6은 GET, 2, 4, 5는 POST

Q2. 웹 애플리케이션 취약점 중 하나로 사용자가 자신의 의지와 무관하게 공격자가 의도한 행동을 하여 특정 웹페이지를 보안에 취약하게 하거나 수정, 삭제 등의 작업을 하게 만드는 공격방법을 일컫는 용어는?

> 정답
>
> 사이트 간 요청 위조(Cross-site request forgery)

Q3. CSRF에 대항하여 Django는 (A)와 (B)를 제공한다.

> 정답 :
>
> middleware와 template tag를 제공한다.
>
> - 장고는 CSRF toekn 템플릿 태그를 제공한다.
> - 일반적으로 데이터 변경이 가능한 POST, PATCH, DELETE Method 등에 적용된다(GET제외)
> - {% csrf_token %}
> - CSRF 공격 관련 보안 설정은 settings.py에서 MIDDLEWARE에 작성 되어있다.



Q4. 웹 애플리케이션의 데이터를 구조화하고 조작하기 위한 도구는?

> 정답 
>
> Model

Q5. 체계화된 데이터의 모임(집합)을 일컫는 용어는?

> 정답 :
>
> Database

Q6. Django가 model에 생긴변화를 반영하는 방법은?

> 정답 :
>
> Migrations



---

# Homework & Workshop

1. Django는 MTV 디자인 패턴으로 이루어진 Web Framework이다. 여기서 MTV는 무엇의 약자이며, 각각 MVC 디자인 패턴과 어떻게 매칭이 되며 각 키워드가 django에서 하는 역할을 간략히 서술하시오.

   > M은 Model, T는 Template, V는 View를 의미한다.
   >
   > MTV의 M은 MVC의 M(Model)과 매칭된다.
   > Model은 웹 애플리케이션의 **데이터를 구조화하고 조작**한다.
   >
   > MTV의 T은 MVC의 V(View)와 매칭된다.
   > Template은 사용자에게 보여지는 부분을 담당한다.
   >
   > MTV의 V은 MVC의 C(Controller)와 매칭된다.
   > View는 요청을 받고 응답을 해주는 역할을 한다.

2. __(a)__는 Django에서 URL 자체를 변수처럼 사용해서 동적으로 주소를 만드는 것을 의미한다. __(a)__는 무엇인지 작성하시오.

   >  (a) : Variable Routing
   >

3. Django 프로젝트는 render할 template 파일들을 찾을 때, 기본적으로 settings.py에 등록된 각 앱 폴더 안의 __(a)__ 폴더 내부를 탐색한다.  __(a)__에 들어갈 폴더 이름을 작성하시오

   > templates

4. django 프로젝트를 한국어로 제공하기 위해 번역이 필요하다. 이 설정을 위해 settings.py에 어떤 변수 그리고 어떤 값을 할당해야 하는지 작성하시오. 1-2 추가로 settings.py에 ‘이 변수‘가 활성화인 상태여야 1-1번 변수를 설정할 수 있다고 한 다. ‘이 변수’는 무엇인가?’

   > 1-1. settings.py의 LANGUAGE_CODE = 'ko-kr'로 변경한다.
   > 1-2. USE_I18N = True여야지 언어를 변경할 수 있다.

5. 다음은 어떤 django 프로젝트의 urls.py의 모습이다. 주소 ’/ssafy’로 요청이 들어왔을 때 실 행되는 함수가 pages 앱의 views.py 파일 안 ssafy 함수라면, 요청에 응답하기 위해 빈칸 __(a)__에 추가되어야 할 코드를 작성하시오

   ``` python
   from django.contrib import admin
   from django.urls import path
   from pages import views
   
   urlpatterns = [
       path(_a_),
       path('admin/', admin.site.urls),
   ]
   ```

   > (a) : 'ssafy/', views.ssafy

6. menus 리스트를 반복문으로 출력하시오.

   ``` django
   {% for _(a)_ in menus %}
   	<p>{{menu}}</p>
   {% endfor %}
   ```

   > menu

7. posts 리스트를 반목문을 활용하여 0번 글부터 출력하시오.

   ``` django
   {% for post in posts %}
   	<p>
           {{_a_}}번 글 : {{post}}
   </p>
   {% endfor %}
   ```

   > forloop.counter0

8. users 리스트가 비어있다면 현재 가입한 유저가 없습니다. 텍스트를 출력하시오

   ``` django
   {% for user in users %}
   	<p>
           {{user}}
   </p>
   {% _(a)_ %}
   	<p>
           현재 가입한 유저가 없습니다.
   </p>
   {% endfor %}
   ```

   > empty

9. 첫 번째 반복문일 때와 아닐 때를 조건문으로 분기처리 하시오

   ``` django
   {% _(a)_ forloop.first %}
   	<p>
           첫 번째 반복문입니다.
   </p>
   {% _(b)_ %}
   	<p>
           첫 번째 반복문이 아닙니다.
   </p>
   {% endif %}
   ```

   > (a) : if, (b) :else

10. 출력된 결과가 주석과 같아지도록 하시오

    ``` django
    <!--5-->
    <p>
        {{'hello'|_(a)_}}
    </p>
    <!-- My Name Is Tom -->
    <p>
        {{'my name is tom'|_(b)_}}
    </p>
    ```

    > (a)length (b):title

11. 변수 today에 datetime 객체가 들어있을 때 출력된 결과가 주석과 같아지도록 작성하시오.

    ``` django
    <!-- 2020년 02월 02일 (Sun) PM 02:02 -->
    {{ today|date:"_(a)_" }}
    ```

    > Y년 m월 d일 (D) A h:i

12. 지문의 코드 중 form 태그의 속성인 action의 역할에 대해 설명하시오. 

    > action의 역할 : 유저가 입력한 데이터가 전송될 URL 지정

13. 지문의 코드 중 method가 가질 수 있는 속성 값을 작성하시오.  

    > 장고에서 공식적으로 지원하는 method의 종류로 GET, POST가 있다.

14. input 태그에 각각 `안녕하세요`, `반갑습니다`, `파이팅` 문자열을 넣고 submit 버튼을 눌렀을 때 이동하는 url 경로를 작성하시오

    >  HOST/PORT//create/?title=안녕하세요&content=반갑습니다&my-site=파이팅

15. “Django가 Model에 생긴 변화를 DB에 반영하는 방법” 을 뜻하는 용어를 작성

    > migrations

16.  Model의 변경사항을 저장하기 위한 명령어를 작성하시오.  

    > migrate

17. 이로 인해 생성된 마이그레이션 파일에 대응되는 SQL문을 확인하기 위한 명령어와 출력결과를 작성하시오. (app의 이름은 articles이다.)

    > sqlmigrate

18. Django에서 사용 가능한 모듈 및 메서드를 대화식 Python Shell에서 사용하려고 할 때,  어떤 명령어를 통해 해당 Shell을 실행할 수 있는지 작성하시오

    > $ pip install ipython

19. Django에서 Model을 정의할 때 사용할 수 있는 필드 타입을 5가지 이상 작성하시오.

    > DateTimeField, ForeignKey, IntegerField, FloatField, ImageField, EmailField, CharField, TextField, AutoField

20. 만들어진 모든 Post 객체를 QuerySet형태로 반환 해주기 위해 빈칸에 들어갈 코드를 작성하시오

    ``` bash
    posts = Post.(a).(b)()
    ```

    > (a) : objects
    >
    > (b) : all

21. RDBMS의 개념적 정의와 이를 기반으로 한 DB-Engine의 종류 세가지 이상 작성하시오.

    > RDBMS, Relational Database Management System의 줄임말로
    > 관계형 모델을 기반으로 하는 데이터베이스 관리시스템을 의미한다.
    > 관계형 데이터베이스 엔진으로 Oracle, MySQL, MariaDB, PostgreSQL등이 있다.

22. SQL에서 사용 가능한 와일드카드 문자인 %와 _을 비교하여 작성하시오

    > %(percent sign)은 0개 이상의 문자가 있는 지 패턴을 확인하며, _(underscore)는 임의의 단일문자가 있는지 확인한다.