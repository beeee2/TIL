# Vue 04 🔍



## 🕯 Server & Client

### Client

- 서버에게 그 서버가 맡는(서버가 제공하는) **서비스를 요청**하고,
- 서비스 요청을 위해 필요한 인자를 **서버가 요구하는 방식에 맞게 제공**하며,
- 서버로부터 반환되는 응답을 **사용자에게 적절한 방식으로 표현**하는기능을 가진 시스템





### ▶ 복기

1. 1:N관계 모델설정
   - author = models.ForeignKey(settings.AUTH_USER_MODEL,on_delete=models.CASCADE)

2. Fetch API
   - https://developer.mozilla.org/ko/docs/Web/API/Fetch_API
   - ex) fetch('http://127.0.0.1:8000/api/v1/articles/')
     - 해당 주소로 XHR 요청을 하겠다는 의미
   - Access to fetch at 'http://127.0.0.1:8000/api/v1/articles/' from origin 'https://www.google.com' has been blocked by **CORS policy:** No 'Access-Control-Allow-Origin' header is present on the requested resource. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.
   - CORS이슈를 발행하는 이유는 악용을 방지하기 위함이다. CORS가 없다면 가짜 피싱 사이트를 만들어두고 사용자가 잘못 접속하면 진짜 사이트인마냥 서비스를 제공하는 척한다. 브라우저는 악의적인 사이트를 방지하고자 CORS 를 이슈를 발행한다. 

3. https://pypi.org/project/django-cors-headers/

   - 장고 CORS를 해결하기 위한 방법

   - CORS_ALLOWED_ORIGINS = [

       "https://www.google.com",

     ]

   - python decouple을 통해 위 내용을 숨겨서 다룰 수 있다. 

     - 배포시에는 SECRET_KEY를 숨겨야 한다. 

       1. manage.py와 동일한 위치에 .env 생성

       2. .env에 SECRET_KEY 변수와 값을 붙여넣어준다.

          SECRET_KEY = 'django-insecure-+9cbge*4cmcx-n5r%vg!l67-0^9-51q9*k1f@36*c4us7mrusw'

       3. pip install python-decouple

       

4. API endpoints

   - https://dj-rest-auth.readthedocs.io/en/latest/api_endpoints.html

5. django -rest - framework

   - ```
     REST_FRAMEWORK = {
         'DEFAULT_AUTHENTICATION_CLASSES': [
             # 'rest_framework.authentication.BasicAuthentication',
             # 'rest_framework.authentication.SessionAuthentication',
             
             'rest_framework.authentication.TokenAuthentication',
         ]
     }
     ```