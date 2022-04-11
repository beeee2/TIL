# 🌱 Handling HTTP requests

## Handling HTTP requests

- Django에서 HTTP 요청을 처리하는 방법
  1. Django shortcut functions
  2. View decorators



### Django shortcut functions

- django.shortcuts 패키지는 개발에 도움될 수 있는 여러 함수와 클래스를 제공한다.
- shortcuts function 종류
  - render ()
  - redirect ()
  - **get_object_or_404()**
  - get_list_or_404()



#### get_object_or_404()

- 모델 manager인 objects에서 get()을 호출하지만, 해당객체가 없을 경우 DoesNotExist 예외 대신 Http 404를 raise
- get()에 경우 조건에 맞는 데이터가 없을 경우에 예외를 발생시킨다.
  - 코드 실행 단계에서 발생한 예외 및 에러에 대해서 브라우저는 http status code 500으로 인식한다.
- 상황에 따라 적절한 예외처리를 하고 클라이언트에게 올바른 에러 상황을 전달하는 것 또한 개발의 중요한 요소 중 하나



### Django View decorators

- Django는 다양한 HTTP 기능을 지원하기 위해 view 함수에 적용할 수 있는 여러 데코레이터를 제공한다.

- Decorator
  - 어떤 함수에 기능을 추가하고 싶을 때, 해당 함수를 수정하지 않고 기능을 연장해주는 함수
  - 즉, 원본 함수를 수정하지 않으면서 추가 기능만을 구현할 때 사용한다.



- Allowed HTTP methods
  - 요청 메서드에(GET, POST) 따라 view 함수에 대한 액세스를 제한
  - 요청이 조건을 충족시키지 못하면 HttpResponseNotAllowwed를 Return (405 Method Not Allowed)
  - require_http_methods(), require_POST(), require_safe(),



#### require_http_methods()

- view 함수가 특정한 method 요청에 대해서만 허용하도록 하는 데코레이터

- ``` python
  from django.views.decorators.http import require_http_methods
  ```

- 

#### require_POST()

- view 함수가 POST method 요청만 승인하도록 하는 데코레이터
- delete 함수에서 사용가능하다.

#### require_safe()

- view 함수가 GET 및 HEAD method만 허용하도록 요구하는 데코레이터
- django는 require_GET 대신 require_safe를 사용하는 것을 권장
- index, detail 함수에서 사용가능하다.



## Media files

#### Media file

- 미디어 파일
- 사용자가 웹에서 업로드하는 정적 파일(user-uploaded)
- 유저가 업로드 한 모든 정적 파일



#### ImageField()

- 이미지 업로드에 사용하는 모델 필드
- FileField를 상속받는 서브 클래스이기 때문에 FileField의 모든 속성 및 메서드를 사용가능하며, 더해서 사용자에 의해 업로드 된 객체가 유효한 이미지 인지 검사한다.
- ImageField 인스턴스는 최대 길이가 100자인 문자열로 DB에 생성되며, max_length 인자를 사용하여 최대 길이를 변경할 수 있다.



#### FileField()

- 파일 업로드에 사용하는 모델 필드
- 2개의 선택 인자를 가지고 있다.
  - upload_to
  - storage





### Image Upload





### Image Resizing

