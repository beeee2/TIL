# JavaScript01 

## JavaScript Intro

#### 동작방식

- 지난 주 까지 서버입장에서 어떻게 사용자의 요청을 분석하고 어떤 비즈니스 로직에 맞게 응답을 줄 것인가에 대해 학습했다.



#### JavaScript의 필요성

- 브라우저 화면을 ' 동적'으로 만들기 위함
- 브라우저를 조작할 수 있는 **유일한 언어**



#### 브라우저에서 할 수 있는 일 

- DOM(Document Object Model) 조작
  - Dom 조작이란 문서(HTML) 조작을 뜻한다.
- BOM(Browser Object Model) 조작
  - navigator, screen, location, frames, history, XHR
- JavaScript Core(ECMAScript)
  - 위 의 두가지를 하기 위해 자바스크립트 코어가 필요하다.
  - Data Structure(Object, Array), Conditional Expression, Iteration



#### DOM이란? 

- **HTML, XML**과 같은 문서를 다루기 위한 프로그래밍 인터페이스
- **문서를 구조화**하고, 구조화된 **구성 요소를 하나의 객체**로 **취급**하여 다루는 논리적 트리 모델
- 문서가 객체(object)로 구조화되어 있으며 **key로 접근 가능**
- 단순한 속성 접근, 메서드 활용 뿐만 아니라 **프로그래밍 언어적 특성을 활용한 조작 가능**
- 주요 객체
  - window : DOM을 표현하는 창(브라우저 탭), 최상위 객체(작성 시 생략 가능)
  - document : 페이지 컨텐츠의 Entry Point 역할을 하며, <head>, <body>등과 같은 수많은 다른 요소들을 포함
  - navigator, location, history, screen



#### DOM - 해석

- 파싱(Parsing)
  - 구문 분석, 해석
  - 브라우저가 문자열을 해석하여 DOM Tree로 만드는 과정



#### BOM이란?

- Brower Object Model
- 자바스크립트가 브라우저와 소통하기 위한 모델
- 브라우저의 창이나프레임을 추상화해서 **프로그래밍적으로 제어할 수 있도록 제공**하는 수단
  - 버튼, url 입력창, 타이틀 바 등 브라우저 윈도우 및 웹 페이지 일부분을 제어 가능
- window 객체는 모든 브라우저로부터 지원받으며 브라우저의 창(window)를 지칭



#### JavaScript Core

- 브라우저(DOM & BOM)을 조작하기 위한 명령어 약속(언어)



***💁‍♀️ 브라우저(BOM)와 그 내부의 문서(DOM)을 조작하기 위해 ECMAScript(JS)를 학습해보자.***

---



## ECMAScript

### ECMA?

- ECMA ( EMCA International)
  - 정보 통신에 대한 표준을 제정하는 비영리 표준화 기구
- ECMAScript는 ECMA에서 ECMA-262*규격에 따라 정의한 언어
  - ECMA-262* : 범용적인 목적의 프로그래밍 언어에 대한 명세
- ECMA Script6는 ECMA에서 제안하는 6번째 표준 명세를 말한다.



#### 세미콜론(semicolon)

- 자바스크립트는 세미콜론을 선택적으로 사용 가능하다.
- 세미콜론이 없으면 ASI*에 의해 자동으로 세미콜론이 삽입된다.
  - ASI* : 자동 세미콜론 삽입 규칙, Automatic Semicolon Insertion



#### 코딩 스타일 가이드

- 코딩 스타일의 핵심은 합의된 원칙과 일관성
  - 절대적인 하나의 정답은 없으며, 상황에 맞게 원칙을 정하고 일관성 있게 사용하는 것이 중요하다.
- 코딩 스타일은 코드의 품질에 직결되는 중요한 요소
  - 코드의 가독성, 유지보수 또는 팀원과의 커뮤니케이션 등 개발 과정 전체에 영향을 끼친다.





### 변수와 식별자

#### 식별자 정의와 특징

- 식별자(identifier)는 변수를 구분할 수 있는 변수명을 말한다.
- 식별자는 반드시 문자, 달러($) 또는 밑줄(_)로 시작한다.
- 대소문자를 구분하며, 클래스명 외에는 모두 소문자로 시작한다.
- 예약어* 사용이 불가능하다.
  - for, if, function등



#### 식별자 작성 스타일

- 카멜 케이스
  - 변수, 객체, 함수에 사용한다.
  - 두 번째 단어의 첫 글자부터 대문자
- 파스칼 케이스
  - 클래스, 생성자에 사용한다.
  - 모든 단어의 첫 번째 글자를 대문자로 작성한다.
- 대문자 스네이크 케이스
  - 상수에 사용한다.
    - 상수의 정의: 개발자의 의도와 상관없이 변경될 가능성이 없는 값을 의미한다.
  - 모든 단어를 대문자로 작성하며, 단어 사이에 언더스코어를 삽입한다.



#### 변수 선언 키워드(let, const)

- let
  - 재할당 할 예정인 변수 선언 시 사용
  - 변수 재선언 불가능
  - 재할당 가능
  - 블록 스코프*
- const
  - 재할당할 예정이 없는 변수 선언 시 사용
  - 변수 재선언 불가능
  - 재할당 불가능
  - 블록 스코프 *



#### 선언, 할당, 초기화

- 선언(Declaration)
  - 변수를 생성하는 행위 또는 시점
- 할당(Assignment)
  - 선언된 변수에 값을 저장하는 행위 또는 시점
- 초기화(Initialization)
  - 선언된 변수에 처음으로 값을 저장하는 행위 또는 시점



#### 블록 스코프* (block scope)

- if, for, 함수 등의 중괄호 내부를 가리킨다.
- 블록 스코프를 가지는 변수는 블록 바깥에서 접근이 불가능하다.



#### 변수 선언 키워드 var

- var
  - var로 선언한 변수는 재선언 및 재할당이 모두 가능하다.
  - ES6 이전에 변수를 선언할 때 사용되던 키워드
  - 호이스팅 되는 특성으로 인해 예기치 못한 문제가 발생할 가능성이 있다.
    - 따라서 ES6 이후부터는 var 대신 let을 사용하는 것을 권장한다.
  - 함수 스코프*



#### 함수 스코프*(function scope)

- 함수의 중괄호 내부를 가리킨다.
- 함수 스코프를 가지는 변수는 함수 바깥에서 접근이 불가능하다.



#### 호이스팅*(hoisting)

- 변수를 선언 이전에 참조할 수 있는 현상
- 변수 선언 이전의 위치에서 접근 시 undefined를 반환한다.



---



## 데이터 타입

#### 데이터 타입 종류

- 자바스크립트의 모든 값은 특정한 데이터 타입을 가진다.
- 크게 원시타입*(Primitice type)과 참조타입(Reference type)으로 분류된다.
  - 원시 타입
    - Numver, String, Boolean, undefined, null, Symbol
  - 참조 타입
    - Objects, Array, Function ...etc



#### 원시타입(Primitive type)

- 객체(object)가 아닌 기본 타입
- 변수에 해당 타입의 값이 담긴다.
- 다른 변수에 복사할 때 실제 값이 복사된다.



- 참조타입(Reference type)
  - 객체(object) 타입의 자료형
  - 변수에 해당 객체의 참조 값이 담긴다.
  - 다른 변수에 복사할 때 참조 값이 복사된다.



- 원시타입(Primitive type) - 숫자
  - 정수, 실수 구분 없는 하나의 숫자 타입
  - 부동소수점 형식을 따른다.
  - NaN(Not-A-Number)
    - 게산 불가능한 경우 반환되는 값
- 원시타입(Primitive type) - 문자열(String) 타입
  - 텍스트 데이터를 나타내는 타입
  - 16비트 유니코드 문자의 집합
  - 작은 따옴표 또는 큰 따옴표 모두 가능하다.
  - 템플릿 리터럴(Template Literal)
    - ES6부 지원
    - 따옴표 대신 bacttick으로 표현
    - ${expression}  형태로 표현식 삽입이 가능하다.

- 원시타입(Primitive type) - undefined
  - 변수의 값이 없음을 나타내는 데이터 타입
  - 변수 선언 이후 직접 값을 할당하지 않으면, 자동으로 undefined가 할당된다.
- 원시타입(Primitive type) - null
  - 변수의값이 없음을 의도적으로 표현할 때 사용하는 데이터 타입
  - null타입과 typeof 연산자
    - typeof 연산자 : 자료형 평가를 위한 연산자
    - null타입은 ECMA 명세의 원시 타입의 정의에 따라 원시 타입에 속하지만, typeof 연산자의 결과는 객체로 표현된다.

- 원시타입(Primitive type) - Boolean 타입
  - 논리적 참 또는 거짓을 나타내는 타입
  - true 또는 false로 표현
  - 조건문 또는 반복문에서 유용하게 사용한다.
    - 조건문 또는 반복문에서 boolean이 아닌 데이터 타입은 자동 형변환 규칙에 따라 true 또는 false로 변환된다.
      - Object는 항상 참이다.



#### undefined 타입과 null 타입 비교

- undefined
  - 빈 값을 표현하기 위한 데이터 타입
  - 변수 선언 시 아무 값도 할당하지 않으면, 자바스크립트가 자동으로 할당
  - typeof 연산자의 결과는 undefined
- null
  - 빈 값을 표현하기 위한 데이터 타입
  - 개발자가 의도적으로 필요한 경우 할당
  - typeof 연산자의 결과는 object



#### 참조타입

- 함수, 배열, 객체



---



## 연산자

#### 할당 연산자

- 오른쪽에 있는 피연산자의 평가 결과를 왼쪽 피 연산자에 할당하는 연산자
- 다양한 연산에 대한 단축 연산자 지원
- Increment 및 Decrement 연산자
  - Increment ++ : 피연산자의 값을 1 증가시키는 연산자
  - decrement -- : 피연산자의 값을 1 감소시키는 연산자
  - Airbnb Style Guide 에서는 += 또는 -= 와 같이 더 분명한 표현으로 적을 것을 권장한다.

#### 비교 연산자

- 피연산자들(숫자, 문자, Boolean등)을 비교하고 결과값을 boolean으로 반환하는 연산자
- 문자열은 유니코드 값을 사용하며 표준 사전 순서를 기반으로 비교한다.
  - ex) 알파벳 끼리 비교할 경우
    - 알파벳 순서상 후순위가 더 크다.
    - 소문자가 대문자보다 더 크다.

#### 동등 비교 연산자(==)

- 두 피연산자가 같은 값으로 평가되는 지 비교 후 boolean값을 반환
- 비교할 때 암묵적 타입 변환을 통해 타입을 일치시킨 후 같은 값인지 비교
- 두 피연산자가 모두 객체일 경우 메모리의 같은 객체를 바라보는 지 판별
- 예상치 못한 결과가 발생할 수 있으므로 특별한 경우를 제외하고 사용하지 않는다.

#### 일치비교 연산자 (===)

- 두 피연산자가 같은 값으로 평가되는지 비교 후 boolean 값을반환
- 엄격한 비교가 이뤄지며 암묵적 타입 변환이 발생하지 않음
  - 엄격한 비교 : 두비교대상의 타입과 값 모두 같은지 비교하는 방식
- 두 피연산자가 모두 객체일 경우 메모리의 같은 객체를 바라보는지 판별

#### 논리 연산자

- 세 가지 논리 연산자로 구성
  - and &&
  - or ||
  - not !
- 단축 평가 지원
  - false && false => false
  - true || false => true

#### 삼항 연산자

- 세개의 피연산자를 사용하여 조건에 따라 값을 반환하는 연산자
- 가장 왼쪽의 조건식이 참이면 콜란 앞의 값을 사용하고 그렇지 않으면 콜론 뒤의 값을 사용한다.
- 삼항 연산자의 결과 값이기 때문에 변수에 할당 가능하다.



---

## 조건문

#### 조건문의 종류와 특징

- 'if' statement
  - 조건 표현식의 결과값을 Boolean 타입으로 변환 후 참/거짓을 판단한다.
  - if, else if,  else
    - 조건은 소괄호(condition) 안에 작성
    - 실행할 코드는 중괄호{}안에 작성한다.
    - 블록 스코프를 새엇ㅇ한다.
- 'switch' statement
  - 조건 표현식의 결과값이 어느 값case에 해당하는지 판별한다.
  - 주로 특정 변수의 값에 따라 조건을 분기할 때 활용한다. 조건이 많아질 경우 if문보다 가독성이 나을 수있음 
  - 표현식의 결과값을 이용한 조건문
  - 표현식의 결과값과 case문의 오른쪽 값을 비교한다.
  - break 및 default문은 선택적으로 사용 가능하다.
  - break문이 없는 경우 break문을 만나거나 default문을 실행할 때까지 다음 조건문을 실행한다.
  - 블록 스코프를 생성한다.

---

## 반복문

#### 반복문의 종류와 특징

- while
  - 조건문이 참인동안 반복 시행
  - 조건은 소괄호 안에 작성
  - 실행할 코드는 중괄호 안에 작성한다
  - 블록 스코프를 생성한다.
- for
  - 세미콜론으로 구분되는 세 부분으로 작성된다.
  - initialization
    - 최초 반복문 진입 시 1회만 실행되는 부분
  - condition
    - 매 반복 시행 전 평가되는 부분
  - expression
    - 매 반복 시행 이후 평가되는 부분
  - 블록스코프 생성
- for ... in
  - 주로 객체object의 속성들을 순회할 때 사용한다.
  - 배열도 순회 가능하지만 인덱스 순으로 순회한다는 보장이 없으므로 권장하지 않는다.
- for ... of
  - 배열순회에 적합하다.
  - 객체순회에 사용할 수 없다.
  - 반복가능한 객체를 순회하며 값을 꺼낼 때 사용한다.
  - 반복가능한 객체의 종류 : Array, Map, Set, String 등

---



# 🌱 함수

#### 함수 in JavaScript

- 참조 타입 주 하나로써 function 타입에 속한다.
- JavaScript에서 함수를 정의하는 방법은 주로 2가지로 구분된다.
  - 함수 선언식 (function declaration)
  - 함수 표현식 (function expression)

- JavaScript 의 함수는 일급객체(First-class citizen)에 해당
  - 일급객체 : 다음의 조건들을 만족하는 객체를 의미함
    - **변수에 할당** 가능
    - 함수의 **매개변수로 전달** 가능
    - 함수의 **반환 값**으로 사용 가능



### 선언식 vs 표현식

#### 함수 선언식(function statement, declaration)

- 함수의 이름과 함께 정의하는 방식
- 3가지 부분으로 구성 
  - 함수의 이름(name)
  - 매개변수 (args)
  - 몸통(중괄호 내부)

```javascript
function name(args) {
    // do something
}

function add(num1, num2) {
    return num1 + num2
}
add(1, 2)
```

#### 함수 표현식(function expression)

- 함수를 표현식 내에서 정의하는 방식
  - 표현식 : 어떤 하나의 값으로 결정되는 코드의 단위
- 함수의 이름을 생략하고 익명 함수로 정의 가능하다
  - 익명함수(anonymous function) : 이름이 없는 함수
  - 익명함수는 함수 표현식에서만 가능하다.
- 3가지 부분으로 구성
  - 함수의 이름(생략가능)
  - 매개변수(args)
  - 몸통 (중괄호 내부)

```javascript
const name = function (args) {
    // do something
}

const add = function (num1, num2) {
    return num1 + num2
}
add(1,2)
```

#### 함수 선언식과 표현식 비교 정리

|        | 함수 선언식(declaration)                         | 함수 표현식(expression)                          |
| ------ | ------------------------------------------------ | ------------------------------------------------ |
| 공통점 | 데이터 타입, 함수 구성요소(이름, 매개변수, 몸통) | 데이터 타입, 함수 구성요소(이름, 매개변수, 몸통) |
| 차이점 | 익명 함수 불가능, 호이스팅이 가능하다            | 익명함수가 가능하다. 호이스팅이 불가능하다.      |
| 비고   |                                                  | Airbnb Style Guide에서 권장한다.                 |

#### 함수의 타입

- 선언식 함수와 표현식 함수 모두 타입은 function으로 동일하다.

  ```javascript
  // 함수 표현식
  const add = function (args) {}
  // 함수 선언식
  function sub(args) {}
  
  console.log(typeof add) // function
  console.log(typeof sub) // function

#### 호이스팅(hoisting) - 함수 선언식

- 함수 선언식으로 선언한 함수는 var로 정의한 변수처럼 hoisting이 발생한다.

- 함수 호출 이후에 선언해도 동작한다.

  ```javascript
  add(2, 7) // 9
  function add (num1, num2) {
      return num1 + num2
  }
  ```

#### 호이스팅(hoisting) - 함수 표현식

- 반면 함수 표현식으로 선언한 함수는 함수 정의 전에 호출 시 에러가 발생한다.

- 함수 표현식으로 정의된 함수는 변수로 평가되어 변수의 scope 규칙을 따른다.

  ```java
  sub(7, 2) // Uncaught ReferenceError : Cannot access 'sub' before initialization
      
  const sub = function (num1, num2) {
      return num1 - num2
  }





#### 기본인자(default arguments)

- 인자 작성 시 '=' 문자 뒤 기본 인자 선언 가능

```javascript
const greeting = function (name='Anonymous') {
    return `Hi ${name}`
}
greeting() // Hi Anonymous
```

#### 매개변수와 인자의 개수 불일치를 허용한다.

- 매개변수보다 인자의 개수가 많을 경우,

  ```javascript
  const noArgs = function() {
      return 0
  }
  
  noArgs(1, 2, 3) // 0
  
  const twoArgs = function (arg1, arg2) {
      return [arg1, arg2]
  }
  
  twoArgs(1, 2, 3) // [1, 2]
  ```

- 매개변수보다 인자의 개수가 적을 경우,

  ``` javascript
  const threeArgs = function (arg1, arg2, arg3) {
      return [arg1, arg2, arg3]
  }
  
  threeArgs()			// [undefined, undefined, undefined]
  threeArgs(1)		// [1, undefined, undfined]
  threeArgs(1,2)		// [1, 2, undefined]
  ```

#### Rest operator

- **rest operator(...)**를 사용하면 함수가 정해지지 않은 수의 매개변수를 **배열**로 받는다.(python의 *args와 유사하다.)

  - 만약 rest operator로 처리한 매개변수에 인자가 넘어오지 않을 경우에는, 빈 배열로 처리한다.

  ```javascript
  const restOpr = function (arg1, arg2, ...restArgs) {
      return [arg1, arg2, restArgs]
  }
  
  restArgs(1,2,3,4,5) // [1,2,[3, 4, 5]]
  restArgs(1, 2) //[1, 2, []]
  ```

#### Spread operator

- **spread operator(...)**를 사용하면 **배열인자를 전개**하여 전달 가능하다.

  ```javascript
  const spreadOpr = function (arg1, arg2, arg3) {
      return arg1 + arg2 + arg3
  }
  
  const numbers = [1, 2, 3]
  spreadOpr(...numbers) // 6
  
  ```

  



---

## 💁‍♀️ Arrow Function

#### 화살표 함수(Arrow Function)

- 함수를 비교적 간결하게 정의할 수 있는 문법

- function 키워드 생략 가능

- 함수의 매개변수가 단 하나 뿐이라면, '()'도 생략가능하다.

- 함수 몸통이표현식 하나라면 '{}'과 return도 생략 가능하다.

  ```javascript
  const arrow1 = function (name) {
      return `hello, ${name}`
  }
  
  // 1. function 키워드를 삭제한다.
  const arrow2 = (name) => {return `hello, ${name}`}
  
  // 2. 매개변수가 1개일 경우에만 () 생략이 가능하다.
  const arrow3 = name => {return `hello, ${name}`}
  
  // 3. 함수 바디가 return을 포함한 표현식 한개 일겨웅에는 {} & return을 삭제할 수 있다.
  const arrow4 = name => `hello, ${name}`



---

## 💁‍♀️ 문자열 (String)

#### 문자열 관련 주요 메서드 목록

| 메서드   | 설명                                            | 비고                                              |
| -------- | ----------------------------------------------- | ------------------------------------------------- |
| includes | 특정 문자열의 존재여부를 참/ 거짓으로 반환한다. |                                                   |
| split    | 문자열을 토큰 기준으로 나눈 배열 반환한다.      | 인자가 없으면 기존 문자열을 배열에 담아 반환한다. |
| replace  | 해당 문자열을 대상 문자열로 교체하여 반환한다.  | replaceAll                                        |
| trim     | 문자열의 좌우 공백을 제거하여 반환한다.         | trimStart, trimEnd                                |



#### includes

- string.includes(value)

  - 문자열에 value가 존재하는 지 판별 후 참또는 거짓을 반환한다.

  ```javascript
  const str = 'a santa at nasa'
  str.includes('santa') // true
  str.includes('asan') // false
  ```

#### split

- string.split(value)

  - value가 없을 경우, 기존 문자열을 배열에 담아 반환한다.
  - value가 빈 문자열일 경우 각 문자로 나눈 배열을 반환한다.
  - value가 기타 문자열일 경우 해당 문자열로 나눈 배열을 반환한다.

  ```javascript
  const str = 'a cup'
  str.split()	// ['a cup']
  str.split('')	// ['a',' ', 'c','u','p']
  str.split(' ')	// ['a', 'cup']
  ```

#### replace

- string.replace(from, to)

  - 문자열에 from 값이 존재할 경우, 1개만 to 값으로 교체하여 반환한다.

- string.replaceAll(from, to)

  - 문자열에 from 값이 존재할 경우, 모두 to 값으로 교체하여 반환한다.

  ```javascript
  const str = 'a b c d'
  str.replace(' ', '-') // 'a-b c d'
  str.replaceAll(' ', '-') // 'a-b-c-d'
  ```

#### trim

- string.trim()

  - 문자열 시작과 끝의 모든 공백문자(스페이스, 탭, 엔터 등)을 제거한 문자열을 반환한다.

- string.trimStart()

  - 문자열 시작의 공백문자(스페이스, 탭, 엔터 등)를 제거한 문자열 반환

- string.trimEnd()

  - 문자열 끝의 공백문자(스페이스, 탭, 엔터 등)를 제거한 문자열 반환

  ```javascript
  const str = ' hello '
  
  str.trim() // 'hello'
  str.trimStart() //'hello '
  str.trimEnd() //' hello'
  ```

  

  



---

## 🌱 배열 (Arrays)

#### 배열의 정의와 특징

- 키와 속성들을 담고 있는 참조 타입의 **객체(object)**
- **순서를 보장**하는 특징이 있음 
- 주로 대괄호를 이용하여 생성하고, 0을 포함한 **양의 정수 인덱스**로 특정 값에 접근이 가능하다.
- **배열의 길이는 array.length 형태**로 접근 가능하다.
  - 배열의 마지막 원소는 **array.length -1**로 접근

```javascript
const numbers = [1, 2, 3,  4, 5]
console.log(numbers[0])//1
console.log(numbers[-1])//undefined
console.log(numbers.length)//5

console.log(numbers[numbers.length - 1])//5
console.log(numbers[numbers.length - 2])//4
console.log(numbers[numbers.length - 3])//3
console.log(numbers[numbers.length - 4])//2
console.log(numbers[numbers.length - 5])//1
```



### 배열관련 주요 메서드

| 메서드          | 설명                                                    | 비고                          |
| --------------- | ------------------------------------------------------- | ----------------------------- |
| reverse         | 원본 배열의 요소들의 순서를 반대로 정렬한다             |                               |
| push & pop      | 배열의 가장 뒤에 요소를 추가 또는 제거한다.             |                               |
| unshift & shift | 배열의 가장 앞에 요소를 추가 또는 제거한다.             |                               |
| includes        | 배열에 특정 값이 존재하는지 판별 후 참/거짓을 반환한다. |                               |
| indexOf         | 배열에 특정 값이 존재하는지 판별 후 인덱스를 반환한다.  | 요소가 없을 경우 -1 반환한다. |
| join            | 배열의 모든 요소를 구분자를 이용하여 연결한다.          | 구분자 생략 시 쉼표기준이다.  |

#### reverse

- array.reverse()

  - 원본 배열의 요소들의 순서를 반대로 정렬한다.

  ```javascript
  const numbers = [1, 2, 3, 4, 5]
  numbers.reverse()
  console.log(numbers) // [5, 4, 3, 2, 1]
  ```

- push & poop

  - array.push() : 배열의 가장 뒤에 요소를 추가한다.
  - array.pop() : 배열의 가장 마지막 요소를 제거한다.

  ```javascript
  const numbers = [1, 2, 3, 4, 5]
  
  numbers.push(100)
  console.log(numbers) // [1,2,3,4,5,100]
  numbers.pop()
  console.log(numbers) // [1,2,3,4,5]
  ```

#### unshift & shift

- array.unshift() 

  - 배열의 가장 앞에 요소를 추가한다.

- array.shift()

  - 배열의 첫번째요소를 제거한다.

  ```javascript
  const numbers = [1, 2, 3, 4, 5]
  
  numbers.unshift(100)
  console.log(numbers) // [100, 1, 2, 3, 4, 5]
  
  numbers.shift()
  console.log(numbers) // [1, 2, 3, 4, 5]
  ```

#### includes

- array.includes(value)

  - 배열에 특정 값이 존재하는지 판별 후 참 또는 거짓 반환

  ```javascript
  const numbers = [1, 2, 3, 4, 5]
  console.log(numbers.includes(1)) // true
  console.log(numbers.includes(100)) // false
  ```

#### indexOf

- array.indexOf(value)

  - 배열에 특정 값이 존재하는지 확인 후 가장 첫 번째로 찾은 요소의 인덱스를 반환한다.
  - 만약 해당 값이 없을 경우 -1을 반환한다.

  ```javascript
  const numbers = [1, 2, 3, 4, 5,]
  let result
  
  result = numbers.indexOf(3) // 2
  console.log(result)
  
  result = numbers.indexOf(100) // -1
  console.log(result)
  ```

#### join

- array.join([separator])

  - 배열의 모든 요소를 연결하여 반환한다.
  - separator(구분자)는 선택적으로 지정가능하며, 생략 시 쉼표를 기본 값으로 사용한다.

  ```javascript
  const numbers = [1, 2, 3, 4, 5]
  let result
  
  result = numbers.join()
  console.log(result) // 1,2,3,4,5
  result=numbers.join('')
  console.log(result) //12345
  result= numbers.join(' ')
  console.log(result) // 1 2 3 4 5
  result = numbers.join('-') 
  console.log(result) // 1-2-3-4-5
  
  ```

#### Spread operator(...)

- 배열내부에서 배열 전개가 가능하다.

- ES5까지는 Array.concat()메서드를 사용한다.

- 얕은 복사에 활용 가능하다.

  ```javascript
  const array = [1, 2, 3]
  const newArray= [0, ...aray, 4]
  
  console.log(newArray) // [0, 1, 2, 3, 4]
  ```



### 배열관련 메서드 목록(2)

- 배열을 순회하며 특정 로직을 수행하는 메서드

- 메서드 호출 시 인자로 callback 함수를 받는 것이 특징이다.

  - **callback 함수 : 어떤 함수의 내부에서 실행될 목적으로 인자로 넘겨받는 함수를 말한다.**

    | 메서드  | 설명                                                         | 비고         |
    | ------- | ------------------------------------------------------------ | ------------ |
    | forEach | 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행한다.          | 반환 값 없음 |
    | map     | 콜백 함수의 반환 값을 요소로 하는 새로운 배열을 반환한다.    |              |
    | filter  | 콜백 함수의 반환 값이 참인 요소들만 모아서 새로운 배열을 반환한다. |              |
    | reduce  | 콜백 함수의 반환 값들을 하나의 값(acc)에 누적 후 반환한다.   |              |
    | find    | 콜백 함수의 반환 값이 참이면 해당 요소를 반환한다.           |              |
    | some    | 배열의 요소 중 하나라도 판별 함수를 통과하면 참을 반환한다.  |              |
    | every   | 배열의 모든 요소가 판별함수를 통과하면 참을 반환한다.        |              |

    





#### forEach

- array.forEach(callback(element[, index[, array]]))

- 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행한다.
- 콜백 함수는 3가지 매개 변수로 구성된다.
  - element : 배열의 요소
  - index :배열의 인덱스
  - array : 배열자체
- **반환 값(return)이 없는 메서드**

```javascript
array.forEach((element, index, array) => {
    // do something
})

const fruits = ['딸기', '바나나', '수박', '사과', '체리']
fruits.forEach((fruit, index) => {
    console.log(fruit, index)
    // 딸기 0
    // 수박 1
    // 사과 2
    // 체리 3
})
```



#### map

- array.map(callback(element[, index[, array ]]))

- 배열의 각 **요소에 대해 콜백함수를 한 번씩 실행**

- 콜백 함수의 **반환값을 요소**로 하는 **새로운 배열을 반환**한다.

- 기존 배열 전체를 다른 형태로 바꿀 때 유용하다.

  ```javascript
  array.map((element, index, array) => {
      // do something
  })
  
  const numbers = [1, 2, 3, 4, 5]
  const doubleNums = numbers.map((num) => {
      return num*2
  })
  
  console.log(doubleNums)
  // [2, 4, 6, 8, 10]
  ```

  



#### filter

- 배열의 **각 요소에 대해 콜백 함수를 한 번씩 실행**
- 콜백 함수의 **반환 값이 참인 요소들**만 모아서 **새로운 배열을 반환**한다.
- 기존 배열의 요소들을 **필터링**할 때 유용하다.

```javascript
array.filter((element, index, array) => {
    // do something
})

const numbers = [1, 2, 3, 4, 5]
const oddNums = numbers.filter((num, index) => {
    return num % 2
})

console.log(oddNums) // 1 3 5
```





#### find 

- array.find(callback(element[, index[, array]]))
- 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행
- 콜백 함수의 **반환 값이 참이면, 조건을 만족하는 첫번째 요소를 반환**한다.
  - **하나**만 찾는다.
- 찾는 값이 **배열에 없으면 undefined를 반환**한다.
- 132p 수정

```javascript
array.find((element, index, array) => {
    // do something
})

const avengers = [
    {name:'Tony', age: 45},
    {name : 'Steve', age: 32},
    {name: 'Thor', age:40},
]

const result = avengers.find((avenger) => {
    return avenger.name === 'Tony'
})

console.log(result) // {name : 'Tony', age:45}
```





#### reduce

- array.reduce(callback(acc, element, [index[, array]])[, initialValue])
- 배열의 각 요소에 대해 콜백 함수를 한 번씩 실행
- 콜백 함수의 **반환 값들을 하나의 값(acc)에 누적 후 반환**
- reduce 메서드의 주요 매개 변수
  - **acc**
    - 이전 callback함수의 **반환 값이 누적되**는 변수
  - **initialValue**(optional)
    - **최초 callback함수 호출 시 acc에 할당되는 값****, default 값은 배열의 첫 번째 값**
- (참고) 빈배열의 경우 initialValue를 제공하지 않으면 에러가 발새한다.

- 배열을 순회하며 전체값을 줄여나가므로 reduce라고 한다.

```javascript
const numbers = [1, 2, 3]

const result = numbers.reduce((acc, num) => {
    return acc + num
},0 )

console.log(result) //6
```



#### some

- array.some(callback(element[, index[, array]]))

- 배열의 **요소 중 하나**라도 주어진 **판별 함수를 통과**하면 **참을 반환**한다.

- 모든 요소가 통과하지 못하면 거짓을 반환한다.

- 빈 배열은 항상 거짓을 반환한다.

  ```javascript
  array.some((element, index, array) => {
      //do something
  })
  
  const numbers =[1, 3, 5, 7, 9]
  
  const hasEvenNumber = numbers.some((num) => {
      return num % 2 === 0
  })
  console.log(hasEvenNumber) // false
  
  const hasOddNumber = numbers.some((num) => {
      return num % 2
  })
  
  console.log(hasOddNumber) // true
  
  ```

  

#### every

- array.every(callback(element[, index [, array]]))
- 배열의 **모든 요소**가 주어진 **판별 함수를 통과**하면 **참을 반환**한다.
- 하나의 요소라도 통과하지 못하면 거짓을 반환한다.
- **빈배열**은 **항상 참**을 반환한다.

```javascript
array.every((element, index, array) => {
    // do something
})

const numbers = [2, 4, 6, 8, 10]
const isEveryNumberEven = numbers.every((num) => {
    return num%2 === 0
})
console.log(isEveryNumberEven) // true

const isEveryNumberOdd = numbers.every((num) => {
    return num % 2
})
console.log(isEveryNumberOdd) // false
```



#### 배열 순회 방법 비교

| 방식       | 특징                                                         | 비교                         |
| ---------- | ------------------------------------------------------------ | ---------------------------- |
| for loop   | - 모든 브라우저 환경에서 지원<br />-인덱스를 활용하여 배열의 요소에 접근<br />- break, continue를 사용할 수 있다. |                              |
| for ... of | - 일부 오래된 브라우저 환경에서 지원하지 않는다.<br />- 인덱스 없이 배열의 요소에 바로 접근 가능하다.<br />-break, continue 사용이 가능하다. |                              |
| forEach    | - 대부분의 브라우저 환경에서 지원한다.<br />- break, continue 사용이 불가능하다. | Airbnb style guide 권장 방식 |

```javascript
const chars= ['a', 'b', 'c' ,'d']

//for loop
for (let idx=0;idx<chars.length; idx++) [
    console.log(idx, chars[idx])
]

// for .. of
for (const char of chars) {
    console.log(char)
}

// forEach
chars.forEach((char, idx) => {
    console.log(idx, char)
})

```



---

## 💁‍♀️ 객체(Objects)

#### 객체의 정의와 특징

- 객체는 속성(property)의 집합이며, 중괄호 내부에 key와 value의 쌍으로 표현한다.
- key는 문자열 타입만 가능하다.
  - key 이름에 띄어쓰기 등의 구분자가 있으면 따옴표로 표현한다.
- value는 모든 타입(함수포함)이 가능하다.
- 객체 요소 접근은 점 또는 대괄호로 가능하다.
  - key 이름에 띄어쓰기 같은 구분자가 있으면 대괄호 접근만 가능하다.

```javascript
const me = {
    name : 'jack',
    phoneNumber : '01023456789',
    'samsung products' : {
        budes: 'galaxy buds pro',
        galaxy : 'Galaxy s 20',
    },
}

console.log(me.name)
console.log(me.phoneNumber)
console.log(me['samsung products'])
console.log(me['samsung products'].buds)
```



#### 객체와 메서드

- 메서드는 객체의 속성이 참조하는 함수

- 객체.메서드명()으로 호출이 가능하다.

- 메서드 내부에서는 this 키워드가 객체를 의미한다.

  - fullName은 메서드가 아니기 때문에 정상출력이 되지 않는다.(NaN)
  - getFullName은 메서드 이기 때문에 해당 객체의 firstName과 lastName을 정상적으로 이어서 반환한다.

  ```javascript
  const me = {
      firstName : 'john',
      lastName : 'doe',
      fullName : this.firstName + this.lastname// NaN
      
      getFullName : fucntion () {
      return this.FirstName + this.lastName
  }
  }
  ```

  

#### 객체 관련 ES6 문법

1. 속성명 축약
2. 메서드명 축약
3. 계산된 속성명 사용
4. 구조 분해 할당(배열도 가능)
5. 객체 전개 구문(Spread Operator)



#### 속성명 축약(shorthand)

- 객체를 정의할 때 key와 할당하는 변수의 이름이 같은 예시와 같이 축약이 가능하다.

  ```javascript
  const books = ['learning JS', 'Learing Python']
  const magazines = ['Vogue', 'Science']
  
  //ES6+
  const bookShop = {
      books,
      magazings,
  }
  console.log(bookShop)
  /*
  
  {
  	books:['learning JS', 'Learing Python'],
  	magazinges : ['Vogue', 'Science']
  }
  */
  ```

  

#### 메서드명 축약

- 메서드 선언 시 function 키워드 생략 가능

``` javascript
const obj = {
    greeting() {
        console.log('HI')
    }
}

obj.greeting() // HI
```



#### 계산된 속성

- 객체를 정의할 때 KEY의 이름을 표혀식을 이용하여 동적으로 생성 가능하다.

  ```javascript
  const key = 'regions'
  const value = ['광주', '대전', '구미', '서울']
  
  const ssafy = {
      [key] : value,
  } 
  console.log(ssafy) // {regions: Array(4)}
  console.log(ssafy.regions) // ['광주', '대전', '구미', '서울']
  ```



#### 구조 분해 할당

- 배열 또는 객체를 분해하여 속성을 변수에 쉽게 할당할 수 있는 문법

  ```javascript
  const userInformation = {
      name : 'kim',
      userId : 'ssafy1234',
      phoneNumber : '010-1234-1234',
      email : 'ssafy@ssafy.com'
  }
  
  const {name} = userInformation
  const {userId} = userInformation
  const {phoneNumber} = userInformation
  const {email} = userInformation
  
  const {name, userId} = userInformation
  ```

  

#### Spread Operator

- spread operator(...)을 사용하면 객체 내부에서 객체 전개가 가능하다.
- ES5까지는 Object.assign() 메서드를 사용한다.
- 얕은 복사에 활용 가능하다.

``` javascript
const obj = {b:2, c:3, d:4}
const newObj = {a:1, ...obj, e:5}

console.log(newObj) // {a:1, b:2, c:3, d:4, e:5}
```



#### JSON(JavaScript Object Notation)

- key-value쌍의 형태로 데이터를 표기하는 언어 독립적 표준 포맷
- 자바스크립트의 객체와 유사하게 생겼으나 실제로는 문자열 타입이다.
  - 따라서 JS의 객체로써 조작하기 위해서는 구문 분석(parsing)이 필수적이다.



- 자바스크립트에서는 JSON을 조작하기 위한 두 가지 내장 메서드를 제공한다.
  - JSON.parse()
    - JSON => 자바스크립트 객체
  - JSON.stringify()
    - 자바스크립트 객체 => JSON

```javascript
//object => JSON
const jsonData = JSON.strignify({
    coffee : 'Americano',
    iceCream : 'Cookie and cream',
})

console.log(jsonData) //	"{"coffee":"Ameriacano".,...}"
console.log(typeof jsonData) //string

const parsedData = JSON.parse(jsonData)

console.log(parsedData) // {coffee: 'Ameircano', ...}
console.log(typeof parsedData) // object
```



---

## 💁‍♀️ this 정리

#### this is window? object?

- JS의 this는 실행 문맥에 따라 다른 대상을 가리킨다.
- class 내부의 생성자 함수
  - this는 생성되는 객체를 가리킨다.
- 메서드(객체.메서드명()으로 호출가능한 함수)
  - this는 해당 메서드가 소속된 객체를 가리킨다.
- 위의 두 가지 경우를 제외하면 모두 최상위 객체 window를 가리킨다.

```javascript
function getFullName() {
    return this.firstName + this.lastName
}
const me = {
    firstName : 'jonh',
    lastName : 'doe',
    getFullName: getFullName,
}

const you = {
    firstName: 'jack',
    lastName :'lee',
    getFullName : getFullName
}

me.getFullName()	//johndoe
you.getFullName()	// jacklee
getFullName()		//NaN
```



#### function 키워드와 화살표 함수 차이

- this.radiuses는 메서드(객체.메서드명()으로 호출이 가능하다.) 소속이기 때문에 정상적으로 접근이 가능하다.
- forEeach 의 콜백함수의 경우 메서드가 아니므로 객체.메서드명()식으로 호출이불가능한다.
- 때문에 콜백함수 내부의 this는 window가 되어 this.PI는 정상적으로 접근이 불가능하다.
- 이 콜백함수 내부에서 this.PI에 접근하기 위해서 함수객체.bind(this)메서드를 사용한다.
- 이 번거로운 bind과정을 없앤 것이 화살표 함수이다.

```javascript
const obj = {
    PI : 3.14,
    radiuses : [1, 2, 3, 4, 5],
    printArea : function() {
        this.radiuses.forEach(function (r) {
            console.log(this.PI * r * *r)
        }.bind(this))
    },
}

const obj = {
    PI : 3.14,
    radiuses : [1, 2, 3, 4, 5],
    printArea : function((r) => {
   	console.log(this.PI * r * r) 
}),
}
```



#### function 키워드와 화살표 함수의 차이

- 함수 내부에 this 키워드가 존재할 경우
  - 화살표 함수와 function 키워드로 선언한 함수가 다르게 동작한다.
- 함수 내부에 this 키워드가 존재하지 않을 경우
  - 완전히 동일하게 조작한다.



---

## 💁‍♀️ lodash

#### A modern Javascript utility Library

- 모듈성, 성능 및 추가 기능을 제공하는 JavaScript 유틸리티 라이브러리
- array, object 등 자료구조를 다룰 때 사용하는 유용하고 간편한 유틸리티 함수들을 제공한다.
- 함수 예시
  - reverse, sortBy, range, random, cloneDeep ...

```html
<body>
    <script src="https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js"></script>
    <script>
    // 위의 CDN import를 통해 _ (underscore) 식별자를 사요할 수 있다.
        
       	_.sample([1,2,3,4]) // 3(random 1 element)
        _.sampleSize([1,2,3,4], 2) // 2, 3
        _.reverse([1,2,3,4]) //[4,3,2,1]
        _.range(5)// [0,1,2,3,4]
        _.range(1,5) // [1, 2, 3,4]
        _.range(1,5,2)// [1, 3]
    </script>
</body>
```

- lodash를 사용하지 않을 경우, 깊은 복사는 직접 함수를 만들어서 구현해야 한다. (내장된 깊은 복사 관련 함수가 없다.)

```html
<body>
    <script src="https://cdn.jsdelivr.net/npm/lodash@4.17.21/lodash.min.js"></script>
    
    const original = {a: {b:1}}
    const ref = original
    const copy = _.cloneDeep(original)
    
    console.log(original.a.b,ref.a.b, copy.a.b) // 1, 1, 1
    ref.a.b = 10
    console.log(original.a.b, ref.a.b , copy.a.b) // 10, 10, 1
    copy.a.b = 100
    console.log(original.a.b, ref.a.b, copy.a.b)	// 10, 10, 100
</body>
```

