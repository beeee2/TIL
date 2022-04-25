## Comment CREATE



```python
# accounts/models.py
from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
    pass
```

```python
# settings.py
AUTH_USER_MODEL = 'accounts.User'
```

``` python
# articles/models.py
class Article(models.Model):
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete = models.CASCADE)
    title = models.CharField(max_length=10)
    content = models.TextField()
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    
class Comment(models.Model):
    article = models.ForeignKey(Article, on_delete=models.CASCADE)
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    content = models.CharField(max_length=200)
    created_at = models.DateTimeField(auth_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
```

```python
# articles/forms.py
from django import forms
from .models import Article, Comment

class CommentForm(forms.ModelForm):
    class Meta:
        model = Comment
        fields = ('content',)
```

``` python
# articles/views.py
from .forms import ArticleForm, CommentForm

@require_safe
def detail(request, pk):
    article = get_object_or_404(Article, pk)
    comment_form = CommentForm()
    context = {
        'article' : article,
        'comment_form' : comment_form,
    }
    return render(request, 'articles/detail.html', context)
```

``` django
# articles/detail.html
<form action="{% url 'articles:comments_create' article.pk %}" method="POST">
    {% csrf_token %}
    {{ comment_form }}
    <input type="submit" />
</form>
```

``` python
# articles/urls.py
urlpatterns = [
    path('<int:pk>/comments/', views.comments_create, name="comments_create"),
]
```

``` python
# articles/views.py

@require_POST
def comments_create(request, pk):
    article = Article.objects.get(pk=pk)
    comment_form = CommentForm(request.POST)
    if comment_form.is_valid():
         comment = comment_form.save(commit=False)
        comment.article = article
        comment.save()
    return redirect('articles:detail', article.pk)
```



### The 'save()' method

- save(commit = False)
  - Create, but don't save the new instance
  - 기본 값은 True이다.
  - 아직 데이터베이스에 저장되지 않은 인스턴스를 반환한다.
  - 저장하기 전에 객체에 대한 사용자 지정 처리를 수행할 때 유용하게 사용

---



## Comment READ

#### 댓글 출력

``` python
# articles/views.py
from .models import Article, Comment

def detail(request, pk):
    article = get_object_or_404(Article, pk=pk)
    comment_form = CommentForm()
    comments = article.comment_set.all()
    context = {
        'article' : article,
        'comment_form' : comment_form,
        'comments' : comments,
    }
    return render(request, 'articles/detail.html', context)
```





---



## Comment DELETE

```python
#articles/urls.py
urlpatterns =  [
    path('<int:article_pk>/comments/<int:comment_pk>/delete',views.comments_delete, name="comments_delete")
]
```

``` python
#articles/views.py
from .models import Article, Comment

def comments_delete(request,article_pk, comment_pk):
    comment = Comment.objects.get(pk=comment_pk)
    comment.delete()
    return redirect('articles:detail', article_pk)
```

``` django
# articles/detail.html
{% for comment in comments %}
	<li>
		{{comment.content}}
        <form action={% url 'articles:comment_ delete' article.pk comment.pk %} method="POST">
        	{% csrf_token %}
        	<input type="submit" value="제출"/>
        </form>
	</li>
{% endfor %}
```

