# Vue 04 ๐



## ๐ฏ Server & Client

### Client

- ์๋ฒ์๊ฒ ๊ทธ ์๋ฒ๊ฐ ๋งก๋(์๋ฒ๊ฐ ์ ๊ณตํ๋) **์๋น์ค๋ฅผ ์์ฒญ**ํ๊ณ ,
- ์๋น์ค ์์ฒญ์ ์ํด ํ์ํ ์ธ์๋ฅผ **์๋ฒ๊ฐ ์๊ตฌํ๋ ๋ฐฉ์์ ๋ง๊ฒ ์ ๊ณต**ํ๋ฉฐ,
- ์๋ฒ๋ก๋ถํฐ ๋ฐํ๋๋ ์๋ต์ **์ฌ์ฉ์์๊ฒ ์ ์ ํ ๋ฐฉ์์ผ๋ก ํํ**ํ๋๊ธฐ๋ฅ์ ๊ฐ์ง ์์คํ





### โถ ๋ณต๊ธฐ

1. 1:N๊ด๊ณ ๋ชจ๋ธ์ค์ 
   - author = models.ForeignKey(settings.AUTH_USER_MODEL,on_delete=models.CASCADE)

2. Fetch API
   - https://developer.mozilla.org/ko/docs/Web/API/Fetch_API
   - ex) fetch('http://127.0.0.1:8000/api/v1/articles/')
     - ํด๋น ์ฃผ์๋ก XHR ์์ฒญ์ ํ๊ฒ ๋ค๋ ์๋ฏธ
   - Access to fetch at 'http://127.0.0.1:8000/api/v1/articles/' from origin 'https://www.google.com' has been blocked by **CORS policy:** No 'Access-Control-Allow-Origin' header is present on the requested resource. If an opaque response serves your needs, set the request's mode to 'no-cors' to fetch the resource with CORS disabled.
   - CORS์ด์๋ฅผ ๋ฐํํ๋ ์ด์ ๋ ์์ฉ์ ๋ฐฉ์งํ๊ธฐ ์ํจ์ด๋ค. CORS๊ฐ ์๋ค๋ฉด ๊ฐ์ง ํผ์ฑ ์ฌ์ดํธ๋ฅผ ๋ง๋ค์ด๋๊ณ  ์ฌ์ฉ์๊ฐ ์๋ชป ์ ์ํ๋ฉด ์ง์ง ์ฌ์ดํธ์ธ๋ง๋ฅ ์๋น์ค๋ฅผ ์ ๊ณตํ๋ ์ฒํ๋ค. ๋ธ๋ผ์ฐ์ ๋ ์์์ ์ธ ์ฌ์ดํธ๋ฅผ ๋ฐฉ์งํ๊ณ ์ CORS ๋ฅผ ์ด์๋ฅผ ๋ฐํํ๋ค. 

3. https://pypi.org/project/django-cors-headers/

   - ์ฅ๊ณ  CORS๋ฅผ ํด๊ฒฐํ๊ธฐ ์ํ ๋ฐฉ๋ฒ

   - CORS_ALLOWED_ORIGINS = [

       "https://www.google.com",

     ]

   - python decouple์ ํตํด ์ ๋ด์ฉ์ ์จ๊ฒจ์ ๋ค๋ฃฐ ์ ์๋ค. 

     - ๋ฐฐํฌ์์๋ SECRET_KEY๋ฅผ ์จ๊ฒจ์ผ ํ๋ค. 

       1. manage.py์ ๋์ผํ ์์น์ .env ์์ฑ

       2. .env์ SECRET_KEY ๋ณ์์ ๊ฐ์ ๋ถ์ฌ๋ฃ์ด์ค๋ค.

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