# π±DB 02

## β Foreign Key

### Foreign Key

- μΈλ ν€(μΈλΆ ν€)
- κ΄κ³ν λ°μ΄ν°λ² μ΄μ€μμ ν νμ΄λΈμ νλ μ€ λ€λ₯Έ νμ΄λΈμ νμ μλ³ν  μ μλ ν€
- μ°Έμ‘°νλ νμ΄λΈμμ μμ±(νλ)μ ν΄λΉνκ³ , μ΄λ μ°Έμ‘°λλ νμ΄λΈμ κΈ°λ³Έ ν€(Primary Key)λ₯Ό κ°λ¦¬ν¨λ€.
- μ°Έμ‘°νλ νμ΄λΈμ μΈλ ν€λ μ°Έμ‘°λλ νμ΄λΈ ν 1κ°μ λμλλ€.
  - μ΄ λλ¬Έμ μ°Έμ‘°νλ νμ΄λΈμμ μ°Έμ‘°λλ νμ΄λΈμ μ‘΄μ¬νμ§ μλ νμ μ°Έμ‘°ν  μ μλ€.
- μ°Έμ‘°νλ νμ΄λΈμ ν μ¬λ¬ κ°κ° μ°Έμ‘°λλ νμ΄λΈμ λμΌν νμ μ°Έμ‘°ν  μ μλ€.



#### Foreign Keyμ μμ

- νλμ κ²μκΈκ³Ό λκΈκ°μ λͺ¨λΈ κ΄κ³(1:N κ΄κ³)
  - **1:N κ΄κ³**μμ **μΈλν€λ Nμ μ­ν μ νλ λͺ¨λΈ**μ΄ κ°μ§κ² λλ€.

#### Foreign Keyμ νΉμ§

- ν€λ₯Ό μ¬μ©νμ¬ λΆλͺ¨ νμ΄λΈμ μ μΌν κ°μ μ°Έμ‘°(**μ°Έμ‘° λ¬΄κ²°μ±**)

- μΈλ ν€μ κ°μ΄ λ°λμ λΆλͺ¨ νμ΄λΈμ **κΈ°λ³Έ ν€μΌ νμλ μμ§λ§ μ μΌν κ°**μ΄μ΄μΌ νλ€.
  - λ³΄ν΅ λΆλͺ¨ νμ΄λΈμ pk(id)κ° κΈ°λ³Έ ν€κ°μ μ­ν μ μννλ€.

#### [μ°Έκ³ ] μ°Έμ‘° λ¬΄κ²°μ±

- λ°μ΄ν°λ² μ΄μ€ κ΄κ³ λͺ¨λΈμμ κ΄λ ¨λ 2κ°μ νμ΄λΈ κ°μ μΌκ΄μ±μ λ§νλ€.
- μΈλ ν€κ° μ μΈλ νμ΄λΈμ μΈλ ν€ μμ±(μ΄)μ κ°μ κ·Έ νμ΄λΈμ λΆλͺ¨κ° λλ νμ΄λΈμ κΈ°λ³Έ ν€ κ°μΌλ‘ μ‘΄μ¬ν΄μΌ νλ€

#### ForeignKey

- A many-to-one relationshop
- 2κ°μ μμΉ μΈμκ° λ°λμ **νμ**
  1. **μ°Έμ‘°νλ model class**
  2. **on_delete μ΅μ**
- migrate μμ μ μΈλν€ νλ μ΄λ¦μ _idλ₯Ό μΆκ°νμ¬ λ°μ΄ν°λ² μ΄μ€ μ΄ μ΄λ¦μ λ§λ λ€.
  - μνλ¬Έμ  ) 'Comment λͺ¨λΈμ μΈλν€ article_idλ₯Ό ν¬ν¨ν©λλ€.' λΌκ³  μ νμλ€λ©΄ μΈλν€ νλλͺμ articleμ΄λ€.

#### comment λͺ¨λΈ μ μνκΈ°

``` python
# articles/models.py
# λκΈμ articles μ±μμ κ΅¬ννλ€.(κ²μν μμ)

class Comment(models.Model):# Comment λͺ¨λΈ(λͺ¨λΈ ν΄λμ€)μ λ€μκ³Ό κ°μ νλλ€μ κ°μ§λ€.
    article = models.ForeignKey(Article, on_delete=models.CASCADE)
    # μΈλν€μ κ΄λ ¨λ λ³μλ, 1:Nκ΄κ³μμ μ°Έμ‘°λλ λͺ¨λΈμ λ¨μν μλ¬Έμλ‘ μμ±νλ€.(M:Nκ΄κ³μμλ λ³΅μνμΌλ‘ μμ±νλ€.)
    # μΈλν€ νλ, ForeignKeyνλλ₯Ό μ¬μ©νλ€.(Fieldκ° λΆμ§ μμμ μ μνλ€.)
    # λκ°μ μΈμλ₯Ό μ¬μ©νλ€. μ°Έμ‘°νλ λͺ¨λΈκ³Ό on_delete
    content = models.CharField(max_length=200)
    # λκΈμ λ΄μ©
    created_at = models.DateTimeField(auto_now_add=True)
    # μμ±μΌ
    updated_at = models.DateTimeField(auto_now=True)
    # μμ μΌ
    
    def __str__(self):
        return self.content
    # κ°μ²΄ ννλ°©μ
```



#### ForeignKey arguments - 'on_delete'

- μΈλ ν€κ° μ°Έμ‘°νλ κ°μ²΄κ° μ¬λΌμ‘μ λ μΈλ ν€λ₯Ό κ°μ§ κ°μ²΄λ₯Ό μ΄λ»κ² μ²λ¦¬ν  μ§λ₯Ό μ μνλ€.
- Database Integrity(λ°μ΄ν° λ¬΄κ²°μ±)μ μν΄μ λ§€μ° μ€μν μ€μ 
- on_delete μ΅μμ μ¬μ©κ°λ₯ν κ°λ€
  - CASECADE : λΆλͺ¨ κ°μ²΄(μ°Έμ‘° λ κ°μ²΄)κ° μ­μ  λμ λ μ΄λ₯Ό μ°Έμ‘°νλ κ°μ²΄λ μ­μ 
  - PROTECT, SET_NULL, SET_DEFAULT, SET(), DO_NOTHING, RESTRICT

#### [μ°Έκ³ ] λ°μ΄ν° λ¬΄κ²°μ±

- λ°μ΄ν°μ μ νμ±κ³Ό μΌκ΄μ±μ μ μ§νκ³  λ³΄μ¦νλ κ²μ κ°λ¦¬ν€λ©°, λ°μ΄ν°λ² μ΄μ€λ RDBMS μμ€νμ μ€μν κΈ°λ₯

- λ¬΄κ²°μ± μ νμ μ ν
  1. κ°μ²΄ λ¬΄κ²°μ±(Entity integrity)
     - PKμ κ°λκ³Ό κ΄λ ¨
     - λͺ¨λ  νμ΄λΈμ΄ PKλ₯Ό κ°μ ΈμΌ νλ©° PKλ‘ μ νλ μ΄μ κ³ μ ν κ°μ΄μ΄μΌ νκ³  λΉ κ°μ νμ©μΉ μμμ κ·μ 
  2. μ°Έμ‘° λ¬΄κ²°μ±(Referential integrity)
     - FK(μΈλ ν€) κ°λκ³Ό κ΄λ ¨
     - FK κ°μ΄ λ°μ΄ν° λ² μ΄μ€μ νΉμ  νμ΄λΈμ PK κ°μ μ°Έμ‘°νλ κ²
  3. λ²μ(λλ©μΈ) λ¬΄κ²°μ±(Domain  integrity)
     - μ μλ νμ(λ²μ)μμ κ΄κ³ν λ°μ΄ν° λ² μ΄μ€μ λͺ¨λ  μ»¬λΌμ΄ μ μΈλλλ‘ κ·μ 

#### λ°μ΄ν°λ² μ΄μ€μ ForeignKey νν

- λ§μ½ ForeignKey μΈμ€ν΄μ€λ₯Ό abcdλ‘ μμ±νλ€λ©΄ abcd_idλ‘ λ§λ€μ΄μ§λ€
- νμ§λ§ λͺμμ μΈ λͺ¨λΈκ΄κ³ νμμ μν΄ μ°Έμ‘°νλ ν΄λμ€ μ΄λ¦μ μλ¬Έμ(λ¨μν)μΌλ‘ μμ±νλ κ²μ΄ λ°λμ§νλ€.(1: N)

#### λκΈ μμ±νκΈ°

1. ``` bash
   $python manage.py shell_plus
   ```

2. ``` bash
   comment = Comment()
   # Comment ν΄λμ€λ₯Ό ν΅ν΄ commentλΌλ μΈμ€ν΄μ€ μμ±, 
   ```

3. ``` bash
   comment.content = 'First comment'
   comment.save()
   # NOT NULL cONSTARINT Failed(μΈλν€ κ°μ΄ λΉμ΄μμ)
   ```

4. ``` bash
   # κ²μκΈ λ¨Όμ  λΉ λ₯΄κ² μμ±
   article = Article.objects.create(title='title', content='content')
   ```

   - comment.article_id μ κ°μ΄ μ½ μ°μ κ²½μ°, aomment.article_id = article.pkλ‘ μμ±νμ¬μΌ νλ€.
   - comment.article = articleλ‘ μ¬μ©ν  μ μλ€.

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
   # μΈλν€λ₯Ό κ°μ§κ³  μλ μμ₯μμλ μ°Έμ‘°κ° μμ£Ό κ°λ¨νκ² λλ€.
   ```



#### admin siteμμ μμ±λ λκΈ νμΈ

``` python
# articles/admin.py

from .models import Article, Comment

admin.stie.register(Comment)
```

``` bash
$python manage.py createsuperuser
```



#### 1:N κ΄κ³ related manager

- μ­μ°Έμ‘°('comment_set')
  - Article(1) - > Comment(N)
  - article.comment ννλ‘λ μ¬μ©ν  μ  μκ³ , article.comment_set managerκ° μμ±λλ€.
    - λκΈμ μΆλ ₯ν  μ  μλ€.
  - κ²μκΈμ λͺ κ°μ λκΈμ΄ μμ± λμλμ§ Django ORMμ΄ λ³΄μ₯ν  μ μκΈ° λλ¬Έμ΄λ€.
    - articleμ commentκ° μμ μλ, μμ μλ μλ€.
    - μ€μ λ‘ Article ν΄λμ€μλ Comment μμ μ΄λ ν κ΄κ³λ μμ±λμ΄ μμ§ μλ€.
- μ°Έμ‘°('article')
  - Comment(N) -> article(1)
  - λκΈμ κ²½μ° μ΄λ ν λκΈμ΄λ  λ°λμ μμ μ΄ μ°Έμ‘°νκ³  μλ κ²μλ¬Όμ΄ μμΌλ―λ‘, comment.articleκ³Ό κ°μ΄μ κ·Όν  μ μλ€.
  - μ€μ  ForeignKey λν Comment ν΄λμ€μμ μμ±λλ€.

#### ForeignKey arguments - 'related_name'

- μ­ μ°Έμ‘°μ μ¬μ©ν  μ΄λ¦('model_set' manager)μ λ³κ²½ν  μ μλ μ΅μ

  ``` python
  # articles/models.py
  
  class Comment(models.Model):
      article= models.ForeignKey(Article, on_delete=models.CASCADE, related_name='contents')
  ```

- μμ κ°μ΄ λ³κ²½νλ©΄ article.comment_setμ λμ΄μ μ¬μ©ν  μ μκ³ , article.commentsλ‘ λμ²΄λλ€.

  - article.comment_set.all() -> article.comments.all()

- [μ£Όμ] μ­μ°Έμ‘° μ μ¬μ©ν  μ΄λ¦ μμ  ν, migration κ³Όμ μ΄ νμνλ€.

- [μ£Όμ] 1:Nμμ κ΅³μ΄ λͺμΉ­μ λ°κΎΈμ§ μλλ€. (comments_set κ·Έλ₯ μ¬μ©νλλ‘ νμ.)





### Comment CREATE

#### CommentForm μμ±

``` python
# articles/forms.py
from .models import Article, Comment

class CommentForm(forms.ModelForm):
    class Meta:
        model = Comment
        fields = '__all__'
```

#### detail νμ΄μ§μμ CommentForm μΆλ ₯

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

- λ λ²μ§Έ κΈμ λκΈμ λ¬κ³  μΆμλ° κ·Έλ₯ μμ κ°μ΄ μμ±νμ λ detail  νμ΄μ§μμ μ΄λ κ²μλ¬Όμ λκΈμ μμ±ν  μ§ μ νν  μ μλ€. μ΄μνλ€. νλ μΆλ ₯μ μμ ν  νμκ° μλ€.

``` python
# articles/forms.py

class CommentForm(forms.ModelForm):
    class Meta:
        model = Comment
        exclude = ('articles',)
        # μ¬μ©μλ‘λΆν° μΈλν€μ κ°μ μ λ¬ λ°μ§ μκΈ° λλ¬Έμ μ΄λ₯Ό μ μΈνλ€.
        # μ΄λ κ² λλ©΄ views.pyμμ λ³λλ‘ articleμ λ°μμ€μΌ νλ€.
```

#### λκΈ μμ± λ‘μ§

``` python
# articles/urls.py

app_name = 'articles'
urlpatterns = [
    # ...
    path('<int:pk>/comments/', views.comments_create, name='comments_create'),
] # μ΄λ€ κ²μκΈμ μμ±λμ΄μΌ νλ μ§ μμμΌνκΈ°λλ¬Έμ κ²μκΈμ pkκ°μ΄ νμνλ€.
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
            # commit=False, λ λ²μ saveκ° κ°λ₯ν μ΄μ 
            # commitμ κΈ°λ³Έ κ°μ Trueμλ€. 
            # commitμ μ€μ  λ°μ΄ν°λ² μ΄μ€μ μ μ₯μ νμ§ μκ³  instanceλ§ μμ±λκ² νλ€.
            comment.article = article
            # μ‘°νν articleμ κ°μ λ£μ΄μ€μΌ νλ€.
            comment.save()
        return redirect('articles:detail', article.pk)
    return redirect('accounts:login')


```



#### The 'save()' method

- save(commit=False)
  - Create, but don't save the new instance
  - μμ§ **λ°μ΄ν°λ² μ΄μ€μ μ μ₯λμ§ μμ μΈμ€ν΄μ€**λ₯Ό λ°ν
  - μ μ₯νκΈ° μ μ **κ°μ²΄μ λν μ¬μ©μ μ§μ  μ²λ¦¬λ₯Ό μνν  λ μ μ©**νκ² μ¬μ©νλ€.
  - commitμ κΈ°λ³Έκ°μ True
  - commitμ ModelFormμ λ©μλ(μμλ°μκΈ° λλ¬Έμ΄λ€.)





### Comment READ

#### λκΈ μ‘°ν

``` python
@require_safe
def detail(request, pk):
    article = get_object_or_404(Article, pk=pk)
    comment_form = CommentForm()
    # μ‘°νν articleμ λͺ¨λ  λκΈμ μ‘°ν(μ­μ°Έμ‘°)
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
    λκΈ λͺ©λ‘
</h4>
{% for comment in comments %}
	<li>{{comment.content}}</li>
{% endfor %}
```





### Comment DELETE

#### λκΈ μ­μ 

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
def comment_delete(request, article_pk , comment_pk): # article_pkλ₯Ό variable routingμΌλ‘ λ°μμ μ¬μ©κ°λ₯
    if request.user.is_authenticated:
        comment = get_object_or_404(Commen, pk=comment_pk)
        # article = comment.article.pk, μ°Έμ‘°ν΄μ μ»μ μ μκ³  returnμ λλ²μ§Έ μΈμλ‘ μΈ μ μλ€.
        comment.delete()
    return redirect('articles:detail', article_pk)
        # URL κ΅¬μ‘°μ μΌκ΄μ±κ³Ό ν΅μΌμ±μ μν΄μ 
       
```

``` html

{% for comment in comments %}
<li>
	{{comment.content}}
    <form action="{% url 'articles:comment_delete' article.pk comment.pk%}" method="POST">
        {% csrf_token %}
        <input type="submit" value="μ­μ ">
    </form>
</li>
{% endfor %}
```



### Comment μΆκ°μ¬ν­

#### λκΈ κ°μ μΆλ ₯νκΈ°

``` html
<h4>
    λκΈ λͺ©λ‘
</h4>
{% if comments %}
	<p>
        <b>{{comments|length}}κ°μ λκΈμ΄ μμ΅λλ€.</b>
</p>
{% endif %}
```

- {{comments:|length}}
- {{article.comment_sel.all|length}}
- {{comments.count}}

#### λκΈμ΄ μλ κ²½μ° λμ²΄ μ»¨νμΈ  μΆλ ₯(DTLμ for-empty νκ·Έ νμ©)

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
            λκΈμ΄ μμ΅λλ€.
    </p>
    {% endfor %}
</ul>
```







---

## β Customizing authentication in Django

### Substituting a custom User model

#### User λͺ¨λΈ λμ²΄νκΈ°

- μΌλΆ λͺ¨λΈμμλ Djangoμ λ΄μ₯ User λͺ¨λΈμ΄ μ κ³΅νλ μΈμ¦ μκ΅¬μ¬ν­μ΄ μ μ νμ§ μμ μ μλ€.
  - ex) username λμ  emailμ μλ³ ν ν°μΌλ‘ μ¬μ©νλ κ²μ΄ λ μ ν©ν μ¬μ΄νΈ
- Djangoλ Userλ₯Ό μ°Έμ‘°νλλ° μ¬μ©νλ AUTH_USER_MODELκ°μ μ κ³΅νμ¬, default user modelμ μ¬μ μ(override)ν   μ μλλ‘ νλ€
- Djanggoλ μ νλ‘μ νΈλ₯Ό μμνλ κ²½μ° κΈ°λ³Έ μ¬μ©μ λͺ¨λΈμ΄ μΆ©λΆνλλΌλ, μ»€μ€ν μ μ  λͺ¨λΈμ μ€μ νλ κ²μ κ°λ ₯νκ² κΆν­
  - λ¨, νλ‘μ νΈμ λͺ¨λ  migrations νΉμ μ²« migrateλ₯Ό μ€ννκΈ° μ μ μ΄ μμμ λ§μ³μΌ νλ€.



#### AUTH_USER_MODEL

- Userλ₯Ό λνλ΄λλ° μ¬μ©νλ λͺ¨λΈ
- νλ‘μ νΈκ° μ§νλλ λμ λ³κ²½ν  μ μμ
- νλ‘μ νΈ μμ μ μ€μ νκΈ° μν κ²μ΄λ©° μ°Έμ‘°νλ λͺ¨λΈμ μ²«λ²μ§Έλ§μ΄κ·Έλ μ΄μμμ μ¬μ©ν  μ μμ΄μΌ νλ€.
- κΈ°λ³Έ κ° : 'auth.User' (authμ±μ User λͺ¨λΈ)



- [μ°Έκ³ ] νλ‘μ νΈ μ€κ°(mid-project)μ AUTH_USER_MODEL λ³κ²½νκΈ°
  - λͺ¨λΈ κ΄κ³μ μν₯μ λ―ΈμΉκΈ° λλ¬Έμ ν¨μ¬ λ μ΄λ €μ΄ μμμ΄ νμ
  - μ¦, μ€κ° λ³κ²½μ κΆμ₯νμ§ μμΌλ―λ‘ μ΄κΈ°μ μ€μ νλ κ²μ κΆμ₯



#### Custom User λͺ¨λΈ μ μνκΈ°

- κ΄λ¦¬μ κΆνκ³Ό ν¨κ» μμ ν κΈ°λ₯μ κ°μΆ User λͺ¨λΈμ κ΅¬ννλ κΈ°λ³Έ ν΄λμ€μΈ AbstractUserλ₯Ό μμλ°μ μλ‘μ΄ User λͺ¨λΈ μμ±

``` python
# accounts/models.py

from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
    pass
```

- settings.pyμ μμ (μ°λ¦¬κ° μ»€μ€νν μ μ  ν΄λμ€λ‘ λ³κ²½)

``` python
AUTH_USER_MODEL = 'accounts.User'
```

- νλ‘μ νΈ μ€κ°μ μ§ννκΈ° λλ¬Έμ λ°μ΄ν°λ² μ΄μ€λ₯Ό μ΄κΈ°ν ν ν λ§μ΄κ·Έλ μ΄μμ μ§ν

  - μ΄κΈ°ν λ°©λ²

    1. db.sqlite3 νμΌ μ­μ 

    2. migrtaions νμΌμ λͺ¨λ μ­μ (νμΌλͺμ μ«μκ° λΆμ νμΌλ§ μ­μ )

       ``` bash
       $ python manage.py makemigrations
       $ python manage.py migrate
       ```

- admin νμ΄μ§μμ μ¬μ©μ(λ€) ν­λͺ©(νμμ λ³΄)μ΄ μ¬λΌμ‘λ€. μλ‘μ΄ Userλ‘ λμ²΄νλ©΄μ λΉ μ§κ² λμλ€.

  - ν΄κ²°λ°©λ², μ₯κ³ λ¬Έμμ°Έμ‘°, substituting-a-custom-user-model

  ``` python
  # articles/admin.py
  
  from django.contrib import admin
  from django.contrib.auth.admin import UserAdmin
  from .models import User
  
  admin.site.register(User, UserAdmin)
  ```

  







### Custom user & Built-in auth forms

- User λͺ¨λΈμ΄ λΉ μ§λ©΄μ μ΄λμ κ° μ΄κΈλλ λΆλΆμ΄ μκΈΈκ²μ΄λ€

1. νμκ°μ μλ ν μλμ κ°μ μλ¬ λ°μ :
   - AttributeError at /accounts/signup
   - νμκ°μμμ μ¬μ©νλ νΌμ UserCreationForm -> ModelForm,-> ν΄λμ€ λ©ν μ λκ° μμ -> λͺ¨λΈμ΄ μμ±λμ΄ μλ€.  
   - UserCretaionFormκ³Ό UserChangeFormμ κΈ°μ‘΄ λ΄μ₯ User λͺ¨λΈμ μ¬μ©ν ModelFormμ΄κΈ° λλ¬Έμ μ»€μ€ν User λͺ¨λΈλ‘ λμ²΄ν΄μΌ νλ€.



#### Custom Built-in Auth Forms(1/2)

κΈ°μ‘΄ User λͺ¨λΈμ μ¬μ©νκΈ° λλ¬Έμ μ»€μ€ν Userλͺ¨λΈλ‘ λ€μ μμ±νκ±°λ νμ₯ν΄μΌ νλ forms

- UserCreationForm
- UserChangeForm

``` python
# accounts/forms.py
import django.contrib.auth.forms import UserChangeForm,UserCreationForm
from django.contrib.auth import get_user_model
# νμ¬ μ₯κ³ λͺ¨λΈμ νμ±νλ μ μ  λͺ¨λΈμ λ¦¬ν΄νλ€.
# μ μ λ μ§μ  μ°Έμ‘°νμ§μλλ€.
# λ¨μ μ μ λͺ¨λΈμ λλ €μ£Όλκ² μλλΌ νμ¬ μ₯κ³  νλ‘μ νΈμ νμ±νλ μ μ λͺ¨λΈμ λ¦¬ν΄νλ€.

class CustomUserChangeForm(userChangeForm):
    class Meta:
        model = get_user_model()
        fields = ('email', 'first_name', 'last_name')
        
class CustomUserCreationForm(UserCreationForm): 
    class Meta:
        model = get_user_model()
```

#### Custom Built-in Auth Forms(2/2)

- μ΄μ²λΌ μ»€μ€ν User λͺ¨λΈμ΄ AbstractUserμ νμ ν΄λμ€μΈ κ²½μ° λ€μκ³Ό κ°μ λ°©μμΌλ‘ formμ νμ₯

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

- νμ¬ νλ‘μ νΈμμ νμ±νλ μ¬μ©μ λͺ¨λΈμ λ°ν
  - User λͺ¨λΈμ μ»€μ€ν°λ§μ΄μ§ν μν©μμλ Custom Userλͺ¨λΈμ λ°νλ€.
- μ΄ λλ¬Έμ Djangoλ User ν΄λμ€λ₯Ό μ§μ  μ°Έμ‘°νλ λμ  django.contrib.auth.get_user_model()μ μ¬μ©νμ¬ μ°Έμ‘°ν΄μΌ νλ€κ³  κ°μ‘°







## User - Article

### 1:N κ΄κ³μ€μ  : User-Article

- μ¬μ©μλ μ¬λ¬ κ°μ κ²μκΈμ μμ±ν  μ μλ€

- Articleμ΄ N, 1μ΄ 1μ΄λ€.

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

- μΈλν€ λ³μλͺμ 1:Nκ΄κ³μμ μ°Έμ‘°νλ λͺ¨λΈμ΄λ¦μ μλ¬Έμ λ¨μν.
- settings.pyμ AUTH_USER_MODEL = 'accounts.User'
- μΈλν€ userμ μ²«λ²μ§Έ μΈμλ‘ Userλ₯Ό μ¬μ©νλ©΄ μλλ€.(μ§μ  ν€ μ°Έμ‘° κΈμ§)
  - κ°μ μ μΌλ‘ userκ°μ λ¦¬ν΄λ°μμ μ κ³΅ν΄μΌνλ€. get_user_model()λν μ¬μ©ν  μ μλ€. λͺ¨λΈμμμ μ°Έμ‘°λ‘ ν¨μλ λΆκ°λ₯νκΈ° λλ¬Έμ΄λ€.



#### User λͺ¨λΈμ μ°Έμ‘°νλ λ°©λ²

1. settings.AUTH_USER_MODEL

- return κ°μΌλ‘ λ¬Έμμ΄μ λ°ννλ€.
- User  λͺ¨λΈμ λν μΈλ ν€ λλ λ€λλ€ κ΄κ³λ₯Ό μ μν  λ μ¬μ©ν΄μΌ νλ€.
- models.pyμμ Userλͺ¨λΈμ μ°Έμ‘°ν  λ μ¬μ©νλ€.

2. get_user_model()

- return κ°μΌλ‘ objectλ₯Ό λ°ννλ€.

- νμ¬ νμ±ν(active)λ User λͺ¨λΈμ λ°ννλ€.
  - μ»€μ€ν°λ§μ΄μ§ν User λͺ¨λΈμ΄ μμ κ²½μ°λ Custom User λͺ¨λΈμ, κ·Έλ μ§ μμΌλ©΄ Userλ₯Ό λ°ννλ€.
  - Userλ₯Ό μ§μ  μ°Έμ‘°νμ§ μλ μ΄μ 
- models.pyκ° μλ λ€λ₯Έ λͺ¨λ  κ³³μμ μ μ  λͺ¨λΈμ μ°Έμ‘°ν  λ μ¬μ©

#### User λͺ¨λΈμ λν μ λ¦¬

- **models.pyμμλ settings.AUTH_USER_MODEL**
- **models.pyλ₯Ό μ μΈν λ€λ₯Έ λͺ¨λ  κ³³μ get_user_model()**





### 1:N κ΄κ³μ€μ  : User-Comment

1. Userμ Comment κ° λͺ¨λΈ κ΄κ³ μ μ ν migrtaion

``` python
#articles/models.py
class Comment(models.Model):
    article = models.ForeignKey(Article, on_delete=models.CASCADE)
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    

```



2. Userμ Comment κ° λͺ¨λΈ κ΄κ³ μ μ ν migration

   - nulll κ°μ΄ νμ©λμ§ μλ user_id νλκ° λ³λμ κ° μμ΄ commentμμΆκ°λλ € νκΈ° λλ¬Έμ΄λ€.

   - 1μ μλ ₯ ν enter, νμ¬ νλ©΄μμ κΈ°λ³Έ κ°μ μ€μ νκ² λ€λ μλ―Έ

   - 1μ μλ ₯ ν enter,

     κΈ°μ‘΄ νμ΄λΈμ μΆκ°λλ user_id νλμ κ°μ 1λ‘ μ€μ νκ² λ€λ μλ―Έλ‘ κΈ°μ‘΄ λκΈμ μμ±μκ° λͺ¨λ 1λ² userκ° λλ€.































