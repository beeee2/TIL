# ๐ฅ Django Review



## ๐ฑ Substituting a custom User model (์ปค์คํ ์ ์  ๋ชจ๋ธ ๋์ฒดํ๊ธฐ)

#### ๊ธฐ๋ณธ ์ ์  ๋ชจ๋ธ์ ์ปค์คํ ์ ์  ๋ชจ๋ธ๋ก ๋์ฒดํ์ 

- Django์ ๋ด์ฅ User๋ชจ๋ธ์ ์ปค์คํํ์.
- Django๋ User๋ฅผ ์ฐธ์กฐํ๋๋ฐ ์ฌ์ฉํ๋ **AUTH_USER_MODEL** ๊ฐ์ ์ ๊ณตํ์ฌ, default user model์ *์ฌ์ ์(override)*ํ  ์ ์๋๋ก ํ๋ค.

- Django๋ ์ ํ๋ก์ ํธ๋ฅผ ์์ํ๋ ๊ฒฝ์ฐ ๊ธฐ๋ณธ ์ฌ์ฉ์ ๋ชจ๋ธ์ด ์ถฉ๋ถํ๋๋ผ๋, **์ปค์คํ ์ ์  ๋ชจ๋ธ์ ์ค์ ํ๋ ๊ฒ์ ๊ฐ๋ ฅํ๊ฒ ๊ถ์ฅ**ํ๋ค.
  - **๋จ, ํ๋ก์ ํธ์ ๋ชจ๋  migrations ํน์ ์ฒซ migrate๋ฅผ ์คํํ๊ธฐ ์ ์ ์ด ์์์ ๋ง์ณ์ผ ํ๋ค.**



#### Custom User ๋ชจ๋ธ ์ ์ํ๊ธฐ

- #accounts/models.py

```python
from django.contrib.auth.models import AbstractUser

class User(AbstractUser):
    pass
```

- settings.py

```python
AUTH_USER_MODEL = 'accounts.User'
```

- admin site์ Custom User ๋ชจ๋ธ์ ๋ฑ๋ก, #admin.py

```python
from django.contrib import admin
from django.contrib.ath.admin import UserAdmin
from .models import User

admin.site.register(User, UserAdmin)
```

- migrations, migrate



## ๐ฑ Custom user & Built in auth forms

- ์ด๋์ ๊ฐ ์ด๊ธ๋๋ ๋ถ๋ถ ํด๊ฒฐํด๋ณด๊ธฐ

#### ํ์๊ฐ์

- ํ์๊ฐ์์์ ์ฌ์ฉํ๋ form, **UserCreationForm**
- ์ฆ, ๊ธฐ์กด User ๋ชจ๋ธ์ ์ฌ์ฉํ๊ธฐ ๋๋ฌธ์ ์ปค์คํ User ๋ชจ๋ธ๋ก ๋ค์์์ฑํ๊ฑฐ๋ ํ์ฅํด์ผ ํ๋ค.

#### ํ์์ ๋ณด ์์ 

- ํ์์ ๋ณด ์์ ์์ ์ฌ์ฉํ๋ form, **UserChangeForm**
- ์ฆ, ๊ธฐ์กด User ๋ชจ๋ธ์ ์ฌ์ฉํ๊ธฐ ๋๋ฌธ์ ์ปค์คํ User ๋ชจ๋ธ๋ก ๋ค์์์ฑํ๊ฑฐ๋ ํ์ฅํด์ผ ํ๋ค.



```python
#accounts/forms.py
from django.contrib.auth.forms import UserChangeForm, UserCreationForm
from django.contrib.auth import get_user_model

class CustomUserChangeForm(UserChangeForm):
    class Meta:
        model = get_user_model()
        fields = ('email',)
        
class CustomUserCreationForm(UserCreationForm):
    class Meta(UserCreationForm.Meta):
        model = get_user_model()
        fields = UserCreationForm.Meta.fields + ('emails',)
```



#### get_user_model()

- ํ์ฌ ํ๋ก์ ํธ์์ ํ์ฑํ๋ ์ฌ์ฉ์ ๋ชจ๋ธ์ ๋ฐํํด์ค๋ค.
  - User ๋ชจ๋ธ์ ์ปค์คํฐ๋ง์ด์งํ ์ํฉ์์๋ Custom User ๋ชจ๋ธ์ ๋ฐํํด์ค๋ค.
- ์ด ๋๋ฌธ์ Django๋ Userํด๋์ค๋ฅผ ์ง์  ์ฐธ์กฐํ๋ ๋์ 
  - **django.contrib.auth.get_user_model()**์ ์ฌ์ฉํ์ฌ ์ฐธ์กฐํด์ผ ํ๋ค๊ณ  ๊ฐ์กฐ.



## ๐ฑ User-Article(1:N)

- ์ฌ์ฉ์๋ ์ฌ๋ฌ ๊ฐ์ ๊ฒ์๊ธ์ ์์ฑํ  ์ ์๋ค.

```python
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

- **settings.AUTH_USER_MODEL**
  - models.py์์ User ๋ชจ๋ธ์ ์ฐธ์กฐํ  ๋ ์ฌ์ฉํ๋ค.
  - ๋ฐํ๊ฐ์ด str์ด๋ค.
- **get_user_model()**
  - ํ์ฌ ํ์ฑํ๋ User ๋ชจ๋ธ์ ๋ฐํํ๋ค.
  - models.py๊ฐ ์๋ ๋ค๋ฅธ ๋ชจ๋  ๊ณณ์์ ์ ์  ๋ชจ๋ธ์ ์ฐธ์กฐํ  ๋ ์ฌ์ฉํ๋ค.
  - ๋ฐํ๊ฐ์ด object๋ค.



```python
#articles/forms.py
class ArticleForm(forms.ModelForm):
    class Meta:
        model = Article
        exclude = ('user',)
```

- ๋๊ฐ ๊ธ์ ์ผ๋์ง์ ๋ํ ๊ฐ์ ์ ๋ฌํด์ค์ผ ํ๋ค.

```python
#articles/views.py

def create(request):
    if request.method == 'POST':
        form = ArticleForm(request.POST)
        if form.is_valid():
            article = form.save(commit=False)
            article.user = request.user
            article.save()
            return redirect('articles:detail', article.pk)
    else:
        form = ArticleForm()
    context = {
        'form' : form
    }
    return render(request, 'articles/create.html', context)
```



#### ์ญ์ 

- ๋ด๊ฐ ์ด ๊ฒ๋ง ์ญ์ ํด๋ณด์(๋ค๋ฅธ ์ฌ๋์ด ๋ด ๊ฒ์๋ฌผ์ ์ญ์ ํ์ง ๋ชปํ๊ฒ ํด๋ณด์)

```python
# articles/views.py

@require_POST
def delete(request, pk):
    article = get_object_or404(Article, pk=pk)
    if request.user.is_authenticated:
        if request.user == article.user:
            article.delete()
    return redirect('articles:index')

```



#### ์์ 

```python
def update(request, pk):
    article = get_object_or_404(Article, pk=pk)
    if request.user == article.user:
        if request.method == 'POST':
            form = ArticleForm(request.POST, instance=article)
            if form.is_valid():
                article = form.save()
                return redirect('articles:detail', article.pk)
        else:
            form = ArticleForm(instance = article)
    else:
        return redirect('articles:index')
    context = {
        'form' : form,
        'article': article,
    }
    return render(request, 'articles/update.html', context)
```



## ๐ฑ User-Comment(1:N)

```python
# articles/model.py
from django.db import models
from django.conf import settings

class Comment(models.Model):
    article = models.ForeignKey(Article, on_delete=models.CASCADE)
    user = models.ForeignKey(settings.AUTH_USER_MODEL, on_delete=models.CASCADE)
    content = models.CharField(max_length=200)
    created_at = models.DateTimeField(auto_now_add=True)
    updated_at = models.DateTimeField(auto_now=True)
    
    def __str__(self):
        return self.content
    
```

```python
#articles/views.py
@require_POST
def comment_create(request, pk):
    if request.user.is_authenticated:
        article = get_object_or_404(Article, pk=pk)
        comment_form = CommentForm(request.POST)
        if comment_form.is_valid():
            comment = comment_form.save(commit=False)
            comment.article = article
            comment.user = request.user
            comment.save()
        return redirect('articles:detail', article.pk)
    return redirect('accounts:login')
```





## ๐ฑ ๋ณ์ ์ง๋ฃ ๊ธฐ๋ก ์์คํ

- ๋ค๋๋ค ๊ด๊ณ(M:N ๊ด๊ณ)
- Django์์๋ ๋ค๋๋ค(M:N, many-to-many) ๊ด๊ณ์ค์  ์ ์ฌ์ฉํ๋ ๋ชจ๋ธ ํ๋
- ํ๋์ ํ์ ์์น์ธ์(M:N ๊ด๊ณ๋ก ์ค์ ํ  ๋ชจ๋ธ ํด๋์ค)๊ฐ ํ์ํ๋ค.



- **ManyToManyField** ์์ฑ ์ ์ค๊ฐ ๋ชจ๋ธ ์ญ์ ๋๋ค.
- ํ๋ ์์ฑ ์์น๋ ๋ ์ค ํ๋ ๋๋ ๋ชจ๋ ์์ฑ์ด ๊ฐ๋ฅํ๋ค.

```python
# hospitals/models.py

from django.db import models

class Doctor(models.Model):
    name = models.TextField()
    
class Patient(models.Model):
    doctors = models.ManyToManyField(Doctor)
	name = models.TextField()

```



## ๐ฑ Like

- User : Article, M:N๊ด๊ณ

```python
# articles/models.py

class Article(models.Model):
    like_users = models.ManyToManyField(settings.AUTH_USER_MODEL)
```

