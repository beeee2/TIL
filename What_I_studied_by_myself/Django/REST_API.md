# 🌱REST API

## 🥔 HTTP

#### HTTP

- HyperText Transfer Protocol
- 웹 상에서 컨텐츠를 전송하기 위한 약속
- HTML 문서와 같은 리소스들을 가져올 수 있도록 하는 프로토콜(규칙, 약속)
- 웹에서 이루어지는 모든 데이터 교환의 기초_
  - 요청(request)
    - 클라이언트에 의해 전송되는 메세지
  - 응답(response)
    - 서버에서 응답으로 전송되는 메세지
- 기본 특성
  - Stateless(상태가 없음 )
  - Connectionless(비연결성)
- 쿠키와 세션을 통해 서버 상태를 요청과 연결하도록 함



#### HTTP 메세지

- 요청예시
  - 메소드 방식
  - 요청한 주소
  - 프로토콜의 버전
  - 헤더부분에 추가적인 정보 기재
- 응답예시
  - 프로토콜의 버전
  - 상태코드(서버의 상태과 결과를 숫자로 표현한다.)
  - 상태 메세지
  - 헤더에 추가적인 정보 기재

- HTTP 객체가 서로 요청과 응답을 통해 왔다갔다 하며 그 안에는 여러 정보들이 들어있음을 알 수 있다.



#### HTTP request methods

- 자원에 대한 행위(수행하고자 하는 동작)을 정의
- 주어진 리소스(자원)에 수행하길 원하는 행동을 나타냄
- HTTP Method 예시
  - GET, POST, PUT, DELETE

** PUT과 PATCH의 차이 알아보기





💁‍♀️ 이제 역할을 바꾸어 수정일 경우 'PUT'을 삭제일 경우'DELETE'를 보내보자.

💁‍♀️ 'GET'은 조회, 'POST'은 작성



#### HTTP response status codes

- 응답의 상태 코드
- 특정 HTTP 요청이 성공적으로 완료되었는 지 여부를 나타낸다.
- 응답은 5개의 그룹으로 나뉘어진다.
  1. Informational responses (1xx)
     - 정보에 대한 응답
  2. Successful responses (2xx)
  3. Redirection messages (3xx)
  4. Client error responses (4xx)
  5. Server error responses (5xx)



#### 웹에서의 리소스 식별

- HTTP 요청의 대상을 리소스(resource, 자원)라고함
- 리소스는 문서, 사진 또는 기타 어떤 것이든 될 수 있음
- 각 리소스는 리소스 식별을 위해 HTTP 전체에서 사용되는 URI(Uniform Resource Identifier)로 식별된다.



#### URL, URN

- URL(Uniform Resource Locator)
  - 통합 자원 위치
  - 네트워크 상에 자원이 어디 있는지 알려주기 위한 약속
  - 과거에는 실제 자원의 위치를 나타냈지만 현재는 추상회된 의미론적인 구성
  - '웹 주소', '링크'라고도 불림
- URN(Uniform Resource Name)
  - 통합 자원 이름
  - URL과 달리 자원의 위치에 영향을 받지 않는 유일한 이름 역할을 한다.
  - 예시
    - ISBM(국제표준도서번호)

#### URI

- Uniform Resource Indentifier
  - 통합 자원 식별자
  - 인터넷의 자원을 식별하는 유일한 주소(정보의 자원을 표현)
  - 인터넷에서 자원을 식별하거나 이름을 지정하는데 사용되는 간단한 문자열
  - 하위 개념
    - URL, URN
- URI는 크게 URL과 URN으로 나눌 수 있지만, URN을 사용하는 비중이 매우 적기 때문에 일반적으로 URL은 URI와 같은 의미처럼 사용되기도 한다.



#### URI의 구조

- Scheme(protocol)
  - 브라우저가 사용해야 하는 프로토콜
  - http(s), data, file, ftp, mailto
- Host ( Domain name)
  - 요청을 받는 웹 서버의 이름
  - IP address를 직접 사용할 수도 있지만, 실 사용 시 불편하므로 웹에서 그리 자주 사용되지는 않는다.
- Port
  - 웹 서버 상의 리소스에 접근하는데 사용되는 기술적인 '문(path)'
  - 일반적으로는 출력되지 않는다. 로컬서버에서 진행할 때 출력된다.
  - 보통 생략된다.
  - HTTP 프로토콜의 표준 포트
    - HTTP 80
    - HTTPS 443

- Path
  - 웹 서버상의 리소스 경로
  - 초기에는 실제 파일이 위치한 물리적 위치를 나타냈지만,
  - 오늘날은 물리적인 실제위치가 아닌 추상화 형태의 구조로 표현

- Query(Indentifier)
  - url에서 물음표 뒤쪽에 붙음
  - 쿼리 또는 식별자라고 부른다.
  - Query String Parameters
  - 웹 서버에 제공되는 추가적인 매개변수
  - &로 구분되는 key-value 목록

- Fragment

  - Anchor
  - 자원 안에서의 북마크의 한 종류를 나타낸다.
  - 브라우저에게 해당 문서(HTML)의 특정 부분을 보여주기 위한 방법
  - 브라우저에게 알려주는 요소이기 때문에 fragment identifier(부분 식별자)라고 부르며 '#' 뒤의 부분은 요청이 서버에 보내지지 않는다.

  - 브라우저가 해석하며 서버에 보내지는 요소는 아니다.



---



## 🥔 RESTful API

#### API

- Application Programming Interface
- 프로그래밍 언어가 제공하는 기능을 수행할 수 있게 만든 인터페이스
  - 애플리케이션과 프로그래밍으로 소통하는 방법
  - CLI는 명령줄, GUI는 그래픽(아이콘), API는 프로그래밍을 통해 특정한 기능을 수행한다.
- Web API
  - 웹 애플리케이션 개발에서 다른 서비스에 요청을 보내고 응답을 받기 위해 정의된 명세
  - 현재 웹 개발을 모든 것을 직접 개발하기보다 여러 Open API를 활용하는 추세
- 응답 데이터 타입
  - HTML, XML, JSON등

- 대표적인 API 서비스 목록
  - Youtube API, Naver Papago API, Kaka Map API,



#### REST

- REpresentational State Transfer
- API Server를 개발하기 위한 일종의 소프트웨어 설계 방법론
  - 2000년 로이 필딩의 박사학위 논문에서 처음으로 소개된 후 네트워킹 문화에 널리 퍼짐
- 네트워크 구조(Network Architecture)원리의 모음
  - 자원을 정의하고 자원에 대한 주소를 지정하는 전잔적인 방법
- REST 원리를 따르는 시스템을 RESTful이란 용어로 지칭한다
- 자원을 정의하는 방법에 대한 고민
  - ex) 정의된 자원을 어디에 위치 시킬것인가



- REST의 자원과 주소의 지정 방법
  1. 자원
     - URI
  2. 행위
     - HTTP Method
  3. 표현
     - 자원과 행위를 통해 궁극적으로 표현되는 (추상화된) 결과물
     - JSON으로 표현된 데이터를 제공

-

- JSON

  - JSON(JavaScript Object Notation)

    - JSON is a lightweight data-interchange format

    - JavaScript 의 표기법을 따른 **단순 문자열**

- 특징
  - 사람이 읽거나 쓰기 쉽고 기게가 파싱(해석, 분석)하고 만들어내기 쉬움
  - 파이썬의 dictionary, 자바스크립트의 object처럼 C계열어가 갖고있는 자료 구조
  - 쉽게 변화할 수 있는 key-value 형태의 구조



#### REST의 핵심 규칙

1. '정보'는 URI로 표현한다.
2. 자원에 대한 '행위'는 HTTP Method로 표현(GET-R, POST-C, PUT-U, DELETE-D)



- 설계 방법론은 지키지 않았을 때 잃는 것보다 지켰을 때 얻는 것이 훨씬 많다.
  - 단, 설계 방법론을 지키지 않더라도 동작 여부에 큰 영향을 미치지는 않는다.



#### RESTful API

- REST 원리를 따라 설계한 API
- RESTful services, 혹은 simply REST services라고도 부른다.



- 프로그래밍을 통해 클라이언트의 요청에 JSON 을 응답하는 서버를 구성
  - 지금까지 사용자의 입장에서 썼던 API를 제공자의 입장이 되어 개발해보기



#### bash창 

``` bash
pip install django-extensionds
pip install django-seed
pip install django==3.2
pip inpstall djangorestframework
pip freeze > requirements.txt
```

#### settings.py

``` python
# INSTALLED_APPS = 
    'django_extensions',
    'rest_framework',
    'django_seed',
]
```



- migrate 하기 (DB 생성)

#### bash

``` bash
pip install psycopg2
python psycopg2 seed articles --number=20
python manage.py createsuperuser
```

- 장고 seed는 article 정보를 이용해서 값들을 랜덤하게 넣어준다. 

- createsuperuser



























---



## 🥔 Response

- HTML 파일(문서) 대신 JSON 파일을 사용자에게 보여줄 것이다.
- JSON 문서를 주는 RESTfull한 API 서버를 만들어볼 예정.
- 'JSON형태로 게시물을 어떻게 응답할 수 있을까'

#### Init Project

- 제공된 00_JSON_response 프로젝트로 진행
- 가상환경 설정 및 패키지 설치

``` bash
python manage.py seed articles --number=20
# 데이터 20개를 넣는다.
# DB에서 확인이 가능하다.
```

- return에 JsonResponse라는 함수를 호출하고 있다. (from django.http.response import JsonResponse)



#### Response - JsonResponse

- Content-Type , entity header
  - 데이터의 media type(MIME type, content type)을 나타내기 위해 사용됨
  - 응답 내에 있는 컨텐츠의 컨텐츠 유형이 실제로 무엇인지 클라이언트에게 알려준다.



#### JsonResponse ojbects

- JSON-encoded response를 만드는 HttpResponse의 서브 클래스

- "JSON"으로 인코딩된 객체를 준다(핵심)

- "safe" parameter

  - True(기본값)

  - dict 이외의 객체를 **직렬화(Serialization)**하려면 False로 설정해야 한다.

    ``` python
    response = JsonResponse({'foo':'bar'})
    response = JsonResponse([1, 2, 3], safe=False)
    ```

    

#### Serialization

- '직렬화'

- 데이터 구조나 객체 상태를 동일하거나 다른 컴퓨터 환경에 저장하고, 나중에 재구성할 수 있는 포맷으로 변환하는 과정



- Serializers in Django
  - Queryset 및 Model Instance와 같은 복잡한 데이터를 JSON, XML 등의 유형으로 쉽게 변환할 수 있는 Python 데이터 타입으로 만들어줌.

- Django의 내장 HttpResponse를 활용한 JSON 응답

  ```python
  def article_json_2(request):
      articles = Article.objects.all()
      data = seializers.serialize('json', articles)
      return HttpResponse(data, content_type='application/json')
  ```

  - articles는 쿼리셋으로 json으로 변환하기 위해 serializers(내장 모듈)를 이용하여 직렬화 시킨다
  - 응답시 content_type은 'application/json'이다.
  - from django.core import serializers

- Django의 내장 HttpResponse를 활용한 JSON 응답 객체
- 주어진 모델 정보를 활용하기 때문에 이전과 달리 필드를 개별적으로  직접 만들어 줄 필요 없음(딕셔너리를 만들지 않았음)
  - model, pk, fields라는 세개의 키 값이 따로 분리되서 보인다.

- **Django REST framework(DRF)** 라이브러리를 사용한 JSON 응답

  - rest한 서버를 만들기 위해 라이브러리를 제공해준다.
  - 장고로 API 서버를 짤 때 무조건 사용하는 라이브러리다.

- 설치과정확인

  ```bash
  $ pip install djangorestframework
  ```

  ```python
  # settings.py
  
  INSTALLED_APPS = [
      #,,,
      'rest_framework',
  ]
  ```

  ``` python
  @api_view()
  def article_json_3(request):
      articles = Article.objects.all()
      serializer = ArticleSerializer(articles, many=True)
      return Response(serializer.data)
  ```

  - **ArticleSerializer** 클래스 

    - from .serializers import ArticleSerializer (serializers 모듈안에 있는 클래스)

  - serializers.py 살펴보기

    ``` python
    from rest_framework import serializers
    from .models import Article
    
    class ArticleSerializer(serializers.ModelSerializer):
        class Meta:
            model = Article
            fields = '__all__'
    ```

    - DRF라이브러리가 장고에서 기본적으로 사용하는 모델폼의 구조와 똑같이 맞춰놓은것 

      







## 🥔 Single Model

** 서버에서 JSON을 만들어 주는 것 ** 

#### DRF with Single Model

- 단일 모델의 data를 직렬화(serialization)하여 JSON으로 변환하는 방법에 대한 학습
- 단일 모델을 두고 CRUD 로직을 수행 가능하도록 설계
- API 개발을 위한 핵심 기능을 제공하는 도구 활용
  - DRF built-in form
  - Postman - 요청과 응답을 포트스맨을 사용할 것이다. 



#### [참고] Postman

- API를 구축하고 사용하기 위해 여러 도구를 제공하는 API 플래솜
- 설계, 테스트, 문서화 등의 도구를 제공함으로써 API를 더 빠르게 개발 및 생성할 수 있도록 돕는다.



#### ModelSerializer

- 모델 필드에 해당하는 필드가 있는 Serializer 클래스를 자동으로 만들 수 있는 shortcut
- 아래 핵심 기능을 제공한다.
  1. 모델 정보에 맞춰 자동으로 필드 생성
  2. serilaizer에 대한 유효성 검사기를 자동으로 생성
  3. .create() & .update()의 간단한 기본 구현이 포함됨

- Model의 필드를 어떻게 '직렬화'할 지 설정하는 것이 핵심
- 이 과정은 Django에서 Model의 필드를 설정하는 것과 동일하다.





## 🥔1:N Relation

