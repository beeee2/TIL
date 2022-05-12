# Vue03 🔍

# 🕯 Vuex

### Vuex

- "Statement management pattern + Library" for vue.js
  - 상태관리 패턴 + 라이브러리
- 상태(state)를 전역 저장소로 관리할 수 있도록 지원하는 라이브러리
  - 상태가 예측 가능한 방식으로만 변경될 수 있도록 보장하는 규칙 설정
  - 애플리케이션의 모든 컴포넌트에 대한 **중앙 집중식 저장소** 역할
- Vue의 공식 devtools와 통합되어 기타 고급기능을 제공



### State

- state는 곧 data이며 해당 애플리케이션의 핵심이 되는 요소
- 중앙에서 관리하는 모든 상태 정보



### 상태관리패턴

- 컴포넌트의 공유된 상태를 추출하고 이를 전역에서 관리 하도록 함
- 컴포넌트는 커다란 view가 되며 모든 컴포넌트는 트리에 상관없이 상태에 액세스하거나 동작을 트리거 할 수 있음

- 상태 관리 및 특정 규칙 적용과 관련된 개념을 정의하고 분리함으로써 코드의 구조와 유지관리 기능 향상



### 기존 Pass props & Emit event

- 각 컴포넌트는 독립적으로 데이터를 관리한다.
- 데이터는 단방향 흐름으로 부모 > 자식간의 전달만 가능하며 반대의 경우 이벤트를 트리거
- 장점
  - 데이터의 흐름을 직관적으로 파악 가능
- 단점
  - 컴포넌트 중첩이 깊어지는 경우 동위 관계의 컴포넌트로의 데이터 전달이 불편해짐
- 공통의 상태를 공유하는 여러 컴퓨터가 있는 경우 데이터 전달 구조가 매우 복잡해짐
- 예를 들면, 지나치게 중첩된 컴포넌트를 통과하는 prop

- 단방향 데이터 흐름
  - state는 앱을 작동하는 원본 소스(data)
  - view는 state의 선언적 매핑
  - action은 view에서 사용자 입력에 대해 반응적으로 state를 바꾸는 방법



### Vuex management pattern

- 중앙 저장소(store)에 state를 모아놓고 관리
- 규모가  큰 (컴포넌트 중첩이 깊은) 프로젝트에서 매우 효율적
- 각 컴포넌트에서는 중앙 집중 저장소의 state만 신경 쓰면 된다.
  - 동일한 state를 공유하는 다른 컴포넌트들도 동기화 된다.



### 단방향 흐름에 의존한 state(상태) 관리

1. 부모 자식 간의 컴포넌트 관계가 단순하거나 depth가 깊지 않은 경우에는 문제가 없음
   - 몇 단계만 거치면 데이터를 쉽게 이동시킬 수 있으며, 
   - 훨씬 직관적으로 데이터 프름을 파악할 수 있다.
2. 하지만 규모가 커졌을 경우의 상태관리가 어려워 진다.
   - 상태를 공유하는 컴포넌트의 상태 동기화 관리가 어렵다.
   - 상태를 전달할 때 상 > 하로만 가능
3. A 컴포넌트의 상태를 공유하는 다른 컴포넌트에 pass props & emit event를 통해 동기화해야 한다.



### Vuex를 활용한 state(상태) 관리

1. 상태의 변화에 따른 여러 흐름을 모두 관리해야 하는 불편함을 해소할 필요가 있다.
   - 상태는 데이터를 주고 받는 컴포넌트 사이의 관계도 충분히 고려해야 하기 때문에 상태 흐름관리가 매우 중요하다.
2. 결국 이러한 상태를 '올바르게 관리하는 저장소'의 필요성을 느끼게 괸다.
   - 상태를 한 곳에 모두 모아 놓고 관리하자
   - 상태의 변화는 모든 컴포넌트에서 공유
   - 상태의 변화는 오로지 Vuex가 관리하여 해당 상태를 공유하고 있는 모든 컴포넌트 변화에 '반응'

3. A컴포넌트와 같은 생태계를 공유하는 다른 컴포넌트는 신경쓰지 않고, 오로지 상태의 변화를 Vuex에 알린다.



## 🕯 Vuex Core Concepts

### Vuex 핵심 컨셉

1. State
2. Mutations
3. Actions
4. Getters





### State

- 중앙에서 관리하는 모든 상태 정보(data)
  - Vuex는 single state tree를 사용
  - 즉, 이 단일 객체는 모든 애플리케이션 상태를 포함하는 "**원본** 소스(single source of truth)"의 역할을 한다.
  - 이는 각 애플리케이션마다 하나의 저장소만 갖게된다는 것을 의미한다.
- 여러 컴포넌트 내부에 있는 특정 state를 중앙에서 관리하게 된다.
  - 이전의 방식은 state를 찾기 위해 각 컴포넌트를 직접 확인해야 했다.
  - Vuex를 활용하는 방식은 Vuex Store에서 각 컴포넌트에서 사용하는 state를 한 눈에 파악 가능
- State가 변화하면 해당 state를 공유하는 여러 컴포넌트의 DOM은 알아서 렌더링
- 각 컴포넌트는 이제 Vuex Store에서 state 정보를 가져와 사용한다.



### Mutations

- "실제로 state를 변경하는 유일한 방법"

- mutation의 handler(핸들러 함수)는 반드시 동기적이어야 한다.
  - 비동기적 로직(콜백함수)은 state가 변화하는 시점이 의도한 것과 달라질 수 있으며, 콜백이 실제로 호출 될 시기를 알 수 있는 방법이 없다.(추적할 수 없다.)
- 첫번째 인자로 항상 state를 받는다.
- Actions에서 commit()메서드에 의해 호출된다.



### Actions

- Mutations와 유사하지만 다음과 같은 차이점이 있다.
  1. state를 변경하는 대신 mutations를 commit() 메서드로 호출해서 실행
  2. mutations와 달리 비동기 작업이 포함될 수 있다. (Backend API와 통신하여 Data Fetching 등의 작업 수행)

- context 객체 인자를 받는다.
  - context 객체를 통해 store/index.js 파일 내에 있는 모든 요소의 속성 접근 & 메서드 호출이 가능
  - 단, (가능하지만) state를 직접 변경하지 않는다.
- 컴포넌트에서 dispatch()메서드에 의해 호출된다.

- "Actions를 통해 state를 조작할 수 있지만, state는 오로지 Mutations를 통해서만 조작해야 한다. "
  - 명확한 역할 분담을 통해 서비스 규모가 커져도 state를 올바르게 관리하기 위함.



### Getters

- state를 변경하지 않고 활용하여 계산을 수행한다.(computed 속성과 유사)
  - compute를 사용하는 것처럼 getters는 저장소의 상태(state)를 기준으로 계산
  - 예를 들어, state에 todoList라는 해야 할 일의 목록의 경우 완료된 todo 목록만을 필터링해서 출력해야 하는 경우가 있음
  - computed 속성과 마찬가지로 getters의 결과는 state 종속성에 따라 캐시(cached)되고, 종속성이 변경된 경우에만 다시 재계산된다.
  - getters자체가 state를 변경하지는 않는다.
    - state를 특정한 조건에 따라 구분(계산)만 한다.
    - 즉, 계산된 값을 가져온다.
    - getters에 정의하는 method들은 계산된 값을 저장하기에 반드시 return이 필요하다.



## 🕯 Component Binding Helper

### mapState

- computed와 Store의 state를 매핑
- Vuex Store의 하위 구조를 반환하여 component 옵션을 생성함
- 매핑된 computed 이름이 state이름과 같을 때 문자열 배열을 전달 할 수 있음

- 하지만 다른 computed 값을 함께 사용할 수 없기때문에 최종 객체를 computed에 전달할 수 있도록 다음과 같이 객체 전개 연산자로 객체를 복사하여 작성한다.

  - ```python
    computed: {
        ...mapState([
            'todos'
        ])
    }
    ```

- mapState는 객체를 반환한다.



### mapGetters

- Computed와 Getterfmf aovld
- getters를 객체 전개 연산자로 계산하여 추가
- 해당 컴포넌트 내에서 매핑하고자 하는 이름이 index.js에 정의해 놓은 getters의 이름과 동일하면 배열의 형태로 해당 이름만 문자열로 추가



### mapActions

- action을 전달하는 컴포넌트 method 옵션을 만듦
- actions를 객체 전개 연산자로 계산하여 추가하기
- 주의
  - mapActions를 사용하면, 이전에 dispatch()를 사용했을 때 payload로 넘겨줬던 this.todo를 pass prop으로 변경해서 전달해야 함

---



## 🕯 Local Storage 

### vuex-persistedstate

- Vuex state를 자동으로 브라우저의 LocalStorage에 저장해주는 라이브러리 중 하나
- 페이지가 새로고침 되어도 Vuex state를 유지시킨다.

```bash
$ npm i vuex-persistedstate
```





