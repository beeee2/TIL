# 😶 React

### props를 통해 컴포넌트에게 값 전달하기

#### defaultProps로 기본값 설정하기

- 컴포넌트에 props를 지정하지 않았을 때 기본적으로 사용할 값을 설정하고 싶다면 컴포넌트에 defaultPropas라는 값을 설정한다.

- ```javascript
  import React from 'react';
  
  function Hello({color, name}) {
      return <div style={{color}}>안녕하세요 {name} </div>
  }
  Hello.defaultProps = {
      name : '이름없음'
  }
  
  export default Hello;
  ```



#### props.childeren

- 컴포넌트 태그 사이에 넣은 값을 조회하고 싶을 땐, props.childeren을 조회하면 된다.

- ```javascript
  import React from 'react';
  
  function Wrapper({children}) {
      return (
      	<div>
          	{children}
          </div>
      )
  }
  
  export default Wrapper;
  ```

- ```javascript
  import React from ' react';
  import Hello from './Hello';
  import Wrapper from './Wrapper';
  
  function App() {
      return (
      	<Wrapper>
          	<Hello />
          	<Hello />
          </Wrapper>
      )
  }
  
  export default App;
  ```

- 