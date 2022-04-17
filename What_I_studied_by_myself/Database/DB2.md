# 🌱DB 02

## ✅ Foreign Key

### Foreign Key

- 외래 키(외부 키)
- 관계형 데이터베이스에서 한 테이블의 필드 중 다른 테이블의 행을 식별할 수 있는 키
- 참조하는 테이블에서 속성(필드)에 해당하고, 이는 참조되는 테이블의 기본 키(Primary Key)를 가리킨다.
- 참조하는 테이블의 외래 키는 참조되는 테이블 행 1개에 대응된다.
  - 이 때문에 참조하는 테이블에서 참조되는 테이블의 존재하지 않는 행을 참조할 수 없다.
- 참조하는 테이블의 행 여러 개가 참조되는 테이블의 동일한 행을 참조할 수 있다.



#### Foreign Key의 예시

- 하나의 게시글과 댓글간의 모델 관계(1:N 관계)
  - **1:N 관계**에서 **외래키는 N의 역할을 하는 모델**이 가지게 된다.

#### Foreign Key의 특징

- 키를 사용하여 부모 테이블의 유일한 값을 참조(**참조 무결성**)

- 외래 키의 값이 반드시 부모 테이블의 **기본 키일 필요는 없지만 유일한 값**이어야 한다.
  - 보통 부모 테이블의 pk(id)가 기본 키값의 역할을 수행한다.

#### [참고] 참조 무결성

- 데이터베이스 관계 모델에서 관련된 2개의 테이블 간의 일관성을 말한다.
- 외래 키가 선언된 테이블의 외래 키 속성(열)의 값은 그 테이블의 부모가 되는 테이블의 기본 키 값으로 존재해야 한다

#### ForeignKey

- A many-to-one relationshop
- 2개의 위치 인자가 반드시 **필요**
  1. **참조하는 model class**
  2. **on_delete 옵션**
- migrate 작업 시 외래키 필드 이름에 _id를 추가하여 데이터베이스 열 이름을 만든다.
  - 시험문제 ) 'Comment 모델은 외래키 article_id를 포함합니다.' 라고 적혀있다면 외래키 필드명은 article이다.

#### comment 모델 정의하기

``` python
# articles/models.py
# 댓글은 articles 앱에서 구현한다.(게시판 요소)

class Comment(models.Model):# Comment 모델(모델 클래스)은 다음과 같은 필드들을 가진다.
    article = models.ForeignKey(Article, on_delete=models.CASCADE)
    # 외래키와 관련된 변수는, 1:N관계에서 참조되는 모델의 단수형 소문자로 작성한다.(M:N관계에서는 복수형으로 작성한다.)
    # 외래키 필드, ForeignKey필드를 사용한다.(Field가 붙지 않음에 유의한다.)
    # 두개의 인자를 사용한다. 참조하는 모델과 on_delete
    content = models.CharField(max_length=200)
    # 댓글의 내용
    created_at = models.DateTimeField(auto_now_add=True)
    # 생성일
    updated_at = models.DateTimeField(auto_now=True)
    # 수정일
    
    def __str__(self):
        return self.content
    # 객체 표현방식
```



#### ForeignKey arguments - 'on_delete'

- 외래 키가 참조하는 객체가 사라졌을 때 외래 키를 가진 객체를 어떻게 처리할 지를 정의한다.
- Database Integrity(데이터 무결성)을 위해서 매우 중요한 설정
- on_delete 옵션에 사용가능한 값들
  - CASECADE : 부모 객체(참조 된 객체)가 삭제 됐을 때 이를 참조하는 객체도 삭제
  - PROTECT, SET_NULL, SET_DEFAULT, SET(), DO_NOTHING, RESTRICT

#### [참고] 데이터 무결성

- 데이터의 정확성과 일관성을 유지하고 보증하는 것을 가리키며, 데이터베이스나 RDBMS 시스템의 중요한 기능

- 무결성 제한의 유형
  1. 개체 무결성(Entity integrity)
     - PK의 개념과 관련
     - 모든 테이블이 PK를 가져야 하며 PK로 선택된 열은 고유한 값이어야 하고 빈 값은 허용치 않음을 규정
  2. 참조 무결성(Referential integrity)
     - FK(외래 키) 개념과 관련
     - FK 값이 데이터 베이스의 특정 테이블의 PK 값을 참조하는 것
  3. 범위(도메인) 무결성(Domain  integrity)
     - 정의된 형식(범위)에서 관계형 데이터 베이스의 모든 컬럼이 선언되도록 규정

#### 데이터베이스의 ForeignKey 표현

- 만약 ForeignKey 인스턴스를 abcd로 생성했다면 abcd_id로 만들어진다
- 하지만 명시적인 모델관계 파악을 위해 참조하는 클래스 이름의 소문자(단수형)으로 작성하는 것이 바랍직하다.(1: N)

#### 댓글 생성하기

1. ``` bash
   $python manage.py shell_plus
   ```

2. ``` bash
   comment = Comment()
   # Comment 클래스를 통해 comment라는 인스턴스 생성, 
   ```

3. ``` bash
   comment.content = 'First comment'
   comment.save()
   # NOT NULL cONSTARINT Failed(외래키 값이 비어있음)
   ```

4. ``` bash
   # 게시글 먼저 빠르게 생성
   article = Article.objects.create(title='title', content='content')
   ```

   - comment.article_id 와 같이 콕 찝을 경우, aomment.article_id = article.pk로 작성하여야 한다.
   - comment.article = article로 사용할 수 있다.

5. ``` bash
   comment.article = article
   ```

6. ``` bash
   comment.save()
   ```

7. ```bash
   comment.pk
   ```

8. ``` bash
   comment.article.content
   # 외래키를 가지고 있는 입장에서는 참조가 아주 간단하게 된다.
   ```



#### admin site에서 작성된 댓글 확인

``` python
# articles/admin.py

from .models import Article, Comment

admin.stie.register(Comment)
```

``` bash
$python manage.py createsuperuser
```



#### 1:N 관계 related manager

- 역참조('comment_set')
  - Article(1) - > Comment(N)
  - article.comment 형태로는 사용할 수  없고, article.comment_set manager가 생성된다.
    - 댓글을 출력할 수  있다.
  - 게시글에 몇 개의 댓글이 작성 되었는지 Django ORM이 보장할 수 없기 때문이다.
    - article은 comment가 있을 수도, 없을 수도 있다.
    - 실제로 Article 클래스에는 Comment 와의 어떠한 관계도 작성되어 있지 않다.
- 참조('article')
  - Comment(N) -> article(1)
  - 댓글의 경우 어떠한 댓글이든 반드시 자신이 참조하고 있는 게시물이 있으므로, comment.article과 같이접근할 수 있다.
  - 실제 ForeignKey 또한 Comment 클래스에서 작성된다.

#### ForeignKey arguments - 'related_name'

- 역 참조시 사용할 이름('model_set' manager)을 변경할 수 있는 옵션

  ``` python
  # articles/models.py
  
  class Comment(models.Model):
      article= models.ForeignKey(Article, on_delete=models.CASCADE, related_name='contents')
  ```

- 위와 같이 변경하면 article.comment_set은 더이상 사용할 수 없고, article.comments로 대체된다.

  - article.comment_set.all() -> article.comments.all()

- [주의] 역참조 시 사용할 이름 수정 후, migration 과정이 필요하다.

- [주의] 1:N에서 굳이 명칭을 바꾸지 않는다. (comments_set 그냥 사용하도록 하자.)





### Comment CREATE

#### CommentForm 작성

``` python
# articles/forms.py
from .models import Article, Comment

class CommentForm(forms.ModelForm):
    class Meta:
        model = Comment
        fields = '__all__'
```

#### detail 페이지에서 CommentForm 출력

``` python
from .forms import ArticleForm, CommentForm

@require_safe
def detail(request, pk):
    article = get_object_or_404(Article, pk=pk)
    comment_form = CommentForm()
    context = {
        'article' : article,
        'comment_form' : comment_form,
    }
    return render(request, 'articles/detail.html', context)
```

``` django
<!-- articles/detail.html -->

{% extends 'base.html' %}

{% block content %}
<!-- ... ->
<a href="{% url 'articles:index' %}">back</a>
<hr>
<form action="" method="POST">
	{% csrf_token %}
	{{ comment_form }}
	<input type="submit">
</form>
{% endblock %}

```

- 두 번째 글에 댓글을 달고 싶은데 그냥 위와 같이 작성했을 때 detail  페이지에서 어느 게시물에 댓글을 작성할 지 선택할 수 있다. 이상하다. 필드 출력을 수정할 필요가 있다.

``` python
# articles/forms.py

class CommentForm(forms.ModelForm):
    class Meta:
        model = Comment
        exclude = ('articles',)
        # 사용자로부터 외래키의 값을 전달 받지 않기 때문에 이를 제외한다.
        # 이렇게 되면 views.py에서 별도로 article을 받아줘야 한다.
```

#### 댓글 작성 로직

``` python
# articles/urls.py

app_name = 'articles'
urlpatterns = [
    # ...
    path('<int:pk>/comments/', views.comments_create, name='comments_create'),
] # 어떤 게시글에 작성되어야 하는 지 알아야하기때문에 게시글의 pk값이 필요하다.
```

``` django
<!-- articles/detail.html -->
<form action="{% url 'articles:comments_create' article.pk %}" method="POST">
    {% csrf_token %}
    {{comment_form}}
    <input type="submit">
</form>
```

``` python
# articles/views.py

@require_POST
def comments_create(request, pk):
    if request.user.is_authenticated:
        article = get_object_or_404(Article, pk=pk)
        comment_form = CommentForm(request.POST)
        if comment_form.is_valid():
            comment = comment_form.save(commit=False)
            # commit=False, 두 번의 save가 가능한 이유
            # commit의 기본 값은 True였다. 
            # commit을 실제 데이터베이스의 저장은 하지 않고 instance만 생성되게 한다.
            comment.article = article
            # 조회한 article의 값을 넣어줘야 한다.
            comment.save()
        return redirect('articles:detail', article.pk)
    return redirect('accounts:login')


```



#### The 'save()' method

- save(commit=False)
  - Create, but don't save the new instance
  - 아직 **데이터베이스에 저장되지 않은 인스턴스**를 반환
  - 저장하기 전에 **객체에 대한 사용자 지정 처리를 수행할 때 유용**하게 사용한다.
  - commit의 기본값은 True
  - commit은 ModelForm의 메서드(상속받았기 때문이다.)





### Comment READ

#### 댓글 조회

``` python
@require_safe
def detail(request, pk):
    article = get_object_or_404(Article, pk=pk)
    comment_form = CommentForm()
    # 조회한 article의 모든 댓글을 조회(역참조)
    comments = article.comment_set.all()
    context = [
        'artlcle' : article,
        'comment_form' : comment_form,
        'comments' : commtens,
    ]
    return render(request, 'articles:detail.html', context)
```

``` html
<h4>
    댓글 목록
</h4>
{% for comment in comments %}
	<li>{{comment.content}}</li>
{% endfor %}
```





### Comment DELETE

#### 댓글 삭제

``` python
# articles > urls.py
urlpatterns = [
    # ...
    path('<int:article_pk>/comments/<int:comment_pk>/delete', views.comment_delete, name='comment_delete')
]
```

``` python
# articles > views.py
@require_POST
def comment_delete(request, article_pk , comment_pk): # article_pk를 variable routing으로 받아서 사용가능
    if request.user.is_authenticated:
        comment = get_object_or_404(Commen, pk=comment_pk)
        # article = comment.article.pk, 참조해서 얻을 수 있고 return의 두번째 인자로 쓸 수 있다.
        comment.delete()
    return redirect('articles:detail', article_pk)
        # URL 구조의 일관성과 통일성을 위해서 
       
```

``` html

{% for comment in comments %}
<li>
	{{comment.content}}
    <form action="{% url 'articles:comment_delete' article.pk comment.pk%}" method="POST">
        {% csrf_token %}
        <input type="submit" value="삭제">
    </form>
</li>
{% endfor %}
```



### Comment 추가사항

#### 댓글 개수 출력하기

``` html
<h4>
    댓글 목록
</h4>
{% if comments %}
	<p>
        <b>{{comments|length}}개의 댓글이 있습니다.</b>
</p>
{% endif %}
```

- {{comments:|length}}
- {{article.comment_sel.all|length}}
- {{comments.count}}

#### 댓글이 없는 경우 대체 컨텐츠 출력(DTL의 for-empty 태그 활용)

``` html
<ul>
    {% for comment in comments%}
    	<li>
    		{{comment.content}}
            <form action=""{% url 'articles:comment_delete' article.pk comment.pk %}"" method="POST" class="d-nline">
                {% csrf_tocken %}
                <input type="submit" value="DELETE">
            </form>
    	</li>
    {% empty %}
    	<p>
            댓글이 없습니다.
    </p>
    {% endfor %}
</ul>
```







---

## ✅ Customizing authentication in Django

### Substituting a custom User model

#### User 모델 대체하기

- 일부 모델에서는 Django의 내장 User 모델이 제공하는 인증 요구사항이 적절하지 않을 수 있다.
  - ex) username 대신 email을 식별 토큰으로 사용하는 것이 더 적합한 사이트
- Django는 User를 참조하는데 사용하는 AUTH_USER_MODEL값을 제공하여, default user model을 재정의(override)할  수 있도록 한다
- Djanggo는 새 프로젝트를 시작하는 경우 기본 사용자 모델이 충분하더라도, 커스텀 유저 모델을 설정하는 것을 강력하게 권항
  - 단, 프로젝트의 모든 migrations 혹은 첫 migrate를 실행하기 전에 이 작업을 마쳐야 한다.



#### AUTH_USER_MODEL

- User를 나타내는데 사용하는 모델
- 프로젝트가 진행되는 동안 변경할 수 없음
- 프로젝트 시작 시 설정하기 위한 것이며 참조하는 모델은 첫번째마이그레이션에서 사용할 수 있어야 한다.
- 기본 값 : 'auth.User' (auth앱의 User 모델)



- [참고] 프로젝트 중간(mid-project)에 AUTH_USER_MODEL 변경하기
  - 모델 관계에 영향을 미치기 때문에 훨씬 더 어려운 작업이 필요
  - 즉, 중간 변경은 권장하지 않으므로 초기에 설정하는 것을 권장



#### Custom User 모델 정의하기

- 관리자 권한과 함께 완전한 기능을 갖춘 User 모델을 구현하는 기본 클래스인 AbstractUser를 상속받아 새로운 User 모델 작성

``` python
# accounts/models.py

from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
    pass
```

- settings.py에 수정(우리가 커스텀한 유저 클래스로 변경)

``` python
AUTH_USER_MODEL = 'accounts.User'
```

- 프로젝트 중간에 진행했기 때문에 데이터베이스를 초기화 한 후 마이그레이션을 진행

  - 초기화 방법

    1. db.sqlite3 파일 삭제

    2. migrtaions 파일을 모두 삭제(파일명에 숫자가 붙은 파일만 삭제)

       ``` bash
       $ python manage.py makemigrations
       $ python manage.py migrate
       ```

- admin 페이지에서 사용자(들) 항목(회원정보)이 사라졌다. 새로운 User로 대체하면서 빠지게 되었다.

  - 해결방법, 장고문서참조, substituting-a-custom-user-model

  ``` python
  # articles/admin.py
  
  from django.contrib import admin
  from django.contrib.auth.admin import UserAdmin
  from .models import User
  
  admin.site.register(User, UserAdmin)
  ```

  







### Custom user & Built-in auth forms

- User 모델이 빠지면서 어디선가 어긋나는 부분이 생길것이다

1. 회원가입 시도 후 아래와 같은 에러 발생 :
   - AttributeError at /accounts/signup
   - 회원가입에서 사용하는 폼은 UserCreationForm -> ModelForm,-> 클래스 메타 정도가 있음 -> 모델이 작성되어 있다.  
   - UserCretaionForm과 UserChangeForm은 기존 내장 User 모델을 사용한 ModelForm이기 때문에 커스텀 User 모델로 대체해야 한다.



#### Custom Built-in Auth Forms(1/2)

기존 User 모델을 사용하기 때문에 커스텀 User모델로 다시 작성하거나 확장해야 하는 forms

- UserCreationForm
- UserChangeForm

``` python
# accounts/forms.py
import django.contrib.auth.forms import UserChangeForm,UserCreationForm
from django.contrib.auth import get_user_model
# 현재 장고모델에 활성화된 유저 모델을 리턴한다.
# 유저는 직접 참조하지않는다.
# 단순 유저모델을 돌려주는게 아니라 현재 장고 프로젝트에 활성화된 유저모델을 리턴한다.

class CustomUserChangeForm(userChangeForm):
    class Meta:
        model = get_user_model()
        fields = ('email', 'first_name', 'last_name')
        
class CustomUserCreationForm(UserCreationForm): 
    class Meta:
        model = get_user_model()
```

#### Custom Built-in Auth Forms(2/2)

- 이처럼 커스텀 User 모델이 AbstractUser의 하위 클래스인 경우 다음과 같은 방식으로 form을 확장

  ``` python
  from django.contrib.auth.forms import UserCreationForm
  from myapp.models import CustomUser
  
  class CustomUserCreationForm(UserCreationForm):
      class Meta(UserCreationForm, Meta):
          model = CustomUser
          fields = UserCreationForm.Meta.fields + ('custom_field',)
  ```

  ``` python
  from django.contrib.auth.forms import UserChangeForm, useCreationForm
  
  class CustomuserCreationForm(UserCreationForm):
      class Meta(UserCreationForm.meta):
          model = get_user_model()
          fields = UserCreationsForm.Meta.fields + ('email',)
  ```



#### get_user_model()

- 현재 프로젝트에서 활성화된 사용자 모델을 반환
  - User 모델을 커스터마이징한 상황에서는 Custom User모델을 반한다.
- 이 때문에 Django는 User 클래스를 직접 참조하는 대신 django.contrib.auth.get_user_model()을 사용하여 참조해야 한다고 강조







## User - Article

### 1:N 관계설정 : User-Article

- 사용자는 여러 개의 게시글을 작성할 수 있다

- Article이 N, 1이 1이다.

``` python
# articles/models.py
from django.db import models
from django.conf import settings

class Article(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    title = models.CharField(max_length=10)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    
    def __str__(self):
        return self.title
```

- 외래키 변수명은 1:N관계에서 참조하는 모델이름의 소문자 단수형.
- settings.py에 AUTH_USER_MODEL = 'accounts.User'
- 외래키 user의 첫번째 인자로 User를 사용하면 안된다.(직접 키 참조 금지)
  - 간접적으로 user값을 리턴받아서 제공해야한다. get_user_model()또한 사용할 수 없다. 모델에서의 참조로 함수는 불가능하기 때문이다.



#### User 모델을 참조하는 방법

1. settings.AUTH_USER_MODEL

- return 값으로 문자열을 반환한다.
- User  모델에 대한 외래 키 또는 다대다 관계를 정의할 때 사용해야 한다.
- models.py에서 User모델을 참조할 때 사용한다.

2. get_user_model()

- return 값으로 object를 반환한다.

- 현재 활성화(active)된 User 모델을 반환한다.
  - 커스터마이징한 User 모델이 있을 경우는 Custom User 모델을, 그렇지 않으면 User를 반환한다.
  - User를 직접 참조하지 않는 이유
- models.py가 아닌 다른 모든 곳에서 유저 모델을 참조할 때 사용

#### User 모델에 대한 정리

- **models.py에서는 settings.AUTH_USER_MODEL**
- **models.py를 제외한 다른 모든 곳은 get_user_model()**





### 1:N 관계설정 : User-Comment

1. User와 Comment 간 모델 관계 정의 후 migrtaion

``` python
#articles/models.py
class Comment(models.Model):
    article = models.ForeignKey(Article, on_delete=models.CASCADE)
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    

```



2. User와 Comment 간 모델 관계 정의 후 migration

   - nulll 값이 허용되지 않는 user_id 필드가 별도의 값 없이 comment에추가되려 하기 때문이다.

   - 1을 입력 후 enter, 현재 화면에서 기본 값을 설정하겠다는 의미

   - 1을 입력 후 enter,

     기존 테이블에 추가되는 user_id 필드의 값을 1로 설정하겠다는 의미로 기존 댓글의 작성자가 모두 1번 user가 된다.































