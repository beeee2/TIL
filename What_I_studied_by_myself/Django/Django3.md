### GET과 POSET

- Data를 조회할 때는 GET

- DB에 변경이 있을 때 POST

  - CREATE 시 > POST
  - READ > GET
  - UPDATE > POST
  - DELETE > POST

  - **주소줄을 이용한 요청은 GET**
  - **redirect**는 **GET**요청

- method를 POST로만 변경하고 난 후,

  ![image-20220310131850917](Django3.assets/image-20220310131850917.png)

  - 403 Forbidden 에러가 발생한다. 
    - 서버에 요청이 전달되었지만 권한 때문에 거절되었다는 것을 의미한다.
    - CSRF verification failed.
    - CSRF란 사이트 간 요청 위조이다. 웹 사이트 취약점 공격의 하나로, 사용자가 자신의 의지와는 무관하게 공격자가 의도한 행위를 특정 웹사이트에 요청하게 하는 공격을 말한다.

---

### ETC

- a 태그와 같이 단순 링크이동도 GET요청과 같다.

### POST

- {% csrf_token %} 필수로 기재한다.

- views.py에 

  ``` python
  article = Article()
  article.title = request.POST.get('title')
  article.content = request.POST.get('content')
  article.save()
  ```

  - request를 POST로 받는 것 기억하기

  