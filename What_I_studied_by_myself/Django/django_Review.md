# 🥔 Django Review



## 🌱 Substituting a custom User model (커스텀 유저 모델 대체하기)

#### 기본 유저 모델을 커스텀 유저 모델로 대체하자 

- Django의 내장 User모델을 커스텀하자.
- Django는 User를 참조하는데 사용하는 **AUTH_USER_MODEL** 값을 제공하여, default user model을 *재정의(override)*할 수 있도록 한다.

- Django는 새 프로젝트를 시작하는 경우 기본 사용자 모델이 충분하더라도, **커스텀 유저 모델을 설정하는 것을 강력하게 권장**한다.
  - **단, 프로젝트의 모든 migrations 혹은 첫 migrate를 실행하기 전에 이 작업을 마쳐야 한다.**



#### Custom User 모델 정의하기

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

- admin site에 Custom User 모델을 등록, #admin.py

```python
from django.contrib import admin
from django.contrib.ath.admin import UserAdmin
from .models import User

admin.site.register(User, UserAdmin)
```

- migrations, migrate



## 🌱 Custom user & Built in auth forms

- 어디선가 어긋나는 부분 해결해보기

#### 회원가입

- 회원가입에서 사용하는 form, **UserCreationForm**
- 즉, 기존 User 모델을 사용하기 때문에 커스텀 User 모델로 다시작성하거나 확장해야 한다.

#### 회원정보 수정

- 회원정보 수정에서 사용하는 form, **UserChangeForm**
- 즉, 기존 User 모델을 사용하기 때문에 커스텀 User 모델로 다시작성하거나 확장해야 한다.



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

- 현재 프로젝트에서 활성화된 사용자 모델을 반환해준다.
  - User 모델을 커스터마이징한 상황에서는 Custom User 모델을 반환해준다.
- 이 떄문에 Django는 User클래스를 직접 참조하는 대신
  - **django.contrib.auth.get_user_model()**을 사용하여 참조해야 한다고 강조.



## 🌱 User-Article(1:N)

- 사용자는 여러 개의 게시글을 작성할 수 있다.

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
  - models.py에서 User 모델을 참조할 때 사용한다.
  - 반환값이 str이다.
- **get_user_model()**
  - 현재 활성화된 User 모델을 반환한다.
  - models.py가 아닌 다른 모든 곳에서 유저 모델을 참조할 때 사용한다.
  - 반환값이 object다.
