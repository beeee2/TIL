# Review

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

- 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터 처리기능인 Create(생성), Read(읽기), Update(갱신), Delete(삭제)를 묶어서 일컫는 말 
- **Article.objects.all()**
  - DB에 **인스턴스 객체를 얻기 위한 쿼리문**. 레코드가 하나만 있으면 인스턴스 객체로, 두 개 이상이면 쿼리셋으로 리턴한다.

- Create

  1. 인스턴스 생성 후 인스턴스 변수 설정

  2. 초기 값과 함께 인스턴스 생성

     ``` bash
     >>> article = Article(title='second', content='django!!')
     >>> article.save()
     >>> Article.objects.all() 
     <QuerySet [<Article: Article object (1)>, <Article: Article object (2)>]>
     ```

  3. 인스턴스를 생성하지 않고 바로 쿼리 표현식 리턴 - QuerySet API - create() 사용한다.

     ``` bash
     >>> Article.objects.create(title='third', content='django!')
     <Article: Article object(3)>
     ```

  - CREATE 관련 메서드
    - save() 메서드
      - Saving objects
      - 객체를 데이터베이스에 저장한다
      - 데이터 생성 시 save() 호출하기 전에는 객체의 ID 값이 무엇인지 알 수 없다.
        - ID 값은 Django가 아니라 DB에서 계산되기 때문이다.
      - 단순히 모델을 인스턴스화 하는 것은 DB에 영향을 미치지 않기 때문에 반드시 save가 필요하다.

- READ

  - QuerySet API method를 사용해 다양한 조회를 하는 것이 중요하다
  - QuerySet API method는 크게 2가지로 분류된다.
    1. Methods that **return new querysets**
    2. Methods that **do not reutrn querysets**
  - all() : 현재 QuerySet의 복사본을 반환
  - get() : 주어진 lookup 매개변수와 일치하는 객체를 반환
    - 객체를 찾을 수 없으면 DoesNotExist예외를 발생시키고, 둘 이상의 객체를 찾으면 MultipleObjectsReturned 예외를 발생시킨다.
    - 위와같은 특징을 가지고 있기 때문에 primary key와같이 고유성을 보장하는 조회에서 사용해야 한다.

  - filter()
    - 주어진 lookup 매개변수와 일치하는 객체를 포함하는 새 QuerySet을 반환한다.
    - 검색이 안 될 경우 빈 쿼리셋을 반환한다.

- UPDATE

  ``` bash
  >>> article = Article.objects.get(pk=1)
  >>> article.title
  'first'
  
  >>> article.title = 'byebye'
  >>> article.save()
  
  >>> article.title
  'byebye'
  ```

  - article 인스턴스 객체의 인스턴스 변수의 값을 변경 후 저장한다.

- DELETE

  - delete()
  - QuerySet의 모든 행에 대해 SQL 삭제 쿼리를 수행하고, 삭제된 객체 수와 객체 유형당 삭제 수가 포함된 딕셔너리를 반환한다.

  ``` bash
  >>> article = Article.objects.get(pk=1)
  
  >>> article.delete()
  (1, {'article.Article' : 1})
  ```

- Field lookups

  - 조회 시 특정 검색 조건을 지정한다.
  - QuerySet 메서드 filter(), exclude() 및 get() 에 대한 키워드 인수로 지정된다.
  - 사용예시 )
    - Article.objects.filter(pk__gt=2), pk가 2보다 큰 친구들을 조회하겠다는 의미
    - Article.objects.filter(content__contains='ja'), 'ja'라는 글자를 포함하는 content 게시물을 조회하겠다는 의미

---



# Model Form

## Django Form Class





## Model Form



## Rendering fields manually
