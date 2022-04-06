# Model Form



## Review

``` python
class Article(modles.Model):
    title = models.CharField(max_length=10)
    content = models.TextField()
```

- 각 모델은 django.models.Model 클래스의 서브 클래스로 표현된다.

- models 모듈을 통해 어떠한 타입의 DB 컬럼을 정의할 것인지 정의
  - 각 필드는 클래스 속성으로 지정되어 있으며, 각 속성은 각 데이터베이스의 열에 매핑

#### Migrations

- Django가 model에 생긴 변화를 반영하는 방법
- Migration 실행 및 DB 스키마를 다루기 위한 몇 가지 명령어
  - makemigrations, migrate, sqlmigrate, showmigrations

#### Migrations의 주요 3단계

1. models.py
   - model의 변경사항 발생 시 
2. $ python manage.py makemigrations
   - migrations 파일 생성
3. $ python manage.py migrate
   - DB 반영(모델과 DB의 동기화)



### Database API

#### DB API

- DB를 조작하기 위한 도구
- Django가 기본적으로 ORM을 제공함에 따른 것으로 DB를 편하게 조작할 수 있도록 돕는다.
- Model을 만들면 Django는 객체들을 만들고 읽고 수정하고 지울 수 있는 database-abstract API를 자동으로 만든다.

- database-abstract API 혹은 database-access API라고도 한다.

#### Making Queries

- Class Name.Manager.QuerySet API

- Manager
  - Django 모델에 데이터베이스 query 작업이 제공되는 인터페이스
  - 기본적으로 모든 Django 모델 클래스에 objects라는 Manager를 추가한다.
- QuerySet
  - 데이터베이스로부터 전달받은 객체 목록
  - queryset안의 객체 0개, 1개 혹은 여러 개일 수 있다.
  - Queryset 을 통해 데이터베이스로부터 조회, 필터, 정렬 등을 수행할 수 있다.



### CRUD

