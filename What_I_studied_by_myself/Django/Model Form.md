

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

### Intro

- Django Form을 사용하다보면 Model에 정의한 필드를 유저로 부터 입력받기 위해 Form에서 Model 필드를 재정의 하는 행위가 중복될 수 잇다.
- 그래서 Django는 **Model을 통해 Form 클래스**를 만들 수 있는 **ModelForm**이라는 Helper를 제공한다.



## Model Form

- **Model**을 통해 **Form Class를 만들 수 있는** Helper
- 일반 Form Class와 완전히 같은 방식(객체 생성)으로 view에서 사용가능



### ModelForm 선언하기

```python
#articles/forms.py

from django import forms
from .models import Article

class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        fields = '__all__'
       # exclude = ('users',)
```

- Meta라는 클래스를 작성한다.
- forms 라이브러리에서 파생된 ModelForm 클래스를 상속받는다.
- 정의한 클래스 안에 **Meta 클래스**를 선언하고, **어떤 모델을 기반**으로 Form을 작성할 것인지에 대한 정보를 Meta 클래스에 지정한다.



### Meta Class

- Model의 정보를 작성하는 곳
- ModelForm을 사용하는 경우 사용할 모델이 있어야 하는데 Meta Class가 이를 구성한다.
  - 해당 Model에 정의한 field 정보를 Form에 적용하기 위함이다



### ModelForm이 쉽게 해주는 것

- 모델필드 속성에 맞는 HTML element 표현
- 이를 통해 받은 데이터를 View함수에서 유효성 검사를 할 수 있도록 한다.



---



#### Create view 수정

``` python
# articles/views.py

def create(request):
    form = ArticleForm(request.POST)
    if form.is_valid():
        article = form.save()
        return redirect('articles:detail', article.pk)
    return redirect('articles:new')
```

- ArticleForm으로부터 데이터를 받는다. (html의 form.as_p)
- ArticleForm(), 괄호 내에 입력받은 데이터를 작성한다. => ArticleForm(request.POST)



#### is_valid() method

- 유효성 검사를 실행하고, 데이터가 유효한지 여부를 boolean 으로 반환한다.
- 데이터 유효성 검사를 보장하기 위한 많은 테스트에 대해 Django는 is_valid()를 제공한다.



#### The save() method

- Form에 바인딩 된 데이터에서 데이터베이스 객체를 만들고 저장한다.
- ModelForm의 하위 클래스는 기존 모델 인스턴스를 키워드 인자 instance로 받아들일 수 있다.
  - 이것이 제공되면 save()는 해당 인스턴스를 수정(UPDATE)
  - 제공되지 않은 경우 save()는 지정된 모델의 새 인스턴스를 만든다(CREATE)
- Form의 유효성이 확인되지 않은 경우 save()를 호출하면 form.errors를 확인하여 에러확인가능

``` python
# CREATE A FORM INSTANCE FROM POST DATA
form = ArticleForm(request.POST)

#CREATE
new_article = form.save()

# UPDATE
article = Article.objects.get(pk=1)
form = ArticleForm(request.POST, instance=article)
form.save()
```



### views.py의 격변

``` python
def create(request):
    if request.method == 'POST':
        # create view함수
        form = ArticleForm(request.POST)
        if form.is_Valid():
            article = form.save()
            return rendirect('aritlces:detail', article.pk)
    else:
        form = ArticleForm()
    context = {
        'form' : form
    }
    return render(request, 'articles/create.html', context)
```

```python
def update(request, pk):
    article = Article.objects.get(pk=pk)
    if request.method == 'POST':
        form = ArticleForm(request.POST, instance=article)
        if form.is_valid():
            article = form.save()
            return redirect('articles:detail', article.pk)
    else:
        form = articleForm(instance=article)
    context = {
        'article' : article,
        'form' : form,
    }
    return render(request, 'articles/update.html',context)
```

```python
def delete(request, pk):
    article = Article.objects.get(pk=pk)
    if request.method == 'POST':
        article.delete()
        return redirect('article:index')
   	else:
        return redirect('article:detail', article.pk)
```



### forms.py의 파일 위치

- Form class는 forms.py뿐만 아니라 다른 어느 위치에 두어도 상관없음
- 하지만 되도록 app폴더/forms.py에 작성하는 것이 일반적인 구조



### form과 ModelForm의 비교

- Form
  - 어떤 Model에 저장해야 하는 지 알 수 없으므로 유효성 검사 이후 cleaned_data 딕셔너리를 생성
  - cleaned_data 딕셔너리에서 데이터를 가져온 후 .save() 호출해야 한다.
  - Model에 연관되지 않은 데이터를 받을 때 사용한다.
- ModelForm
  - Django가 해당 model에서 양식에 필요한 대부분의 정보를 이미 정의
  - 어떤 레코드를 만들어야 할 지 알고 있으므로 바로 .save()호출이 가능하다.

