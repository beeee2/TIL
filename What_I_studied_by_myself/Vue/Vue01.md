# 🌱 Vue 01

## Intro

### Front-End Development

- HTML, CSS 그리고 JavaScript를 활용해서 *데이터를 볼 수 있게* 만들어 준다.
  - 이 작업을 통해 사용자(User)는 데이터와 상호작용 (Interaction)할 수 있다.



- 대표적인 프론트엔드 프레임워크
  - Vue.js, React, Angular



### Vue.js

- 사용자 인터페이스를 만들기 위한 진보적인 자바스크립트 프레임워크
- 현대적인 tool과 다양한 라이브러리를 통해 SPA(Single Page Application)를 완벽하게 지원한다.



### SPA

- Single Page Application (단일 페이지 애플리케이션)
- 현재 페이지를 동적으로 렌더링함으로써 사용자와 소통하는 웹 어플리케이션
- 단일 페이지로 구성되며 서버로부터 최초에만 페이지를 다운로드하고, 이후에는 동적으로 DOM을 구성한다.
  - 처음 페이지를 받은 이후부터는 서버로부터 새로운 전체 페이지를 불러오는 것이 아닌, 현재 페이지 중 필요한 부분만 동적으로 다시 작성한다.
- 연속되는 페이지 간의 사용자 경험(UX)을 향상
  - 모바일 사용량이 증가하고 있는 현재 트래픽의 감소와 속도, 사용성, 반응성의 향상은 매우 중요하다.
- 동작 원리의 일부가 CSR(Client Side Rendering)의 구조를 따른다.



### SPA 등장 배경

- 과거 웹 사이트들은 요청에 따라 매번 새로운 페이지를 응답하는 방식이었다.
  - MPA(Multi Page Application)

- 스마트폰이 등장하면서 모바일 최적화의 필요성이 대두됨
  - 모바일 네이티브 앱과 같은 형태의 웹 페이지가 필요해짐
- 이러한 문제를 해결하기 위해 Vue.js와같은 프론트엔드 프레임워크가 등장
  - CSR(Client Side Rendering), SPA(Single Page Application)의 등장
- 1개의 웹 페이지에서 여러 동작이 이루어지며 모바일 앱과 비슷한 형태의 사용자 경험을 제공



### CSR

- Client Side Rendering
- 서버에서 화면을 구성하는 SSR 방식과 달리 클라이언트에서 화면을 구성
- 최초 요청시 HTML, CSS, JS 등 데이터를 제외한 각종 리소스를 응답받고 이후 클라이언트에서 필요한 데이터만 요청해 JS로 DOM을 렌더링하는 방식
- 즉, 처음엔 뼈대만 받고 브라우저에서 동적으로 DOM을 그린다.
- SPA가 사용하는 렌더링 방식

- 장점
  1. 서버와 클라이언트 간 트래픽 감소
     - 웹 애플리케이션에 필요한 모든 정적 리소스를 최초에 한 번 다운로드 후 필요한 데이터만 갱신
  2. 사용자 경험(UX) 향상
     - 전체 페이지를 다시 렌더링하지 않고 변경되는 부분만을 갱신하기 때문
- 단점
  1. SSR에 비해 전체 페이지 최종 렌더링 시점이 느림
  2. SEO(검색 엔진 최적화)에 어려움이 있음(최초문서에 데이터 마크업이 없기 때문)



### SSR

- Server Side Rendering
- 서버에서 클라이언트에게 보여줄 페이지를 모두 구성하여 전달하는 방식
- JS 웹 프레임워크 이전에 사용되던 전통적인 렌더링 방식

- 장점
  1. 초기 구동속도가 빠름
     - 클라이언트가 빠르게 컨텐츠를 볼 수 있다.
  2. SEO(검색엔진최적화)에 적합
     - DOM에 이미 모든 데이터가 작성되어 있기 때문이다.
- 단점
  - 모든 요청마다 새로운 페이지를 구성하여 전달한다.
    - 반복되는 전체 새로고침으로 인해 사용자 경험이 떨어진다.
    - 상대적으로 트래픽이 많아 서버의 부담이 클 수 있다. 



### SSR & CSR

- 두 방식의 차이는 최종 HTML 생성 주체가 누구인가에 따라 결정된다.
- 즉, 실제 브라우저에 그려질(렌더링) HTML을 서버가 만든다면 SSR/클라이언트가 만든다면 CSR



- SSR과 CSR을 단순 비교하여 '어떤 것이 더 좋다'가 아니라, 내 서비스 또는 프로젝트 구성에 맞는 방법을 적절하게 선택하는 것이 중요하다.

- 예를 들어, Django에서 Axios를 활용한 좋아요/팔로우 로직의 경우 대부분은 Server에서 완성된 HTML을 제공하는 구조(SSR)

- 단, 특정 요소(좋아요/팔로우)만 JS(AJAX & DOM조작)를 활용(CSR)
  - AJAX를 활용해 비동기 요청으로 필요한 데이터를 클라이언트에서 서버로 직접 요청을 보내 받아오고 JS를 활용해 DOM을 조작한다.



### SEO

- Search Engine Optimization(검색 엔진 최적화)
- 웹 페이지 검색엔진이 자료를 수집하고 순위를 매기는 방식에 맞게 웹 페이지를 구성해서 검색 결과의 상위에 노출될 수 있도록 하는 작업
- 인터넷 마케팅 방법 중 하나
- 구글의 등장 이후 검색엔진들이 컨텐츠의 신뢰도를 파악하는 기초 지표로 사용된다.
  - 다른 웹 사이트에서 얼마나 인용되었나를 반영한다.
  - 결국 타 사이트에 인용되는 횟수를 늘리는 방향으로 최적화.

---



## Concepts of Vue.js

### MVVM Pattern

- 애플리케이션 로직을 UI로부터 분리하기 위해 설계된 디자인 패턴
- 구성요소
  1. Model
  2. View
  3. View Model



### MVVM

#### Model

- "Vue에서 Model은 Javascript의 Object다."
- Object === {key:value}
- Model은 Vue Instance 내부에서 data라는 이름으로 존재
- 이 data가 바뀌면 View(DOM)가 반응한다.

#### View

- "Vue에서 View는 DOM(HTML)이다."
- Data의 변화에 따라서 바뀌는 대상

#### ViewModel

- "Vue에서 ViewModel은 모든 Vue Instance이다."
- View와 Model 사이에서 Data와 DOM에 관련된 모든 일을 처리한다.
- ViewModel을 활용해 Data를 얼마만큼 잘 처리해서 보여줄 것인지(DOM)를 고민하는 것 



---

## 💁‍♀️ Basic syntax of Vue.js

### Vue instance

- 모든 Vue 앱은 Vue 함수로 새 인스턴스를 만드는 것부터 시작한다.
- Vue 인스턴스를 생성할 때는 Options 객체를 전달해야 한다.
- 여러 Options들을 사용하여 원하는 동작을 구현한다.
- Vue Instance === Vue Component

```javascript
const app = new Vue({
    
})
```



### Options/DOM - 'el'

- Vue 인스턴스에 연결(마운트)할 기존 DOM 요소가 필요하다.
- CSS 선택자 문자열 혹은 HTML Element로 작성한다.
- new를 이용한 인스턴스 생성때만 사용한다.

```javascript
const app = new Vue({
    el: "#app"
})
```



### Options/Data - 'data'

- Vue 인스턴스의 데이터 객체
- Vue 인스턴스의 상태 데이터를 정의하는 곳
- Vue template에서 interpolation을 통해 접근이 가능하다.
- v-bind, v-on과 같은 directive에서도 사용가능하다.
- Vue 객체 내 다른 함수에서 this 키워드를 통해 접근이 가능하다.

```javascript
const app = new Vue({
    el: "#app",
    data: {
        message: 'Hello',
    }
})
```



### Options/Data - 'methods'

- Vue 인스턴스에 추가할 메서드
- Vue template에서 interpolation을 통해 접근이 가능하다.
- v-on 과 같은 directive에서도 사용이 가능하다.
- Vue 객체 내 다른 함수에서 this 키워드를 통해 접근이 가느하다.
- 주의
  - 화살표 함수를 메서드를 정의하는데 사용하면 안된다.
  - 화살표 함수가 부모 컨텍스트를 바인딩하기 때문에, 'this'는 Vue 인스턴스가 아니다.

```javascript
const app = new Vue({
    el:"#app",
    data: {
        message: "Hello",
    },
    methods: {
        greeting: function() {
            console.log("hello")
        }
    }
})
```



### 'this' keyword in vue.js

- Vue 함수 객체 내에서 vue 인스턴스를 가리킨다.
- 단, 화살표 함수를 사용하면 안되는 경우
  1. data
  2. method 정의



---

## 💁‍♀️ Template Syntax

### Template Syntax

- 렌더링 된 DOM을 Vue 인스턴스의 데이터에 선언적으로 바인딩할 수 있는 HTML 기반 템플릿 구문을 사용한다.
  1. Interpolation
  2. Directive



### Interpolation (보간법)

1. Text
   - <s pan>메세지 : {{msg}} </span>
2. Raw HTML
   - <span v-html="rawHtml"></span>
3. Attribute
   - <d iv v-bind:id="dynamicId"></div>
4. JS 표현식
   - {{number + 1}}
   - {{message.split('').reverse().join('')}}



### Directive (디렉티브)

- v-접두사가 있는 특수 속성
- 속성 값은 단일 JS 표현식이 된다(v-for는 예외)
- 표현식의 값이 변경될 때 반응적으로 DOM에 적용하는 역할을 한다.



- 전달인자(Arguments)

  - ' : ' 를 통해 전달인자를 받을 수도 있음.

  ``` html
  <a v-bind:href="url">...</a>
  <a v-on:click="doSomething">...</a>
  ```

- 수식어(Modifiers)

  - '.' 점으로 표시되는 특수 접미사
  - directive를 특별한 방법으로 바인딩 해야 함을 나타낸다.

  ``` html
  <form v-on:submit.prevent="onSubmit">
      ...
  </form>
  ```

  

### v-text

- 엘리먼트의 textContent를 업데이트
- 내부적으로 interpolation 문법이 v-text로 컴파일 된다.

```html
<div id="app">
    <p v-text="message">
        아래와 동일
    </p>
    <p>
        {{message}}
    </p>
</div>
<!-- cdn 불러오기 -->
<script>
	const app = new Vue({
        el: '#app',
        data: {
            message: '아래와 동일',
        }
    })
</script>
```





### v-html

- 엘리먼트의 innerHTML을 업데이트
  - XSS 공격에 취약할 수 있다.
- 임의의 사용자로부터 입력받은 내용은 v-html에 **절대 사용 금지**

```html
<!DOCTYPE html>
<html lang="en">
    <head>
        <!--생략-->
    </head>
    <body>
        <div id="app">
            <div>Hello</div>
            <div v-html="myHtml"></div>
        </div>
    <script>
    	const app = new Vue({
            el: '#app',
            data: {
                myHtml: '<b>Hello</b>',
            }
        })    
    </script>
    </body>
</html>
```



### v-show

- 조건부 렌더링 중 하나
- 요소는 항상 렌더링 되고 DOM에 남아있음
- 단순히 엘리먼트에 display CSS 속성을 토글하는 것

```html
<div id="app">
    <p v-show="isTrue">
        true
    </p>
</div>
<script>
	const app = new Vue({
        el: "#app",
        data: {
            isTrue:true,
        }
    })
</script>
```



### v-if, v-else-if, v-else

- 조건부 렌더링 중 하나
- 조건에 따라 요소를 렌더링
- directive의 표현식이 true일 때만 렌더링
- 엘리먼트 및 포함된 directive는 토글하는 동안 삭제되고 다시 작성된다.

```html
<div id="app">
    <div v-if="seen">
        seen이 true일때만 렌더링된다.
    </div>
    
    <div v-if="myType === 'A'">
        A
    </div>
    <div v-if="myType === 'B'">
        B
    </div>
    <div v-if="myType === 'C'">
        C
    </div>
    <div v-else>
        Not A/B/C
    </div>
</div>

<script>
	const app = new Vue({
        el: '#app',
        data: {
            seen:true,
            myType:'A',
        }
    })
</script>
```





### v-show와 v-if

#### v-show (Expensive initial load, cheap toggle)

- CSS display 속성을 hidden으로 만들어 토글
- 실제로 렌더링은 되지만 눈에서 보이지 않는 것이기 때문에 딱 한 번만 렌더링이 되는 경우라면 v-if에 비해 상대적으로 렌더링 비용이 높다.
- 하지만, 자주 변경되는 요소라면 한 번 렌더링 된 이후부터는 보여주는지에 대한 여부만 판단하면 되기 때문에 토글 비용이 적음.

#### v-if(Cheap initial load, expensive toggle)

- 전달인자가 false인 경우 렌더링되지 않는다.
- 화면에서 보이지 않을 뿐만 아니라 렌더링 자체가 되지 않기 떄문에 렌더링 비용이 낮다.
- 하지만, 자주 변경되는 요소의 경우 다시 렌더링 해야하므로 비용이 증가할 수 있다.



#### v-for

- 원본 데이터를 기반으로 엘리먼트 또는 템플릿 블록을 여러 번 렌더링
- item in items 구문 사용
- item 위치의 변수를 각 요소에서 사용할 수 있음
  - 객체의 경우에는 key
- v-for 사용 시 반드시 **key 속성을 각 요소에 작성해야 한다.**
- v-if와 함께 사용하는 경우 v-for가 우선순위가 더 높다.
  - 단, **가능하면 둘다 동시에 사용하지 말 것.**

```html
<div id="app">
    <div v-for="fruit in fruits">
        {{fruit}}
    </div>
    <div v-for="(fruit, index) in fruits" :key="`fruit-${index}`">
        {{fruit}}
    </div>
    <div v-for="todo in todos" :key="todo.id">
        {{todo.title}} : {{todo.completed}}
    </div>
</div>
<script>
	const app = new Vue({
        el: "#app",
        data: {
            fruits: ['apple', 'banana', 'coconut'],
            todos: [
                {id:1, title:'todo1', completed: true},
            ]
        }
    })
</script>
```



### v-on

- 엘리먼트에 이벤트 리스너를 연결
- 이벤트 유형은 전달인자로 표시함
- 특정 이벤트가 발생했을 때, 주어진 코드가 실행된다.
- 약어
  - @
  - v-on:click->@click

```html
<div id="app">
    <button v-on:click="doAlert">
        BUTTON
    </button>
    <button @click="doAlert">
        BUTTON
    </button>
    <button @click="onInputEnter('saffy')">
        BUTTON
    </button>
    
    <form action="/articles/" @submit.prevent>
        <button>
            SUMBIT
        </button>
    </form>
    
    <input @keyup.enter="onEnter">
</div>
<script>
	const app = new Vue({
        el: '#app',
        data: {
            message: 'Hello Vue.js',
        },
        methods: {
            doAlert: function() {
                alert("hello")
            },
            onInputEnter: function(event) {
                console.log(event)
                console.log(event.target.value)
            },
            onEnter:function() {
                console.log(event),
                console.log(event.target.value)
            }
            
        }
    })
</script>

```



### v-bind

- HTML 요소의 속성에 Vue의 상태 데이터를 값으로 할당
- Object 형태로 사용하면 value가 true인 key가 class바인딩 값으로 할당
- 약어
  - :
  - v-bind:href-> :href

```html
<div id="app">
    <img v-bind:src="imageSrc">
    <img :src="imageSrc">

	<h2 :class="[activeRed, myBackground]">
        Hello Vue.js
    </h2>
    
    <ul>
        <li v-for="todo in todos" :class="{active: todo.isActive}" style="{fontSize:fontSize+'px'}">{{todo}}</li>
    </ul>
</div>

<script>
	const app = new Vue({
        el: '#app',
        data: {
            imageSrc: 'https://picsum.photos/200/300',
            isRed: true,
            activeRed: 'active',
            myBackground: 'my-background-color',
            todos: [
                {id:1, title: 'todo 1', isActive:true},
            ],
            fontSize: 30,
        }
    })
</script>
```



### v- model

- HTML form 요소의 값과 data를 양방향 바인딩
- 수식어
  - .lazy
    - input 대신 change이벤트 이후에 동기화
  - .number
    - 문자열을 숫자로 변경
  - .trim
    - 입력에 대한 trim을 진행

```html
<div id="app">
    <h2>
        1. Input > Data
    </h2>
    <h3>
        {{myMessage}}
    </h3>
    <input @input="onInputChange" type="text">
    <hr>
    
    <h2>
        2. Input - Data  
    </h2>
    <h3>
    	{{ myMessage2 }}    
    </h3>
    <input v-model="myMessage2" type="text">
    <hr>
    
    <h2>
        3. Checkbox
    </h2>
    <input type="checkbox" id="checkbox" v-model="checked">
    <label for="checkbox">{{ checked }}</label>
</div>

<script>
	const app = new Vew({
        el: '#app',
        data: {
            myMessage:'',
            myMessage2:'',
            checked: true,
        },
        methods: {
            onInputChange: function(event) {
                this.myMessage = event.target.value
            },
        }
        
    })
</script>
```



### Options/Data - 'computed'

- 데이터를 기반으로 하는 계산된 속성
- 함수의 형태로 정의하지만 함수가 아닌 함수의 반환 값이 바인딩 됨
- 종속된 데이터에 따라 저장(캐싱) 된다
- **종속된 데이터가 변경될 때만 함수를 실행**한다.
- 즉, 어떤 데이터에도 의존하지 않는 computed 속성의 경우 절대로 업데이트 되지 않는다.
- 반드시반환 값이 있어야 한다.

``` html
<div id="app">
    <p>
        {{num}}
    </p>
    <p>
        {{doubleNum}}
    </p>
</div>
<script>
	const app = new Vue({
        el: '#app',
        data: {
            num: 2,
        },
        computed: {
            doubleNum: function() {
                return this.num * 2
            }
        }
    })
</script>
```



### computed & methods

- computed 속성 대신 methods에 함수를 정의할 수도 있다.
  - 최종 결과에 대해 두 가지 접근 방식은 서로 동일하다.
- 차이점은 computed 속성은 종속 대상을 따라 저장(캐싱)된다.
- 즉, computed는 종속된 대상이 변경되지 않는 한 computed에 작성된 함수를 여러 번 호출해도 계산을 다시 하지 않고 계산되어 있던 결과를 반환한다.
- 이에 비해 methods를 호출하면 렌더링을 다시 할 때마다 항상 함수를 실행한다.



#### Options/Data - 'watch'

- 데이터를 감시
- 데이터에 변화가 일어났을 때 실행되는 함수

```html
<div id="app">
    <p>
        {{num}}
    </p>
    <button @click="num+=1">
        add1
    </button>
</div>
<script>
	const app = new Vue({
        el: "#app",
        data: {
            num:2,
        },
        watch: {
            num : function() {
                console.log(`${this.num}이 변경되었습니다.`)
            }
        }
    })
</script>
```



### computed & watch

#### computed

- 특정 데이터를 직접적으로 사용/가공하여 다른 값으로 만들 때 사용
- 속성은 계산해야 하는 목표 데이터를 정의하는 방식으로 소프트웨어 공학에서 이야깋는 선언형 프로그래밍 방식
- 특정 값이 변동하면 해당 값을 다시 계산해서 보여준다.

#### watch

- 특정 데이터의 변화상황에 맞춰 다른 data등이 바뀌어야 할 때 주로 사용
- 감시할 데이터를 지정하고 그 데이터가 바뀌면 특정 함수를 실행하는 방식
- 소프트웨어 공학에서 이야기하는 명령형 프로그래밍 방식
- 특정 값이 변동하면 다른 작업을 한다.
- 특정 대상이 변경되었을 때 콜백함수를 실행시키기 위한 트리거



- computed와 watch는 어떤 것이 더 우수한 것이 아닌 사용하는 목적과 상황이 다름



### 선언형 & 명령형

- 선언형 프로그래밍
  - 계산해야 하는 목표 데이터를 정의(computed)
- 명령형 프로그래밍
  - 데이터가 바뀌면 특정 함수를 실행(watch)



### Options/Assets - 'filter'

- 텍스트 형식화를 적용할 수 있는 필터
- interpolation 혹은 v-bind를 이용할 때 사용 가능
- 필터는 자바스크립트 표현식 마지막에 "|" (파이프)와 함께 추가되어야 한다.
- 이어서 사용(chaining)가능

``` html
<div id="app">
    <p>
        {{numbers|getOddNums|getUnderTenNums}}
    </p>
</div>
<script>
	const app = new Vue({
        el: '#app',
        data: {
            numbers: [1,2,3,4,5,6,7,8,9,10,11,12,13,14,15]
        },
        filters: {
            getOddNums: function(nums){
                const oddNums = nums.filter(function (num) {
                    return num%2
                })
            },
            getUnderTenNums: function(nums) {
                const underTen = nums.filter(function (num) {
                    return num < 10
                })
                return underTen
            }
        }
    })
</script>
```





## 💁‍♀️ Lifecycle Hooks

### Lifecycle Hooks

- 각 Vue 인스턴스는 생성될 때 일련의 초기화 단계를 거친다.

  - 예를 들어 데이터 관찰 설정이 필요한 경우,
  - 인스턴스를 DOM에 마운트하는 경우,
  - 데이터가 변경되어 DOM를 업데이트하는 경우 등
- 그 과정에서 사용자 정의 로직을 실행할 수 있는 Lifecycle Hooks도 호출된다.
- 공식 문서를 통해 각 라이프 사이클 훅의 상세 동작을 참고




#### created

- created hook은 vue 인스턴스가 생성된 후에 호출된다.

  ```javascript
  new Vue({
      data: {
          a:1
      },
      created: function() {
          console.log('a is: ' + this. a) // => 'a is : 1 '
      }
  })
  ```

- created를 사용해 애플리케이션의 초기 데이터를 API 요청을 통해 불러올 수 있다.

  ```javascript
  const API_URL ="이미지 주소"
  const app = new Vue({
      el: '#app',
      data: {
          imgSrc: '',
      },
      methods: {
          getImg: function() {
              axios.get(API_URL)
              	.then(response => {
                  this.imgsrc= response.data.message
              })
          }
      },
      created: function() {
          this.getImg()
      }
  })
  ```

  
