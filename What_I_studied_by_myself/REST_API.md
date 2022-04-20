# 🌱REST API

## 🥔 HTTP

#### HTTP

- HyperText Transfer Protocol
- 웹 상에서 컨텐츠를 전송하기 위한 약속
- HTML 문서와 같은 리소스들을 가져올 수 있도록 하는 프로토콜(규칙, 약속)
- 웹에서 이루어지는 모든 데이터 교환의 기초
  - 요청(request)
    - 클라이언트에 의해 전송되는 메세지
  - 응답(response)
    - 서버에서 응답으로 전송되는 메세지
- 기본 특성
  - Stateless(상태가 없음 )
  - Connectionless(비연결성)
- 쿠키와 세션을 통해 서버 상태를 요청과 연결하도록 함



#### HTTP 메세지

- 요청예시
  - 메소드 방식
  - 요청한 주소
  - 프로토콜의 버전
  - 헤더부분에 추가적인 정보 기재
- 응답예시
  - 프로토콜의 버전
  - 상태코드(서버의 상태과 결과를 숫자로 표현한다.)
  - 상태 메세지
  - 헤더에 추가적인 정보 기재

- HTTP 객체가 서로 요청과 응답을 통해 왔다갔다 하며 그 안에는 여러 정보들이 들어있음을 알 수 있다.



#### HTTP request methods

- 자원에 대한 행위(수행하고자 하는 동작)을 정의
- 주어진 리소스(자원)에 수행하길 원하는 행동을 나타냄
- HTTP Method 예시
  - GET, POST, PUT, DELETE



💁‍♀️ 이제 역할을 바꾸어 수정일 경우 'PUT'을 삭제일 경우'DELETE'를 보내보자.

💁‍♀️ 'GET'은 조회, 'POST'은 작성



#### HTTP response status codes

- 응답의 상태 코드
- 특정 HTTP 요청이 성공적으로 완료되었는 지 여부를 나타낸다.
- 응답은 5개의 그룹으로 나뉘어진다.
  1. Informational responses (1xx)
  2. Successful responses (2xx)
  3. Redirection messages (3xx)
  4. Client error responses (4xx)
  5. Server error responses (5xx)



#### 웹에서의 리소스 식별

- HTTP 요청의 대상을 리소스(resource, 자원)라고함
- 리소스는 문서, 사진 또는 기타 어떤 것이든 될 수 있음
- 각 리소스는 리소스 식별을 위해 HTTP 전체에서 사용되는 URI(Uniform Resource Identifier)로 식별된다.



## 🥔 RESTful API

## 🥔 Response

## 🥔 Single Model

## 🥔1:N Relation

