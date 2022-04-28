# 🌱 JavaScript 02

#### 핵심인물

- 팀 버너스리
  - WWW, URL, HTTP, HTML 최초 설계자
  - 웹의 아버지
- 브랜던 아이크(Brendan Eich)
  - JavaScript 최초 설계자
  - 모질라 재단 공동 설립자
  - 코드네임 피닉스 프로젝트 진행
    - 파이어폭스의 전신



#### JavaScript의 탄생

- 1994년 당시 넷스케이프 커뮤니케이션스사의 Netscape Navigator 브라우저가 전 세계 점유율을 80% 이상 독점하며 브라우저의 표준 역할을 한다.
- 당시 넷스케이프에 재직 중이던 브랜던 아이크가 HTML을 동적으로 동작하기 위한회사 내부 프로젝트를 진행 중 JS를 개발한다.
- JavaScript 이름 변천사
  - Mocha -> LiveScript -> JavaScript(1996)

- 그러나 1995년 경쟁사 마이크로소프트에서 이를 채택하여 커스터마이징한 JScript를 만듦
- 이를, IE 1.0에 탑재(거의 홀라당 뺏김) -> 1차 브라우저 전쟁의 시작



#### 제 1차 브라우저 전쟁

- 넷스케이프 vs 마이크로소프트(이하 MS)
- 빌 게이츠 주도하에 MS는 1997년 IE 4를 발표하면서 시장을 장악하기 시작한다.
  - 당시 윈도우 OS의 시장 점유율은 90%
  - 글로벌 기업 MS의 공격적인 마케팅
- MS의 승리로 끝나며 2001년부터 IE의 점유율은 90%를 상회
- 1998년 넷스케이프에서 나온 브랜던 아이크 외후계자들은 모질라 재단을 설립
  - 파이어 폭스를 통해 IE에 대항하며 꾸준히 점유율을 올려나감

- MS의 폭발적 성장, IE3에서 자체적인 JScript를지원, 호환성무제로 크로스 브라우징 등의 이슈 발생
- 이후 넷스케이프 후꼐자들은 모질라 재단 기반의 파이어폭스를 개발



#### 제 2차 브라우저 전쟁

- MS vs Google
- 2008년 Google의 Chrome 브라우저 발표
- 2011년 3년 만에 파이어폭스의 점유율을 돌파 후 2012년부터 전 세계 점유율 1위 등록
- 크롬의 승리 요인
  - 압도적인 속도
  - 강력한 개발자 도구 제공
  - 웹 표준



#### 파편화와 표준화

- 제 1차 브라우저 전쟁 이후 수많은 브라우저에서 자체 자바스크립트 언어를 사용하게 된다.
- 결국 서로 다른 자바스크립트가 만들어지면서 크로스 브라우징 이슈가 발생하여 웹 표준의 필요성이 제기
- 크로스 브라우징(Cross Browsing)
  - W3C에서 채택된 표준 웹 기술을 채용하여 각각의 브라우저바다 다르게 구현되는 기술을 비슷하게 만들되, 어느 한쪽에 치우치지 않도록 웹 페이지를 제작하는 방법론 (동일성이 아닌 동등성)
  - 브라우저마다 렌더링에 사용하는 엔진이 다르기 때문

- 1996년부터 넷스케이프는 표준 제정의 필요성을 주장
  - ECMA 인터내셔널(정보와 통신 시스템을 위한 국제적 표준화 기구)에 표준 제정 요청
- 1997년 ECMAScript1 (ES1) 탄생
- 제 1차 브라우저 전쟁 이후 제기된 언어의 파편화를 해결하기 위해 각 브라우저 회사와 재단은 표준화에 더욱 적극적으로 힘을 모으기 시작한다.



#### JavaScript ES6+

- 2015년 ES2015(ES6)탄생
  - "NEXT-gen of JS"
  - JavaScript의 고질적인 문제들을 해결
  - JavaScript의 다음 시대라고 불릴 정도로 많은 혁신과 변화를 맞이한 버전
  - 이때부터 버전 순서가 아닌 출시 연도를 붙이는 것이 공식 명칭이나 통상적으로 ES6라고 부른다.
  - 현재는 표준 대부분이 ES6+로 넘어왔다.



#### Vanilla Javascript

- 크로스 브라우징, 간편한 활용등을 위해 많은 라이브러리 등장(jQuery 등)
- ES6이후 다양한 도구의 등장으로 순수 자바스크립트 활용의 증대



### 정리

- History of javaScript & Browser
  - 브라우저 전쟁
  - 파편화와 표준화의 투쟁
- 브라우저 전쟁의 여파
  - Cross Browsing Issue
  - 표준화(통합)를 위한 노력
  - Vanilla JavaScript



---

# 🌱 DOM 조작과 Event

## 💁‍♀️ DOM

#### 브라우저에서 할 수 있는 일

#### DOM이란?

- HTML, XML과 같은 문서를 다루기 위한 문서 프로그래밍 인터페이스
- 문서를 구조화하고 구조화된 구성요소를하나의 객체로 취급하여 다루는 논리적 트리 모델
- 문서가 구조화되어 있으며 각 요소는 객체(object)로 취급
- 단순한 속성 접근, 메서드 활용뿐만 아니라 프로그래밍 언어적 특성을 활용한 조작이 가능하다.

#### DOM 조작

- Document는 문 서 한 장에 해당하고 이를 조작하ㅡㄴ 것이다.
- DOM 조작 순서
  1. 선택(Select)
  2. 변경(Manipulation)



#### DOM 관련 객체의 상속 구조

- EventTarget
  - Event Listener를 가질 수 있는 객체가 구현하는 DOM 인터페이스
- Node
  - 여러가지 DOM 타입들이 상속하는 인터페이스

- Element
  - Document 안의 모든 객체가 상속하는 가장 범용적인 인터페이스
  - 부모인 Node와 그 부모인 EventTarget의 속성을 상속
- Document
  - 브라우저가 불러온 웹 페이지를 나타낸다.
  - DOM 트리의 진입점(entry point)역할을 수행한다.
- HTMLElement
  - 모든 종류의 HTML 요소
  - 부모 element의 속성을 상속



### DOM 선택 - 관련 메서드

#### document.querySelector(selector)

- 제공한 선택자와 일치하는 element하나 선택
- 제공한 CSS selector를 만족하는 첫 번째 element 객체를 반환(없다면 null)

#### document.querySelectorAll(selector)

- 제공한 선택자와 일치하는 여러 element를 선택
- 매칭할 하나 이상의 셀렉터를 포함하는 유효한 CSS selector를 인자(문자열)로 받는다.
- 지정된 셀렉터에 일치하는 **NodeList를 반환**한다.
  - NodeList는 유사 배열이고 forEach를 이용하여 반복을 편하게 할 수 있다.



- 이 두가지 는 id, class 그리고 tag선택자 등을 모두 사용가능하므로 더 구체적이고 유연하게 선택할 수 있기에 위 두 메서드를 주로 사용하도록 한다.



#### DOM 선택- HTMLCollection & NodeList

- 둘다 배열과 같이 각 항목에 접근하기 위한 index를 제공(유사배열)

#### HTMLCollection

- name, id, index속성으로 각 항목에 접근이 가능하다.

#### NodeList

- index로만 각 항목에 접근 가능
- 단, HTMLCollection과 달리 배열에서 사용하는 for Each 메서드 및 다양한 메서드 사용 가능



둘 다LiveCollection으로 DOM의 변경사항을 실시간으로 반영하지만, 

querySelectorAll()에 의해 반환되는 NodeList는 Static Collection으로 실시간으로 반영되지 않는다.



#### DOM 선택 - Collection

- Live Collection

  - 문서가 바뀔 때마다 실시간으로 업데이트 된다

  - DOM의 변경사항을 실시간으로 collection에 반영

  - ex) HTMLCollection, NodeList

    

- Static Collection (non-live)

  - DOM이 변경되어도 collection 내용에는 영향을 주지 않는다.
  - querySelectorAll()의 반환 NodeList만 static collection



### DOM 변경, 변경관련 메서드

#### Creation

- document.createElement()
  - 작성한 태그 명의 HTML 요소를 생성하여 반환한다.



#### XSS(Cross-site Scripting)

- 공격자가 입력 요소를 사용하여(<input>) 웹 사이트 클라이언트 측 코드에 악성 스크립트를 삽입해 공격하는 방법

- 피해자(사용자)의 브라우저가 악성 스크립트를 실행하며 공격자가 액세스 제어를 우회하고 사용자를 가장할 수 있도록 함

 





---

## 🌱 DOM 조작 실습

#### Event(이벤트) 개념

- **네트워크 활동**이나 **사용자와의 상호작용** 같은 사건의 **발생**을 **알리기 위한 객체**
- 이벤트 발생
  - 마우스 클릭, 키보드 누르는 등 사용자 행동으로 발생할 수 있음
  - 특정 메서드를 호출하여 프로그래밍적으로도 만들어 낼 수 있다.



#### Event 기반 인터페이스

- AnimationEvent, ClipborardEvent, DragEvent 등
- UIEvent
  - 간단한 사용자 인터페이스 이벤트
  - Event의 상속을 받음
  - MouseEvent, KeyboardEvent, InputEvent, FocusEvent 등의 부모 객체 역할을함



### Event handler

- EventTarget.addEventListener()
  - 지정한 이벤트가 대상에 전달될 때마다 **호출할 함수**를 설정한다.
  - 이벤트를 지원하는 모든 객체를 대상으로 지정 가능하다.
  - addEventListener(type, listener[, options])
    - type 반응할 이벤트 유형(대소문자 구분 문자열)
  - listener
    - 지정된 타입의 이벤트가 발생했을 때 알림을 받는 객체
    - EventListener 인터페이스 혹은 JS function 객체(콜백  함수)여야 한다.





### DOM관련 객체의 상속 구조 복습

- EventTarget
  - Event Listener를 가질 수 있는 객체가 구현하는 DOM 인터페이스



#### Event 취소

- event.preventDefault()
- 현재 이벤트의 기본 동작을 중단
- HTML 요소의 기본 동작을 작동하지 않게 막는다.
  - A태그의 기본동작은 클릭시 링크로 이동/ form 태그의 기본 동작은 form 데이터 전송
- 이벤트를 취소할 수 있는 경우, 이벤트의 전파를 막지않고 그 이벤트를 취소한다.





