# ๐ถ React

### props๋ฅผ ํตํด ์ปดํฌ๋ํธ์๊ฒ ๊ฐ ์ ๋ฌํ๊ธฐ

#### defaultProps๋ก ๊ธฐ๋ณธ๊ฐ ์ค์ ํ๊ธฐ

- ์ปดํฌ๋ํธ์ props๋ฅผ ์ง์ ํ์ง ์์์ ๋ ๊ธฐ๋ณธ์ ์ผ๋ก ์ฌ์ฉํ  ๊ฐ์ ์ค์ ํ๊ณ  ์ถ๋ค๋ฉด ์ปดํฌ๋ํธ์ defaultPropas๋ผ๋ ๊ฐ์ ์ค์ ํ๋ค.

- ```javascript
  import React from 'react';
  
  function Hello({color, name}) {
      return <div style={{color}}>์๋ํ์ธ์ {name} </div>
  }
  Hello.defaultProps = {
      name : '์ด๋ฆ์์'
  }
  
  export default Hello;
  ```



#### props.childeren

- ์ปดํฌ๋ํธ ํ๊ทธ ์ฌ์ด์ ๋ฃ์ ๊ฐ์ ์กฐํํ๊ณ  ์ถ์ ๋, props.childeren์ ์กฐํํ๋ฉด ๋๋ค.

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