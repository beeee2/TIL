# 💁‍♀️ CSS Layout



## 🧚‍♀️ CSS Layout

#### CSS Layout techniques

- Display
- Position
- Float(CSS1, 1996)
- **Flexbox(2012)**
- Grid(2017)
- 기타
  - Responsive Web Design(2010), Media Queries(2012)



### 💫 float

- 박스를 왼쪽 혹은 오른쪽으로 이동시켜 텍스트를 포함 인라인 요소들이 주변을 wrapping 하도록 한다.
- 요소가 Normal flow를 벗어나도록 한다.

#### Float 속성

- none : 기본값
- left : 요소를 왼쪽으로 띄움
- right : 요소를 오른쪽으로 띄움

> 🧐 박스에 float을 주었을 때 p 태그는 박스에 겹치지 않고 표현되었는데, div 태그들을 나열했을 때 왜 파란색 박스는 빨간색 박스 뒤로 뒤로가는 걸까?
>
> :  (답변 대기중)

#### Clearing Float

- Float는 Normal Flow에서 벗어나 부동 상태(떠 있음)

- 따라서, 이후 요소에 대하여 Float 속성이 적용되지 않도록 Clearing 이 필수적임

  - ::after : 선택한 요소의 맨 마지막 자식으로 가상 요소를 하나 생성

    - 보통 content 속성과 함께 짝징, 요소에 장식용 콘텐츠를 추가할 때 사용

  - clear 속성은 float이 적용된 요소의 **부모요소에게 부여**

    ```
    .clearfix::after {
    	content: '';
    	display: block;
    	clear : both;
    }
    ```

#### Float 정리

- Float는 레이아웃을 구성하기 위해 필수적으로 활용 되었으며, 최근엔 Flexbox, Grid 등장과 함께 사용도가 낮아졌다.
- Float 활용 전략 - Normal Flow 에서 벗어난 레이아웃 구성
  - 워너하는 요소들을 Float 지정하여 배치
  - 부모 요소에 Clearing Float를 하여 이후 요소부터 Normal Flow를 가지도록 지정한다. 



### 💫 flexbox

#### CSS Flexible Box Layout

- 행과 열 형태로 아이템들을 배치하는 1차원 레이아웃 모델
- 축
  - main axis(메인 축)
  - cross axis(교차 축)
- 구성 요소
  - Flex Container(부모 요소)
  - Flex Item (자식 요소)

#### Flexbox 구성요소

- Flex Container(부모 요소)
  - flexbox 레이아웃을 형성하는 가장 기본적인 모델
  - Flex Item들이 놓여있는 영역
  - display 속성을 flex 혹은 inline-flex로 지정
- Flex Item(자식 요소)
  - 컨테이너에 속해있은 컨텐츠(박스)
- Flex를 사용하는 이유
  - (수동값 부여 없이)
  - 수직 정렬이 가능하다.
  - 아이템의 너비와 높이 혹은 간격을 동일하게 배치할 수 있다.

#### Flex 속성 : flex-direction

- Main axis 기준 방향 설정
- 역방향의 경우 HTML 태그 선언 순서와 시각적으로 다르니 유의(웹 접근성에 영향)
  - row, row-reberse, column, column-reverse

#### Flex 속성 : flex-wrap

- 아이템이 컨테이너를 벗어나는 경우 해당 영역 내에 배치되도록 설정
- 즉, 기본적으로 컨테이너 영역을 벗아니지 않도록 한다.
  - wrap
  - nowrap

#### Flex 속성 : flex-direction & flex-wrap

- flex-direction : Main axis의 방향을 설정
- flex-wrap: 요소들이 강제로 한 줄에 배치되게 할 것인지 여부 설정
  - nowrap(기본 값) : 한줄에 배치
  - wrap : 넘치면 그 다음 줄로 배치
- flex-flow
  - flex-direction과 flex-wrap의 shorthand
  - flex-direction과 flex-wrap에 대한 설정 값을 차례로 작성
  - ex) flex-flex: row nowrap;

#### Flex 속성 : justify-content

- Main axis를 기준으로 공간 배분
- flex-start, flex-end, center, space-between, space-around, space-evenly

#### Flex 속성 : align-content

- Cross axis를 기준으로 공간 배분 (아이템이 한 줄로 배치되는 경우 확인할 수 없음)
- flex-start, flex-end, center, space-between, space-around, space-evenly

#### Flex 속성 : justify-content & align-content

- 공간 배분
  - flex-start(기본 값) : 아이템들을 axis 시작점으로
  - flex-end : 아이템들을 axis 끝 쪽으로
  - center : 아이템들을 axis 중앙으로
  - space-between : 아이템 사이의 간격을 균일하게 분배
  - sapce-around : 아이템을 둘러싼 영역을 균일하게 분배
  - space-evenly: 전체 영역에서 아이템 간 간격을 균일하게 분배

#### Flex 속성 : align-items

- 모든 아이템을 Cross axis를 기준으로 정렬
- stretch, flex-start, flex-end, center, baseline

#### Flex 속성 : align-self

- 개별 아이템을 Cross axis 기준으로 정렬
- 주의! 해당속성은 컨테이너에 적용하는 것이 아니라 개별아이템에 적용한다.
- stretch, flex-start, flex-end, centers

#### Flex에 적용하는 속성

- 기타 속성
  - flex-grow : 남은 영역을 아이템에 분배
  - order : 배치순서
    - 작은 수일수록 앞으로 가고,
    - 큰 수일수록 뒤로간다.



## 🧚‍♀️ bootstrap

- Quickly design and customize responsibe mobile - first sites with Bootstarp, the world's most popular front-end open source toolkit, featuring Sass variables and mixins, responsive grid system, extensive prebuilt components, and powerful JavaScript plugins
- Bootstrap으로 만든 사이트 : 넷플리스, 싸피

- 5버전 사용할 예정



#### CDN

- Content Delivery(Distribution) Network
  - 컨텐츠(CSS, JS, Image, Text 등) 효율적으로 전달하기 위해 여러 노드에 가진 네트워크에 데이터를 제공하는 시스템이다.
  - 개별 end-user의 가까운 서버를 통해 빠르게 전달 가능(지리적이점)
  - 외부 서버를 활용함으로써 본인 서버의 부하가 적어진다.

- CSS, JS를 CDN으로 불러와 사용하도록 한다.

  - CSS는 head 부분에 붙여넣는다.

  - JS는 body 태그 닫기전에 붙여넣도록 한다.

    



#### spacing

- m : margin
- p :padding
- t : top
- b : bottom
- s :left
- e :right
- x : left,right
- y : top,bottom
- 0 : 0rem, 0px
- 1 : 0.25rem, 4px
- 2 : 0.5rem, 8px
- 3 : 1 rem, 16px
- 4 : 1.5rem, 24px
- 5 : 3rem, 48px

#### color

- 후치 수식이다.

  ````
  <p class="text-primary">텍스트 색깔이 보기좋은 파랑색이다.</p>
  ````

#### 부트스트랩 홈페이지에서 다양한 클래스들을 살펴볼 수 있다.



### 💫 bootstrap grid system

#### Bootstrap grid System

- Bootstrap Grid System은 flexbox로 제작된다.

- container, rows, column으로 컨텐츠를 배치하고 정렬

  - 컨테이너 안에,

  - **항상 row를 먼저 만들어주자.** 

    ```html
    <div class="row">
        <div class="box col-1">1</div>
        <div class="box col-1">2</div>
        <div class="box col-1">3</div>
    </div>
    ```

  - col-(breakpoint)-(숫자)



- 반드시 기억해야 할 두 가지!
  - 12개의 column
    - 왜 12개일까? 약수가 많아 여러가지 경우로 나누어 다룰 수 있다.
    - 12개가 넘어가면 줄이 넘어간다.
  - 6개의 grid breakpoints
  - 





## 🧚‍♀️ Responsive web

