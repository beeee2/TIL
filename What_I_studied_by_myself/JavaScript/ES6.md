# ๐ฑ ES6

- ES6๋ ์๋ฐ์คํฌ๋ฆฝํธ์ ๋ง์ ๋ณํ๋ฅผ ๊ฐ์ ธ์จ ํฐ ์๋ฐ์ดํธ. 



### Let and Const

- let๊ณผ const ์ ์ ์ฐ๋ฆฌ๊ฐ ์ฌ์ฉํ๋ ๊ฒ์ var.
  - ํฐ ์ ํ๋ฆฌ์ผ์ด์ ์ ์์์ var๋ ํฐ ๋ฌธ์ ๋ฅผ ์ผ๊ธฐํ  ์ ์๋ค.
  - var๋ก ๊ฐ์ ์ด๋ฆ์ ์ฌ์ฉํ๊ฒ ๋  ์ ํด๋น ๋ณ์๊ฐ ๋ค๋ฅธ ๊ฐ๋ฐ์์ ์ํด ์๋์น์๊ฒ ๋ณํ  ์ ์๋ค.
  - variable์ด ๋ณํ๋ ๊ฑธ ๋ง๊ธฐ ์ํ ์ด๋ค ๋ฉ์ปค๋์ฆ์ด ํ์ํ๋ค. const๊ฐ ๋์จ ๋ฐํ์ด๋ค.
- const
  - ์ฌ์ฉ์ ๊ถ์ฅํ๋ค.
- let
  - ๊ฐ์ ๋ฐ๊ฟ ์ ์๋ค.
  - ๊ฐ์ ๋ณ๊ฒฝํด์ผ ํ๋ค๋ฉด let์ ์ฌ์ฉํ๋ค.



### Temporal dead zone

- Temporal dead zone์ let์ด๋ ๊ฐ์ด ์๊ฐ๋๋ ๊ฐ๋์ด๋ค.

- ์๋ฐ์คํฌ๋ฆฝํธ๋ ์์์๋ถํฐ ์๋๋ก ์ฝ๋๋ฅผ ์คํํ๋๋ฐ var ํ๋จ์ ์ ์๋ ๊ฑธ ์์์ console.log๋ฅผ ํตํด ๋์ฐ๋ ค ํ  ์ ์๋ค.(undefined ์ถ๋ ฅ)
- ์ด๋ 'hoisting'์ ๊ฐ๋๊ณผ ๊ด๋ จ์ด ์๋ค.

#### hoisting

- ์๋ฐ์คํฌ๋ฆฝํธ๊ฐ ํ๋ก๊ทธ๋จ์ ์คํํ๊ธฐ ์ ์ ๋ณ์ ๋ฑ์ ์๋จ์ผ๋ก ๋์ด์ฌ๋ ค ์ค๋ค. ์ค์ ๋ก ์ ์๋๊ธฐ ์ ์ ํธ์ถํด๋ ์๋ฌ๋ฅผ ๋์ฐ์ง ์๊ณ  undefined๋ฅผ ์ถ๋ ฅํ๋ค. 
- ์๋ฌ๋ฅผ ๋ด์ผ ํ๋ ์ํฉ์์ ์๋ฌ๋ฅผ ๋ด์ง ๋ชปํ๋ค. 
- let์ var์ ๋ค๋ฅด๊ฒ ์ ์๋์ด ์์ง ์๋ค๊ณ ํ๋ฉฐ ์๋ฌ๋ฅผ ๋ฐ์์ํจ๋ค. (์์ ํ๋ค.)



### Block scope

#### scope

- ๊ธฐ๋ณธ์ ์ผ๋ก ๋ฒ๋ธ์ด๋ฉฐ,

- ์ด ๋ฒ๋ธ์ด variabl๋ค์ด ์ ๊ทผ ๊ฐ๋ฅํ์ง ์๋์ง๋ฅผ ๊ฐ์งํด์ค๋ค. 

  ```javascript
  if (true) {
      const hello = 'hi';
  }
  console.log(hello); // ์ถ๋ ฅ๋์ง ์๋๋ค. ์๋ฌ ๋ฐ์
  ```

- const์ let ๋ชจ๋ block scope๋ก ๋์ด์๋ค. ํด๋น ๋ธ๋ก๋ด์์๋ง ์กด์ฌํ๋ค๋ ์๋ฏธ๋ค. 

- var๋ block scope๋ฅผ ๊ฐ์ง์ง ์๊ณ  function scope๋ฅผ ๊ฐ์ง๋ค. 

  - function scope ์ ๋ป์ var๊ฐ function ์์์ ์ ๊ทผํ  ์ ์๋ค๋ ์๋ฏธ๋ค

  ```javascript
  function a () {
      const hello = ' hi';
  }
  console.log(hello); // error ๋ฐ์

---



## ๐ฑ FUNCTIONS

### arrow function

- arrow function์ ์๋ฐ์คํฌ๋ฆฝํธ์์ ํจ์์ ๋ชจ์ต์ ๊ฐ์ ํ ๊ฒ์ผ๋ก ์ฝ๋๋ฅผ ๋ ์ฝ๊ฒ ๋ณผ ์ ์๋๋ก ํ๋ ๋ฐฉ๋ฒ์ด๋ค.

- ๊ธฐ์กด์ function์ ๋ง๋ค๋ ค๋ฉด function์ ์ ๊ณ  ํจ์์ ์ด๋ฆ์ ์ ์ ํ arguments๋ค์ด ์ค๊ณ  block์ ์์ฑํ๋ค.

  ```javascript
  function ํจ์์ด๋ฆ (์ธ์๋ค) {
      //๋ธ๋ก
  }
  ```

โ	ํน์ ์ต๋ชํจ์๋ก ์๋์ ๊ฐ์ด ์์ฑํ  ์ ๋ ์๋ค.

```javascript
function(์ธ์๋ค) {
    //๋ธ๋ก
}
```



- ' => ' ์ arrow๋ผ๊ณ  ํ๋ค.

```javascript
const names = ['์ฌ๊ณผ'. 'ํฌ๋', '๋ฐ๋๋']

const hearts = names.map(functions(item) {
          return '๋ด๊ฐ ์ข์ํ๋ ๊ฒ :' + item;
          })
// map์ ๊ฐ๊ฐ์ ์์ดํ๋ง๋ค ํจ์๋ฅผ ํธ์ถํ๋ค.
// ์ด ๋ map์ ๋ฌด์ธ๊ฐ return ํด์ค์ผ ํ๋ค. ๋ฌด์์ return ํ๋์ง ๊ฐ์ ์๋ก์ด array๋ก ์ถ๊ฐ๋  ๊ฒ์ด๋ค.

// ์์ ์ฝ๋๋ฅผ ๋ ๋ณด๊ธฐ์ข๊ฒ ๋ง๋ค๋ฉด ์๋์ ๊ฐ๋ค. arrow function์ ์ฌ์ฉํด๋ณด์.

const hearrs = names.map(item =>  '๋ด๊ฐ ์ข์ํ๋ ๊ฒ :' + item;)
```

- arguments๊ฐ ํ๋๋ง ์๋ ๊ฒฝ์ฐ ๊ดํธ๊ฐ ํ์์๊ณ , ๋ ๊ฐ ์ด์์ ์ธ์๊ฐ ์์ ๊ฒฝ์ฐ ๊ดํธ๊ฐ ํ์ํ๋ค.



### 'this' in Arrow Functions

- arrow function์ ์ฌ์ฉํ์ง ์์์ผ ํ  ๋ - this ํค์๋๋ฅผ ์ฌ์ฉํด์ผ ํ๋ ๊ฒฝ์ฐ

- ์ด๋ฒคํธ ๋ฆฌ์ค๋๋ฅผ ํ์์ function์ด ์์ ๋ ์๋ฐ์คํฌ๋ฆฝํธ๋ ์ฐ๋ฆฌ๊ฐ ํด๋ฆญํ ๋ฒํผ์ this ํค์๋์ ๋ฃ๋๋ค.

  ```javascript
  const button = document.querySelector("button");
  
  vutton addEventListener("click", function() {
     console.log(this) // ๋ฒํผ ํ๊ทธ๊ฐ ์ถ๋ ฅ๋๋ค.
     console.log("clicked"); 
  });
  
  vutton addEventListener("click", () =>) {
     console.log(this) // ๋ฒํผํ๊ทธ ๋์  window๊ฐ ์ถ๋ ฅ๋๋ค. this ๊ฐ ๋์ด์ button์ ๊ฐ๋ฆฌํค์ง ์๋๋ค.
     console.log("clicked"); 
  });
  ```

  - arrow function ์์ ์๋ this๋ window๋ฅผ ์ฐธ์กฐํ๋ค.
  - arrow function์ this๋ฅผ ์ด๋ฒคํธ๋ก๋ถํฐ ๊ฐ์ง๊ณ  ์์ง ์๋๋ค. arrow function์ this๋ฅผ window object๋ก ๊ฐ์ง๊ณ  ์๋ค.



### Arrow Functions in the Real World!

#### find

- Array.prototype.find๋ ์ ๊ณต๋๋ ํ์คํธ ์กฐ๊ฑด์ ๋ง์กฑํ๋ ์ฒซ๋ฒ์งธ ์๋ฆฌ๋จผํธ ๊ฐ์ ๋ฆฌํดํ๋ ํจ์.

```javascript
email = ["su@eun.com", "naver@google.com", "lynn@gmail.com", "nico@nomad.com"]
// gmail.com์ ์ฐพ์๋ณด์

const foundMail = email.find(item => item.includes("@gmail.com"));
console.log(foundMail)
```



#### filter

- filter ๋ฉ์๋๋ ์ ๊ณต๋ ํจ์์ ์กฐ๊ฑด์ ๋ง์กฑํ ๋ชจ๋  ์๋ฆฌ๋จผํธ๋ฅผ ์๋ก์ด array๋ก ๋ง๋ค์ด ๋ฐํํ๋ค.

```javascript
emails = ["su@eun.com", "naver@google.com", "lynn@gmail.com", "nico@nomad.com"]
// gmail.com์ ์ฐพ์๋ณด์

const noGmail = emails.filter(email => !email.includes("@gamil"))
console.log(noGmail)
```



#### forEach

- forEach ๋ฉ์๋๋ ๊ฐ array์ ์๋ฆฌ๋จผํธ๋ง๋ค ์ ๊ณต๋ ํจ์๋ฅผ ์คํํ๋ค.

  ```javascript
  emails = ["su@eun.com", "naver@google.com", "lynn@gmail.com", "nico@nomad.com"]
  // gmail.com์ ์ฐพ์๋ณด์
  
   emails.forEach(email => {
    console.log(email.split("@")[0])
   })
  ```

  

#### map

- map์ forEach์ง๋ง ๋ฐํ๋ element๋ค๋ก ์๋ก์ด array๋ฅผ ๋ง๋ค์ด์ค๋ค.

  ```javascript
  emails = ["su@eun.com", "naver@google.com", "lynn@gmail.com", "nico@nomad.com"];
  // gmail.com์ ์ฐพ์๋ณด์
  
   const cleaned = emails.map(email => email.split("@")[0]);
   console.log(cleaned);
  ```



#### object๋ฅผ ๋ฐํํ๋ ๋ฐฉ๋ฒ

```javascript
emails = ["su@eun.com", "naver@google.com", "lynn@gmail.com", "nico@nomad.com"];
// gmail.com์ ์ฐพ์๋ณด์

 const cleaned = emails.map((email, index) => ({
   username:email.split("@")[0], index:index
  }));
 console.log(cleaned);
```



### Default Values

ES6์์ function์ ํ ๊ฐ์ง ๋ ์ถ๊ฐ๋ ์ ์ default value ๊ธฐ๋ณธ ๊ฐ์ด๋ค. 

๊ธฐ๋ณธ๊ฐ์ arrow function ๋ฟ๋ง ์๋๋ผ ์ผ๋ฐ ํจ์์๋ ์ ์ฉํ  ์ ์๋ค.

```javascript
function sayHi(aName) {
  return "Hello " + aName;
}

console.log(sayHi("sueun"))
// ๋ง์ฝ ์ฌ์ฉ์๊ฐ ์ด๋ฆ์ ์๋ ฅ์ํ๋ฉด ์ด๋ป๊ฒ ์ถ๋ ฅ๋ ๊น ? undefined๋ก ์ถ๋ ฅ๋๋ค. 
// ๋ณด๊ธฐ ์ ์ข์ง ์๋ค. ๊ธฐ๋ณธ๊ฐ์ ์ด์ฉํ์ฌ ์ด๋ฐ ๋ถ๋ถ๋ค์ ๋ณด์ํ  ์ ์๋ค.
```

```javascript
function sayHi(aName = "anonymous") {
  return "Hello " + aName;
}

console.log(sayHi()) // "Hello anonymous" ๋ก ์ถ๋ ฅ๋๋ค.
```

- ์๋์ฒ๋ผ ์ฐ์ผ ์๋ ์๋ค.

```javascript
const sayHi = (aName = 'anonymous') => "hello " + aName;

console.log(sayHi())
```







---

## ๐ฑ STRINGS

### Strings

- ์๋ฐ์คํฌ๋ฆฝํธ์์ variable์ ๊ฐ์ง ๋ฌธ์์ด์ ์ฐ๋ ๋ฐฉ๋ฒ์ ๋ํด ์์๋ณด์.

```javascript
const sayHi = (aName = 'anonymous') => "hello " + aName;

console.log(sayHi())
```

๋ฅผ ์๋์ ๊ฐ์ด ๋ฐ๊ฟ ์ ์๋ค.

```javascript
const sayHi = (aName = 'anonymous') => `hello ${aName} lovely to have you`;

console.log(sayHi())
```

- ํํ์๋ ๋ฃ์ ์ ์๋ค.



### HTML Fragments

- string ์์ ํํ์์ ๋ฃ์ ์ ์๋ค๋ ์  ๋ง๊ณ ๋ template literal์ ๋ฉ์ง๊ฒ ์ฌ์ฉํ  ์ ์๋ ๊ฒฝ์ฐ๋ **javascript ์์์ html์ ์ธ ์ ์์ ๋**์ด๋ค.

- HTML Fragments ์์ฑ 

  ```javascript
  const wrapper = document.querySelector(".wrapper");
  
  const addWelcome = () => {
    const div = `
    	<div class="hello">
    		<h1 class="title">Hello</h1>
    	</div>
    `;  
      wrapper.innerHtml = div;
  };
  
  setTimeout(addWelcome, 2000);
  ```

  - template literal์ด ๋ด๊ฐ ๋ง๋๋ space, enter๋ ๊ณ ๋ คํด์ค๋ค.
    - single quotes์ double quotes๋ ์ค ๋ฐ๊ฟ์ ์ง์ํ์ง ์๋๋ค

  ```javascript
  // template literal์ ๋๋ค๋ฅธ ์์ 
  const wrapper = document.createElement(".wrapper");
  const friends = ["me", "lynn", "dal", "mark"];
  
  const list = `
  	<h1>
  		<ul>
  			${friends.map(friend => `<li>${friend}</li>`).join("")}
  		</ul>
  	</h1>
  `;
  
  wrapper.innerHtml = list;
  ```

  

### Cloning Styled Components

- styled components๋ ๋ฆฌ์กํธ๋ฅผ ์ํ ๋ผ์ด๋ธ๋ฌ๋ฆฌ, ํจํท ๊ฐ์ ๊ฐ๋
  - JS์์ css๋ฅผ ์ธ ์ ์๊ฒ ํด์ฃผ๋ฉฐ html์ ์ป์ ์ ์๊ฒ ํด์ค๋ค.

- ์๋ ์์ ๋ template literal์ ์ด์ฉํ์ฌ styled components๋ฅผ ํด๋ก ํ ๊ฒ



1. function
   - function์ ์ฐ๋ฆฌ๊ฐ ๋ง๋ค๊ณ  ์ถ์ element๋ฅผ ๋ฐ๊ณ  
   - ์ ์ฉํ๊ณ  ์ถ์ CSS๋ ๋ฐ์ ๋ค์์ 
   - CSS๋ฅผ ์ ์ฉํ element๋ฅผ ๋ฆฌํดํ๋ค. 

```javascript
const styled = (css) => {console.log(css)}

styled`background-color:#fff;
border-radius:10px`;


```

์๋์ ๊ฐ์ด ์ถ๋ ฅ๋๋ค.

[ 'background-color:#fff;\nborder-radius:10px' ]

- ์ด๋ ๊ฒ ํจ์๋ฅผ ํธ์ถํ๋ฉด string๋ค์ styled์ arguments๋ก ๋ค์ด๊ฐ๊ฒ ๋๋ค.

```javascript
const styled = aElement => {
  const el = document.createElement(aElement);
  return args => {
    const styles = args[0];
    el.style = styles;
    return el
  };
};

const title = styled("h1")`
  border-radius:10px;
  color:blue;
`;

console.log(title);
```

![image-20220429130741209](ES6.assets/image-20220429130741209.png)





### More String Improvements!

1. string.includes()

   - email๊ณผ ๊ด๋ จํ์ฌ ์ ์ฉํ๊ฒ ์ฌ์ฉํ  ์ ์๋ค.

2. string.repeat()

   - ์ํ๋ ์ด๋ค ๊ธ์๋  ๋ฐ๋ณตํ  ์ ์๋ค.

     ```javascript
     const CC_NUMBER = "6060";
     
     const displayName = `${"*".repeat(10)}${CC_NUMBER}`;
     
     console.log(displayName)
     ```

3. string.startsWith()

   ```javascript
   const name = "Ms. Sueun";
   console.log(name.startsWith("Ms"));
   ```

   - ์ฐธ์ด ๋ฐํ๋๋ค

4. string.endsWith()

   ```javascript
   const name = "Ms. Sueun";
   console.log(name.endsWith("Sueun"));
   
   ```

   - ์ฐธ์ด ๋ฐํ๋๋ค.
   - ์ ํจ์ฑ ๊ฒ์ฌ์ ๊ด๋ จํ์ฌ ์ ์ฉํ๊ฒ ์ฌ์ฉํ  ์ ์๋ค. (์ด๋ฉ์ผ์์ .com์ผ๋ก ๋๋๋ ์ง ํ์ธํ  ์ ์๋ค.)



---



# ๐ฑ ARRAY

## Array.from() and Array.of()

#### Array.of

- ์ด๋ค ๊ฑธ array๋ก ๋ง๋ค๊ณ  ์ถ์ ๋ ์ฌ์ฉํ๋ค.

  ```javascript
  const friends = Array.of("nico", "bee","hodoo", "fox")
      console.log(friends)
  ```

  ```html
  <button class="btn">1</button>
    <button class="btn">2</button>
    <button class="btn">3</button>
    <button class="btn">4</button>
    <button class="btn">5</button>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
    <script>
      const buttons = document.querySelectorAll("button");
      Array.from(buttons).forEach(button => {
        button.addEventListener("click", () => console.log("I ve been clicked"))
      });
    </script>
  ```

  - ์ด๋ค ์ํฉ์์๋ array๋ฅผ ์ป์ง ๋ชปํ๋ค. ์์ buttons๋ array-like object์ ํด๋นํ๋ค.
  - Array.from()์์ ๊ดํธ ์์ array-like objects๋ฅผ ๋ฐ์์ array๋ก ๋ง๋ค์ด์ค๋ค.





## Array.find(), Array.findIndex(), Array.fill()

#### array.find()

- find๋ ์กฐ๊ฑด์ด ์์ด์ผ ํ๋ค.

- ์กฐ๊ฑด์ ๋ง์กฑํ๋ ์ฒซ ๋ฒ์งธ ์์๋ฅผ ๋ฆฌํดํด์ค๋ค.

#### array.findIndex()

- findIndex๋ find์ ๊ฐ๋ค.
- element๊ฐ ์ด๋ ์๋ ์ง ์๊ณ  ์ถ์ ๋ ์ฌ์ฉํ๋ค.

```javascript

    const emails = [
      "lynn@korea.com",
      "hodo@gmail.com",
      "mom@naver.com",
      "soon@gorea.com"
    ];

    const target = emails.findIndex(email => email.includes("gorea.com"));
    console.log(target)
    console.log(emails[target])
    if (target !== -1) {
      const username = emails[target].split("@")[0];

      const email = "korea.com";

      console.log(`${username}@${email}`);

      emails[target] = `${username}@${email}`;
      console.log(emails);
    }
```



### array.fill()

- fill์ ์์์ง์ ๋ถํฐ ์ข๋ฃ์ง์ ๊น์ง static value๋ก array๋ฅผ ์ฑ์ฐ๋ ๊ฒ์ด๋ค.

  ```javascript
   const emails = [
        "lynn@korea.com",
        "hodo@gmail.com",
        "mom@naver.com",
        "soon@gorea.com"
      ];
  
      if (target !== -1) {
        emails.fill("*".repeat(5), 1, 3);
      }
        console.log(emails);
  



#### array.includes

- array์์ ์ด๋ค ๊ฑธ ๊ฐ๊ณ  ์๋์ง ์๊ณ  ์ถ์ ๋ ์ฌ์ฉํ๋ค.



---

# ๐ฑDESTRUCTURING

## Object Destructuring

#### destructuring(๋น๊ตฌ์กฐํ)

- destructuring์ object๋ array, ๊ทธ ์ธ ์์๋ค ์์ ๋ณ์๋ฅผ ๋ฐ๊นฅ์ผ๋ก ๋์ง์ด ๋ด์ ์ฌ์ฉํ  ์ ์๋๋ก ํ๋ ๊ฒ์ด๋ค.

- ํฐ ์ค๋ธ์ ํธ์์ ํน์  ๋ณ์๋ ๊ทธ ์์ ์ํ ์์ ์ค๋ธ์ ํธ์ ์ ๊ทผํ  ์ ์๋๋ก ํด์ค๋ค.

```javascript
  const settings = {
      notifications : {
        follow : true,
        alers : true,
        unfollow : false
      },
      color : {
        theme : "dark"
      }
    };

    const {
        {notifications : {follow = false} = {}},
        // settings์์ notifications ์์ผ๋ก ๊ฐ์ follow๊ฐ ์๋์ง ์ฐพ์๋ณธ๋ค.
        // follow๊ฐ ์๋ค๋ฉด follow = false๋ผ๊ณ  ์ ์ธํด์ค๋ค.
        // ์์ ๋ false๊ฐ ์ถ๋ ฅ๋๋ค.
      color
    } = settings

    console.log(follow);
```



## Array Destructuring

- ๋๊ดํธ๋ฅผ ์ฌ์ฉํ๋ค.

  ```javascript
  const days = ["MON", "TUE", "WEN", "THU", "FRI", "SAT", "SUN"]
      
  const [mon, tue, wen] = days;
  
  console.log(mon, tue, wen);
  ```

  

  

## Renaming

- API๋ฑ์ ํตํด ๋ฐ์ดํฐ๋ฅผ ๋ฐ์ ๊ฒฝ์ฐ ์์น์๋ ์ด๋ฆ์ผ๋ก ๋ฐ์ดํฐ๋ฅผ ๋ฐ๊ฒ๋  ์ ์๋ค. ์ด ๋ ์ด๋ฆ์ ๋ฐ๊ฟ์ฃผ๋ ๊ฒ์ด rename์ด๋ค.

```javascript
const settings = {
      color : {
        chosen_color : "dark"
      }
    };

const {
    color : {chosen_color : chosenColor = "light"}
} = settings

console.log(chosenColor)
```



- chosenColor๋ฅผ ์๋ฐ์ดํธํ๋ ๋ฐฉ์์ผ๋ก ์ฌ์ฉํ๊ณ  ์ถ์ ๋, ์๋์ ๊ฐ์ด ์ ์ฒด๋ฅผ ์๊ดํธ๋ก ๊ฐ์ธ์ค๋ค.
- ์ ๋ณ์๋ฅผ ์์ฑํ๋ ๋์  let๋ณ์์ธ chosenColor๋ฅผ ์๋ฐ์ดํธ ํ๋ ๊ฒ์ด๋ค.

```javascript
let chosenColor = "blue";
console.log(chosenColor);

({
    color : {chosen_color : chosenColor = "light"}
} = settings);

console.log(chosenColor);
```



## Function Destructuring

- ์ ์  ์ธํ์ ์ ์ฅํ๋ ํจ์ SaveSettings๋ฅผ ๋ง๋ค์ด๋ณด์.

- ํจ์์ ๊ธธ๊ฒ ์ธ์๋ฅผ ๋ฐ๋ ๊ฒ๋ณด๋ค settings array์ ๋ฃ์ด์ ์ ๋ฌํ์.

- ๋ณ์๋ค์ ๊ฐ๋์ฑ์ ํ๋ณดํ๊ณ  ๊ฐ ๋ณ์์ ๊ธฐ๋ณธ ๊ฐ์ ์ค์ ํ๋ ค๋ฉด ์ด๋ป๊ฒ ํด์ผํ ๊น?

  - object Destructuring์ ์ฌ์ฉํ๋ค.

  ```javascript
  function saveSettings({follow, alert, color="blue"}) {
        console.log(color);
      };
  
      saveSettings({
        follow : true,
        alert : true,
        mkt : false
      });
  ```



## Value Shorthands

- ๋ณ์๋ช๊ณผ ์์ฑ๊ฐ์ ๋๊ฐ์ด ์ฌ์ฉํ๊ณ  ์ถ๋ค๋ฉด ๋จ์ถ์์ฑ๋ช์ ์ฌ์ฉํ  ์ ์๋ค. (shorthand property)
- ๋จ์ถ์์ฑ๋ช์ ์ฌ์ฉํ๋ฉด ๋ณ์๋ช๋ง ์์ฑํ๋ฉด ๋๋ค.



## Swapping and Skipping

### Variable Swapping

- ์ผ๋จ let ๋ณ์์ฌ์ผ ํ๋ค.
- ์ฐ๋ฆฌ๋ ๋ ๋ณ์์ ์์ฑ๊ฐ์ด ์๋ก ๊ตํ๋๊ธธ ์ํ๋ค๋ฉด,
  1. ์๋ชป๋ ๋ณ์๋ค์ ์ด์ฉํด์ array๋ฅผ ๋ง๋ ๋ค.
  2. ๊ทธ๋ฐ ๋ค์ ์ฌ๋ฐ๋ฅธ ๋ณ์์ ํจ๊ป array destructuring์ ํ๋ค.

### omitting

- array์์ ํน์  ๊ฐ์ ์๋ตํ๋ ๋ฐฉ๋ฒ
- days์์ ๋ง์ง๋ง ๋ ๊ฐ์ ๊ฐ๋ง ๊ฐ์ง๊ณ  ์ค๊ณ  ์ถ๋ค๋ฉด?

```javascript
const days = ["mon", "tue", "wed", "thu", "fri", "sat", "sun"]
    const [,,, thu, fri] = days
    console.log(thu, fri)
```



---

# ๐ฑ REST AND SPREAD

## Introduction to Spread

### โ Spread

- ์ฌ์ฉ๋ฐฉ๋ฒ์ ๋ฐ๋ผ ๋ค๋ฅธ ๊ฒฐ๊ณผ๋ฅผ ๊ฐ์ ธ์ฌ ์ ์๋ค.

- spread๋ ๊ธฐ๋ณธ์ ์ผ๋ก ๋ณ์๋ฅผ ๊ฐ์ ธ์์ ํ์ด ํด์น๊ณ  ์ ๊ฐํ๋ ๊ฒ์ด๋ค.

- spread๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด์๋ ... ๋ฅผ ์ฌ์ฉํด์ผ ํ๋ค. ...๋ฅผ ์ฌ์ฉํ๋ฉด array ์์ ๋ค์ด์๋ ๋ฐ์ดํฐ๊ฐ ๋ณด์ด๋ ๊ฒ์ด์๋๋ผ array์์ ๋ค์ด์๋ ๋ณ์๋ค์ด ๋ฐ๋ก ๋ณด์ธ๋ค.

  ```javascript
  const days = [1, 2, 3, 4];
  
  console.log(...days);
  ```

- ์ฌ๋ฌ๊ฐ์ array๋ฅผ ํฉ์น๊ณ  ์ถ์ ๋ spread๋ฅผ ์ด์ฉํ๋ค.

  ```javascript
  const days = [1, 2, 3, 4];
  const alp = ["a", "b", "c"];
  
  console.log([...days, ...alp]); //(7)ย [1, 2, 3, 4, 'a', 'b', 'c']
  ```

- ๊ฐ์ฒด๋ผ๋ฆฌ ํฉ์น ๋๋ ์ฌ์ฉํ  ์ ์๋ค.



## Spread Applications

- ์ด๋ป๊ฒ ํ๋ฉด object์ ์์ฑ(property)์ ์กฐ๊ฑด๋ถ๋ก ์ถ๊ฐํ  ์ ์๋๊ฐ?

  ```javascript
  const lastName = prompt("Last name : ")
  
  const user = {
      username : "nico",
      age : 24,
      lastName : lastName !== "" ? lastName : undefined
  };
  
  console.log(user)
  ```

  ```javascript
  const lastName = prompt("Last name : ")
  
      const user = {
        username : "nico",
        age : 24,
        ...(lastName !== "" && {lastName})
      };
  
      console.log(user)
  ```



## Intro to Rest Parameters

- Parameter(๋งค๊ฐ๋ณ์)๋ผ๋๊ฑด ์ฐ๋ฆฌ๊ฐ ํจ์์๊ฒ ์ ๋ฌํ๋ ์ธ์๋ค์ ์ด์ผ๊ธฐ ํ๋ค.
- ๊ทธ๋ ๋ค๋ฉด rest parameter๋ ๋ฌด์์ผ๊น
  - ๋๋ ์๋ parameter๋ฅผ ์ ๋ฌ๋ฐ๋ ํจ์๋ฅผ ๋ง๋ค์ด์ ์ดํดํด๋ณด์.
  - parameter์ ๋ค์ด๊ฐ๋ฉด rest๋ก ์ฌ์ฉ๋๋ค๊ณ  ๋ด๋ ๋๋ค.

- spread๋ ์ ๊ฐ์๋ค๋ฉด rest๋ ์ถ์์ ๊ฐ๋ค.

```javascript
const infiniteArgs = (...kimchi) => console.log(kimchi)

infiniteArgs("1",2, true, "lalala", "dkdkdkdkkmd", 4, false)
```

- rest๋ ๋ชจ๋  ๊ฐ์ ํ๋์ ๋ณ์๋ก ์ถ์(contract) ์์ผ์ฃผ๋ ๊ฒ์ด๋ค.

```javascript
const bestFriendsMaker = (firstOne, ...rest) => {
      console.log(`my best friend is ${firstOne}`);
      console.log(`There are ${rest}`)
};

bestFriendsMaker('nico', 'lynn', 'dall', 'japan guy');
```

- rest๋ array๋ฅผ ๋ง๋ ๋ค. 





## Rest + Spread + Destructure Magic 

1. ํน์  ์์ฑ ๊ฐ ์ ์ธ์ํค๊ธฐ 

   ```javascript
   const user = {
         name : "nico",
         age : 25,
         password : 12345
       }
   
       const killPassword = ({password, ...rest}) => rest;
       const cleanuser = killPassword(user)
       console.log(cleanuser)
   ```

    - object๋ฅผ ์ง์ฐ๊ฑฐ๋ ์ ๋ฆฌํ  ๋ ์ฌ์ฉํ๋ค.

2. ๊ธฐ๋ณธ๊ฐ ์ค์ ํ๊ธฐ

   ```javascript
   const user = {
         name : "nico",
         age : 25,
         password : 12345
       }
   
       const setCountry = ({country = "KR", ...rest}) => ({country, ...rest});
       console.log(setCountry(user))
   ```

   - rest ๊ตฌ๋ฌธ์ ์ด์ฉํด์ ์๋ ฅ ์ธ์์ ๋๋จธ์ง ๊ฐ๋ค์ ํ๋๋ก ์ถ์ํ๊ณ , 
   - ๊ทธ๋ฆฌ๊ณ ๋์ country์ ํจ๊ป ๋๋จธ์ง ๊ฐ์ ๋ด๊ณ  ์๋ rest ๋ณ์๋ฅผ ์ ๊ฐํ์ฌ returnํด์ค๋ค.

3. ์์ฑ๋ช ๋ฐ๊พธ๊ธฐ(rename property)

   ```javascript
   const user = {
         NAME : "nico",
         age : 25,
         password : 12345
       }
   
       const rename = ({NAME:name, ...rest}) => ({name, ...rest})
       console.log(rename(user))
   ```

   - destructuring์ ์ฌ์ฉํ์ฌ ๋ณ์๋ฅผ renameํด์ฃผ์๋ค. 
   - rest๊ตฌ๋ฌธ๊ณผ spread ๊ตฌ๋ฌธ์ ๋ชจ๋ ์ฌ์ฉํ๋ค.



---

# ๐ฑ FOR OF LOOP

## For .. of

- ๋ฃจํ๋ ๊ธฐ๋ณธ์ ์ผ๋ก ๊ฐ์ ์ผ์ ๋ฐ๋ณต์ ์ผ๋ก ํ๋ ๊ฒ์ด๋ค. 

  ```javascript
  const friends = ["nico", "bee", "hodoo", "soon"];
      
      for (const friend of friends) {
        console.log(friend);
      }
  ```

- For ..of ๋์  forEach๋ฅผ ์ฌ์ฉํ  ์ ์๋ค. forEach๋ ๋ฐฐ์ด์ ์๋ ๊ฐ๊ฐ์ ์๋ฆฌ๋จผํธ์ ๋ํด ํน์ ํ ์ก์์ ์คํํด์ค๋ค.

  ```javascript
  const friends = ["nico", "bee", "hodoo", "soon"];
  
  friends.forEach((friend,idx, arr) => console.log(friend, idx, arr));
  ```



- for of์ ์์ฉ

  1. for of๋ array์์๋ง ๋์ํ๋ ๊ฒ์ด์๋๋ผ, iterableํ ๋ชจ๋  ๊ฒ์์ ๋์ํ๋ค.

     - iterableํ๋ค๋ ๊ฒ์ ๋ฃจํ๊ฐ ๊ฐ๋ฅํ๋ค๋ ์๋ฏธ๋ค.

       - String์์๋ ๊ฐ๋ฅํ๋ค. NodeLists์์๋ ๊ฐ๋ฅํ๋ค.

         ```javascript
         for (const friend of "longwordsgogogogo") {
               console.log(friend);
             }
         ```

     - ๋ฐ๋ฉด forEach๋ array์์๋ง ๊ฐ๋ฅํ๋ค.

  2. ๋ฃจํ๋ฅผ ๋ฉ์ถ ์๋ ์๋ค.

     ```javascript
     const friends = ["nico", "bee", "hodoo", "soon","pipie","gogo","flie","mark","lala","rorl","koko","jinju","hodod","wiwi"];
         
         for (const friend of friends) {
           if (friend === 'mark') {
             break;
           }
           else {
             console.log(friend);
           }
         }
     ```

     

---

# ๐ฑ PROMISES

## Introduction to Async

#### ์๋ฐ์คํฌ๋ฆฝํธ์ ๋น๋๊ธฐ์ฑ๊ณผ ๋๊ธฐ์ฑ

- ์ปดํจํฐ๋ ๋ ๊ฐ์ง ์ผ์ ๋์์ ํ  ์ ์๋ค. ์๋ฐ์คํฌ๋ฆฝํธ ๋ํ ์ด์ ๊ฐ๋ค. ๋์์ ๋ง์ ์ผ๋ค์ ํ  ์ ์๋ค.
- ์์ฐจ์ ์ผ๋ก ์ฒ๋ฆฌ๋๋ ๊ฒ ์๋๋ผ ํ๊บผ๋ฒ์ ์คํ๋๋ค๋ ์ ! 



## Creating Promises

#### Promise

๋น๋๊ธฐ ์์์ด ๋ง์ดํ  ๋ฏธ๋์ ์๋ฃ ๋๋ ์คํจ์ ๊ทธ ๊ฒฐ๊ณผ ๊ฐ์ ๋ํ๋ธ๋ค. 

๊ทธ๋์ Promise๋ฅผ ๋ง๋ค ๋๋ ์คํํ  ์ ์๋ function์ ๋ฃ์ด์ผ ํ๋ค.

**Promise์ ํต์ฌ**์ **๋ด๊ฐ ์์ง ๋ชจ๋ฅด๋ value์ ํจ๊ป ์์ํ  ์ ์๊ฒ ํด์ค๋ค**๋ ๊ฒ์ด๋ค.



## Using Promises

Promise๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด **Then**์ ์ฌ์ฉํด๋ณด์.

- ์๋ฐ์คํฌ๋ฆฝํธ์ promise๊ฐ ๋๋์ดํ์ ๋ช๋ น์ด๋ฅผ ์ ๋ฌํ๋ ค๋ฉด, 
- ์ฌ๊ธฐ์ ์ธ์  ๋๋๋ ๊ฑด ์ค์ํ์ง ์๋ค. ์ด์จ๋  ๋๋๊ณ  ๋ ์ดํ์ ๊ฐ์ ๋๋ ค๋ฌ๋ผ๊ณ  ๋ช๋ น์ด๋ฅผ ๋ด๋ฆฐ๋ค.

```javascript
const amIsexy = new Promise((resolve, reject) => {
      setTimeout(resolve, 3000, "Yes You are");
    });

amIsexy.then(value => console.log(value))
```

- Promise์ ๊ฐ์ return ํด์ฃผ๊ธฐ ์ํด then์ ์ฌ์ฉํ  ์ ์๋ค.



- ๋ง์ฝ Promise์ ์๋ฌ๊ฐ ์๋ค๋ฉด ์ด๋ป๊ฒ ๋ ๊น? ๊ทธ๋๊ฐ ๋ฐ๋ก reject๋ฅผ ์ฌ์ฉํ  ์ํฉ์ด๋ค.

- ์๋ฌ๋ฅผ ์ฐพ๊ธฐ ์ํด catch๋ฅผ ์ฌ์ฉํ๋ค. catch๋ then์ด๋ ๋น์ทํ์ง๋ง ์๋ฌ๋ฅผ ์ํด ์ฐ์ธ๋ค.

  ```javascript
  const amIsexy = new Promise((resolve, reject) => {
        setTimeout(reject, 3000, "You are Ugly");
  });
  
  amIsexy.then(value => console.log(value)).catch(value => console.log(value))
  ```

- then์ด ์คํ๋๋ฉด catch๋ ์ ๋ ์คํ๋์ง ์๋๋ค. ๋ฐ๋๋ก catch๊ฐ ์คํ๋๋ฉด then์ ์ ๋ ์คํ๋์ง ์๋๋ค.

- resolve ํน์ reject๋ฅผ ํตํด ๊ฐ์ ์ป์ด์์ ์ฌ์ฉํ๋ค.



---

## Chaining Promises

- ๊ฐ๋ ํ๋์  promise๊ฐ ์๋ ์ฌ๋ฌ ๊ฐ์ promise๋ฅผ ์ฌ์ฉํด์ผ ํ๋ ๊ฒฝ์ฐ๊ฐ ์๋ค. (๊ฒฐ๊ณผ๊ฐ์ด ์ฌ๋ฌ๊ฐ๊ฐ ๋์์ผ ํ๋ ๊ฒฝ์ฐ)

  - ์ด ๋ ์ฐ๊ฒฐ๋ ๋ชจ๋  then์ ์๋ก์ ์์๊ฐ ๋๋๊ธฐ๋ง์ ๊ธฐ๋ค๋ฆฐ๋ค. 
  - ์ด ๊ณผ์ ์ chaining์ด๋ผ๊ณ  ํ๋ค. (์๋ก ์ฐ๊ฒฐ๋ ๋ชจ์ต)
  - promise๋ค์ ์ฎ๊ณ  ์ถ์ ๋๋ ๊ธฐ์กด์ then์์ **return๊ฐ์ด ์์ด์ผ ํ๋ค.**

  ```javascript
  const amIsexy = new Promise((resolve, reject) => {
        resolve(2);
      });
  
      amIsexy
        .then(number => {
          console.log(number*2);
          return number*2;
        })
        .then(otherNumber => {
          console.log(otherNumber*2);
        });
  ```

- ์ฌ๋ฌ๊ฐ์ then ์ค์ ํ๋๊ฐ error ๊ฐ ์๊ฒผ์๋๋  catchํ  ์ ์๋ค. catch๊ฐ ๋ค๋ฅธ ๋ชจ๋  error๋ค์ ์ก์์ค ๊ฒ์ด๋ค. (์๋์ฐธ๊ณ )

```javascript
const amIsexy = new Promise((resolve, reject) => {
      resolve(2);
    });

    const timesTwo = number => number*2;

    amIsexy
      .then(timesTwo)
      .then(timesTwo)
      .then(timesTwo)
      .then(timesTwo)
      .then(timesTwo)
      .then(() => {
        throw Error("Something is wrong")
      })
      .then(lastNumber => console.log(lastNumber))
      .catch(error => console.log(error));
```

```javascript
const amIsexy = new Promise((resolve, reject) => {
      reject(2);
    });

    const timesTwo = number => number*2;

    amIsexy
      .then(timesTwo)
      .then(timesTwo)
      .then(timesTwo)
      .then(timesTwo)
      .then(timesTwo)
      .then(() => {
        throw Error("Something is wrong")
      })
      .then(lastNumber => console.log(lastNumber))
      .catch(error => console.log("catch๋ก error๋์ฐ๊ธฐ"));
```



## Promise.all

- Promise.all์ ์ฃผ์ด์ง ๋ชจ๋  Promise๋ฅผ ์คํํ ํ ์งํ๋๋ ํ๋์ Promise๋ฅผ ๋ฐํํ๋ค. 

- ๋ชจ๋  Promise๊ฐ ์ ๋ถ reslove๋๊ณ  ๋๋ฉด ๋ง์ง๋ง Promise๋ฅผ ๋ฆฌํด๊ฐ์ผ๋ก ์ค๋ค.

- ๋ชจ๋  ๊ฐ์ ์ป์ ๋๊น์ง Promise.all์ด ๊ธฐ๋ค๋ ธ๋ค๊ฐ ์ ๊ณต์ ํ๋ค. 

  - ํ๋์ API๊ฐ ์๋ 3๊ฐ, 4๊ฐ์ API์์ ๊ฐ์ ๋ถ๋ฌ์์ผ ํ  ๋๊ฐ ์๋ค.

    ```javascript
    const p1 = new Promise(resolve => {
          setTimeout(resolve, 5000, "First");
        });
        const p2 = new Promise(resolve => {
          setTimeout(resolve, 1000, "Second");
        });
        const p3 = new Promise(resolve => {
          setTimeout(resolve, 3000, "Third");
        });
    
        const motherPromise = Promise.all([p1, p2, p3]);
    
        motherPromise.then(values => console.log(values));
    // (3)ย ['First', 'Second', 'Third']
    ```

- ๋ง์ฝ ํ๋์ promise๋ผ๋ reject ๋๋ฉด ๋ค๋ฅธ ๋ชจ๋  promise๋ค๋ ๊ฐ์ด reject ๋๋ค.

  ```javascript
  const p1 = new Promise(resolve => {
        setTimeout(resolve, 5000, "First");
      });
      const p2 = new Promise((resolve, reject) => {
        setTimeout(reject, 1000, "I hate JS");
      });
      const p3 = new Promise(resolve => {
        setTimeout(resolve, 3000, "Third");
      });
  
      const motherPromise = Promise.all([p1, p2, p3]);
  
      motherPromise
        .then(values => console.log(values))
        .catch(err => console.log(err));
  ```

  

## Promise.race

- Promise.race๋ Promise ALl์ด๋ ์ฌ์ฉ๋ฒ์ ๋์ผํ๋ค.

- Promise Race์ ๋ค๋ฅธ ์ ์ ์ฃผ์ด์ง Promise๋ค ์ค ํ๋๋ผ๋ resolve ๋๊ฑฐ๋ reject๋๋ฉด ๋๋ค๋ ๊ฒ์ด๋ค. Promise๋ค ๊ฐ์ฅ ๋น ๋ฅธ๊ฒ ๊ฒฐ๊ณผ๋ฅผ ๊ฒฐ์ ํ๋ค.

  ```javascript
  const p1 = new Promise(resolve => {
      setTimeout(resolve, 10000, "First");
  });
  const p2 = new Promise((resolve, reject) => {
      setTimeout(reject, 5000, "I hate JS");
  });
  const p3 = new Promise(resolve => {
      setTimeout(resolve, 3000, "Third");
  });
  
  const motherPromise = Promise.race([p1, p2, p3]);
  
  motherPromise
      .then(values => console.log(values))
      .catch(err => console.log(err));
  ```

  - ์ด๋ ๊ฒ์ด ๋จผ์  ๋๋์ง ์๊ด์์ ๋ race๋ฅผ ์ฌ์ฉํ๋ฉด ๋๋ค.



## finally

- Promise๊ฐ ์ฑ๊ณตํ๊ฑฐ๋ ์คํจํ ํ ๋ง์ง๋ง์ผ๋ก ์ด๋ค ํ๋์ ํ๊ธฐ๋ฅผ ์ํ  ์ ์๋ค. ๊ทธ๋ด ๋ ์ฌ์ฉํ๋ ๊ฒ์ด finally๋ค. 

```javascript
const p1 = new Promise((resolve, reject) => {
      setTimeout(resolve, 10000, "First");
    })
      .then((value) => console.log(value))
      .catch((error) => console.log(error))
      .finally(() => console.log("I'm Done"));
```



## Real word Promises

#### fetch

- fetch๋ Promises๋ฅผ returnํ๋ค.

- fetch๊ฐ ํ๋ ์ผ์ ๋ญ๊ฐ๋ฅผ ๊ฐ์ง๊ณ  ์ค๋ ๊ฒ์ด๋ค.

  ```javascript
  
  fetch("http://127.0.0.1:5500/app.html")
      .then(response => response.text())
      .then(text => console.log(text))
  ```

  



---

# ๐ฑ ASYNC / AWAIT

## Async Await

- async/await๋ ๋ Promise์ ์๋ฐ์ดํธ๋ค.
- ๊ณ์ํด์ ๋ฐ๋ณตํด์ ์์ฑ๋๋ then ์ฝ๋๋ ๋ณด๊ธฐ ๋ณ๋ก ์ข์ง ์๋ค.
- ๊ธฐ๋ณธ์ ์ผ๋ก async/await์ Promise๋ฅผ ์ฌ์ฉํ๋ ์ฝ๋๋ฅผ ๋ ์ข๊ฒ ๋ณด์ด๊ฒํ๋ ๋ฌธ๋ฒ์ด๋ค.
- async/await์ Promise๋ฐ์์ ๊ฐ์ ๊ฐ์ ธ์ฌ ์ ์๋ ๋ฐฉ๋ฒ์ด๋ค.



- ๋จผ์ , await์ ํผ์์๋ ์ฌ์ฉํ  ์ ์๋ค. await์ ํญ์ async function ์์์๋ง ์ฌ์ฉํ  ์ ์๋ค.
- ์ ๋ง์ then์ ์ฌ์ฉํ๋ ๊ฒ ๋์ ์ await์ ์ฌ์ฉํ๋ฉด ๋๋ค.
- **await์ ๊ธฐ๋ณธ์ ์ผ๋ก Promise๊ฐ ๋๋๊ธธ ๊ธฐ๋ค๋ฆฐ๋ค.** 

```javascript
const getMoviesAsync = async () => {
      const response = await fetch("https://yts.mx/api/v2/list_movies.json");
      const json = await response.json()
      console.log(json)
    };

getMoviesAsync();
```





## try catch finally

```javascript
const getMoviesAsync = async () => {
    try {
        const response = await fetch("https://yts.mx/api/v2/listmovies.json");
        const json = await response.json()
        console.log(json) 
    } catch(e) {
        console.log(e)
    }
};

getMoviesAsync();
```

```javascript
const getMoviesAsync = async () => {
    try {
        const response = await fetch("https://yts.mx/api/v2/listmovies.json");
        const json = await response.json()
        console.log(json) 
    } catch(e) {
        console.log(e)
    } finally {
        console.log("We are Done!")
    }
};
```

- catch block์  await ์์ ์๋ error๋ง ์ก๋๊ฒ ์๋๋ผ ๋ฐ์ ์๋ error๊น์ง ์ก๋๋ค.
- ์ด๋ค error๊ฐ try block ์ ์๋์ง ๋ฌด์กฐ๊ฑด ์ก๋๋ค. 



## Parallel Async Await

#### Parallel

```javascript
const getMoviesAsync = async () => {
    try {
        const [moviesResponse, suggestionsResponse] = await Promise.all([
            fetch("https://yts.mx/api/v2/list_movies.json"),
            fetch("https://yts.mx/api/v2/movie_suggestions.json?movie_id=100")
        ]);

        const [moviews, suggestions] = await Promise.all([
            moviesResponse.json(),
            suggestionsResponse.json()
        ]);

        console.log(moviews, suggestions)
    } catch(e) {
        console.log(3)
    }
};
getMoviesAsync();
```



# ๐ฑ CLASSES

## Introduction to Classes

- ๋ด๊ฐ ์์ฒญ ๋ง์ ์ฝ๋๋ฅผ ๊ฐ์ง๊ณ  ์๊ณ  ์ด๊ฒ์ ๊ตฌ์กฐํํ๊ธธ ์ํ  ๋ Class๋ฅผ ์ด์ฉํ๋ค๋ฉด ๋งค์ฐ ์ ์ฉํ  ์ ์๋ค.

- Class๋ ๊ธฐ๋ณธ์ ์ผ๋ก blueprint(์ฒญ์ฌ์ง)์ด๋ค.

- Class๋ ์ฌ์ฌ์ฉ์ด ๊ฐ๋ฅํ๋ค.

- Class๋ constructor(์์ฑ์)๋ฅผ ์์ ๊ฐ์ง๊ณ  ์๋ค.

- ์ฒญ์ฌ์ง Class๋ฅผ ์ด์ฉํ์ฌ ๋ณ์๋ฅผ ์ ์ธํด์ค์ผ ํ๋ค.

  ```javascript
  class User {
      constructor() {
          this.userName = "sueun";
      }
  }
  
  const sexyUser = new User();
  console.log(sexyUser.userName)
  ```

  ```javscript
  class User {
        constructor(name) {
          this.userName = name;
        }
      }
  
      const sexyUser = new User("hodoo");
      const uglyUser = new User("sueun");
      console.log(sexyUser.userName);
      console.log(uglyUser.userName);
  ```

  ``` javascript
  class User {
        constructor(name) {
          this.userName = name;
        }
        sayHello() {
          console.log(`Hello, my name is ${this.userName}`);
        }
      }
  
      const sexyUser = new User("hodoo");
      sexyUser.sayHello();
  ```



## Extending Classes

- 'this'๋ ๊ธฐ๋ณธ์ ์ผ๋ก ํด๋์ค ์์์ ๋ณผ ์ ์๊ณ  ํด๋์ค ๊ทธ ์์ฒด๋ฅผ ๊ฐ๋ฆฌํจ๋ค.
  - ํด๋์ค์ ๋ฌด์ธ๊ฐ๋ฅผ ์ถ๊ฐํ๊ณ  ์ถ๊ฑฐ๋ ์ด๋ค๊ฒ์ ๋ถ๋ฌ์ค๊ณ  ์ถ์ ๋ 'this'๋ฅผ ์ฌ์ฉํ๊ฒ ๋  ๊ฒ์ด๋ค.
- this๋ ์ํฉ์ ๋ฐ๋ผ ๊ฐ๋ฆฌํค๋ ๊ฒ์ด ๋ค๋ฅธ๋ฐ ๋ด๊ฐ ์ด๋ป๊ฒ class์ functions์ ์ ์ํ๋๋์ ๋ฐ๋ผ ๋ฌ๋ผ์ง๋ค.

``` javascript
class User {
    constructor(name, lastName, email, password) {
        this.userName = name;
        this.lastName = lastName;
        this.email = email;
        this.password = password;
    }
    sayHello() {
        console.log(`Hello, my name is ${this.userName}`);
    }
    getProfile() {
        console.log(`${this.username} ${this.email} ${this.password}`);
    }
    updatePassword(newPassword, currentPassword) {
        if (currentPassword === this.password) {
            this.password = newPassword
        } else {
            console.log( "Can't change password.");
        }
    }
}

const sexyUser = new User("hodoo", "lee", "hodo@nate.com", "1234");
sexyUser.updatePassword("abcd", "1234");
console.log(sexyUser.password);
```





#### extend

- ์๋ฅผ ๋ค์ด user ํด๋์ค๋ฅผ ๊ฐ์ง๊ณ  ์๊ณ  user ํด๋์ค์ ์ด๋ค ๋ถ๋ถ์ ์ฝ๊ฐ ๋ ์์ ํ๊ณ  ์ถ๋ค๋ฉด?

- extends ๋ฅผ ์ฌ์ฉํ์ฌ userํด๋์ค๋ฅผ ์์ํ๋ค.

  ```javascript
  class User {
      constructor(name, lastName, email, password) {
          this.userName = name;
          this.lastName = lastName;
          this.email = email;
          this.password = password;
      }
      sayHello() {
          console.log(`Hello, my name is ${this.userName}`);
      }
      getProfile() {
          console.log(`${this.username} ${this.email} ${this.password}`);
      }
      updatePassword(newPassword, currentPassword) {
          if (currentPassword === this.password) {
              this.password = newPassword
          } else {
              console.log( "Can't change password.");
          }
      }
  }
  
  const sexyUser = new User("hodoo", "lee", "hodo@nate.com", "1234");
  sexyUser.updatePassword("abcd", "1234");
  console.log(sexyUser.password);
  
  class Admin extends User {
      deleteWebsite() {
          console.log("Deleting the whole website...")
      }
  }
  
  const sexyAdmin = new Admin();
  sexyAdmin.deleteWebsite();
  ```

  

## 

- ์์์ ๋ค๋ค๋ user๋ฅผ ๋ฆฌํฉํ ๋ง ํด๋ณด์. ๋ง์ ์ธ์๊ฐ๋ค์ ๊ฐ์ฒด๋ก ๋ฌถ์ด ๋ฃ์ด์ค๋ค.

  - ๋ง์ฝ ๋ด๊ฐ ์ฌ๋ฌ arguments๋ฅผ ๊ฐ์ง๊ณ  ์๋ค๋ฉด options ์ค๋ธ์ ํธ๋ก ํ๋ ๊ฒ ๋ ์ข๋ค. ๋ด๊ฐ ์ด๋ค ๊ฐ์ ๋๊ฒจ์ฃผ๋ ์ง ๋ณผ ์ ์๊ธฐ ๋๋ฌธ์ด๋ค.

    ```javascript
    class User {
          constructor(options) {
            this.userName = options.userName;
            this.lastName = options.lastName;
            this.email = options.email;
            this.password = options.password;
          }
          sayHello() {
            console.log(`Hello, my name is ${this.userName}`);
          }
          getProfile() {
            console.log(`${this.userName} ${this.email} ${this.password}`);
          }
          updatePassword(newPassword, currentPassword) {
            if (currentPassword === this.password) {
              this.password = newPassword
            } else {
              console.log( "Can't change password.");
            }
          }
        }
    
        const sexyUser = new User({
          userName :"hodoo", 
          lastName: "lee", 
          email : "hodo@nate.com", 
          password : "1234"
        });
        sexyUser.updatePassword("abcd", "1234");
        console.log(sexyUser.password);
    ```

- admin ๋ง๋ค๊ธฐ
  - ์ฐ๋ฆฌ๊ฐ constructor์์ด admin์ ๋ง๋ ๋ค๋ฉด ์๋ฌด๋ฐ ๋ฌธ์ ๊ฐ ์์ง๋ง,
  - ์ฐ๋ฆฌ๊ฐ admin constructor์ ์ฌ์ฉํ๊ฒ ๋๋ค๋ฉด ๊ธฐ์กด์(์์์ ์ ์๋) user constructor์ ์๊ฒ ๋๋ค.
  - ์ฐ๋ฆฌ๋ ํน๋ณํ ํจ์๋ฅผ ํธ์ถํ๋ค. ์ด ํจ์๋ classes ์์์๋ง ์ ํจํ๊ณ  super๋ผ๊ณ  ๋ถ๋ฆฐ๋ค.
  - super๋ ์์ํด๋์ค๋ฅผ ํธ์ถํ๋ค.

```javascript
<body>
  <span id="count">0</span>
  <button id="add">+</button>
  <button id="minus">-</button>

  <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
  <script>
    class User {
      constructor({username, lastname, email, password}) {
        this.username = username;
        this.lastname = lastname;
        this.email = email;
        this.password = password;
      }
      getProfile() {
        console.log(`${this.username} ${this.email} ${this.password}`)
      }

      updateProfile(newpassword, currentpassword) {
        if (currentpassword == this.password) {
          this.password = newpassword;
        } else {
          console.log("can't change password");
        }
      }
    }

    const sexyUser = new User({
      username : "Nico",
      lastname : "serrano",
      email : "email@com",
      password : "1234",
    });

    class Admin extends User {
      constructor({username,lastname,email,password,superadmin,isActive}) {
        super({username,lastname,email,password});
        this.superadmin = superadmin;
        this.isActive = isActive;
      }

      deleteWebsite() {
        console.log("Boom!");
      }
    }

    const admin = new Admin({
      username : "nico",
      lastname : "serrano",
      email : "nico@com",
      password : "1234",
      superadmin : true,
      isActive: true
    })

    class Counter {
      constructor ({initialNumber=0, counterId, plusId, minusId}) {
        this.count = initialNumber;
        this.counter = document.querySelector("#count");
        this.plusBtn = document.querySelector("#add");
        this.minusBtn = document.querySelector("#minus");
        this.addEventListeners();
      }

      addEventListeners= () => {
        this.plusBtn.addEventListener("click", this.increase);
        this.minusBtn.addEventListener("click", this.decrease);
      };

      increase = () => {
        this.count = this.count + 1;
        this.repaintCount();
      }
      
      decrease = () => {
        this.count = this.count - 1; 
        this.repaintCount();
      }

      repaintCount =() =>  {
        this.counter.innerText = this.count;
      }
    } ;

    new Counter ({
      initialNumber: 0,
      counterId : "count",
      plusId : "add",
      minusId : "minus"
    })
   </script>
</body>
```



---

# ๐ฑ SYMBOL, SET AND MAP

## Symbols

- ์๋ฐ์คํฌ๋ฆฝํธ๋ Strings, Booleans, numbers๋ฅผ  Data types์ผ๋ก ๊ฐ์ง๊ณ  ์๋ค. 
- Symbols์ ์๋ก์ด Data types์ด๋ค.
- Symbols๋ ์์ฑ์์ ํ ๊ฐ์ง๋ฅผ ๊ฐ์ง๋๋ฐ ๋ฐ๋ก Description์ด๋ค.



## Sets

- ์๋ฐ์คํฌ๋ฆฝํธ๋ **object**๋ฅผ ์ฌ์ฉํ์ฌ object์ property๋ฅผ ์ญ์ ํ๊ฑฐ๋ ์ถ๊ฐํ๊ฑฐ๋ ํน์ ๊ฐ์ง๊ณ  ์ฌ ์๋ ์๋ค.
- set์ ์ฌ์ฉํ๋ฉด ์ด๋ค ํ์์ ๊ณ ์ ํ value๋  ์ ์ฅํ  ์ ์๊ฒ ํด์ค๋ค.
- set์ ๊ฐ๋ ฅํ api๊ฐ ์ฐ๋ฆฌ์ ์์์ ๋์์ค ๊ฒ์ด๋ค.
  - has, delete, add , size...



## WeakSet

- weak sets์ sets๊ณผ ๊ฐ์ง๋ง ๋ค๋ฅด๋ค. 

```javascript
const weakSet = new WeakSet();
```

- weak sets๋ ์ค๋ก์ง ojects๋ง ์ ์ฅํ  ์ ์๋ค.

- garbage collector์ ๋ญ๊ฐ ์ฌ์ฉ๋์ง ์๊ฑฐ๋ ๋ฟ์ง ์๊ฑฐ๋ ๋๋ ๋ญ๊ฐ ๋๋  ๊ฐ์ ๋ฉ๋ชจ๋ฆฌ ๋ด์ ์์๋ค์ ์ฐจ์งํ๊ณ  ์๋ค๋ฉด ์ด๊ฒ๋ค์ ์ฒญ์ํ๋ ค๊ณ  ํ  ๊ฒ์ด๋ค. 
- weak set์์ ์ ์ฅ๋ ๊ฒ๋ค์ ์ฝํ๊ฒ ๋ถ๋ค๋ ค ์๋ค. 
  - ๋ง์ฝ weak set์ ๋ฃ์ object๋ฅผ ๊ฐ๋ฆฌํค๋ ๊ฒ์ด ์๋ค๋ฉด ์ด๊ฒ์ ์ง์์ง ๊ฒ์ด๋ค.
  - garbage collector๋... ๋ฉ๋ชจ๋ฆฌ๊ฐ ๋ถ์กฑํ  ๋ ์ฐพ์์จ๋ค.



## Map and Weakmap 

```javascript
const map = new Map();
```

- map๋ ๋ค์ํ API๋ฅผ ๊ฐ์ง๊ณ  ์๋ค.
  - delete, clear, entries, forEach, set has Key
  - map์ add๊ฐ ์๋ค.

- set์ ๋๊ฐ์ arguments๋ฅผ ์ค๋ค. key์ value.

  - key์ ์ฐ๋ฆฌ๊ฐ ํ  ์ ์๋ ๊ฒ์ ๋ญ๊ฐ๋ฅผ ๋ฃ๋ ๊ฒ์ด๋ค. 

    ```jacascript
    map.set("age", 18)
    ```

    

  - ๊ฐ์ ๋ฃ๋ ๋์ ์ ์ด๋ฆ์ ๋ฃ์ ์ ์๋ค.

    ```javascript
    map.has("age"); // true
    map.get("age"); // 18
    ```

    

---

# ๐ฑ GENERATORS AND MAPS

## Generators

- generators๋ ๊ธฐ๋ณธ์ ์ผ๋ก pauseํ  ์ ์๋ ํจ์๋ค.
- generators๋ฅผ ์ฌ์ฉํ๊ธฐ ์ํด์๋ ๋ช๊ฐ์ง ๊ท์น์ ๋ฐ๋ผ์ผ ํ๋ค.
  - function ๊ทธ๋ฆฌ๊ณ  *์ ์ฌ์ฉํ๋ค.
  - function์ *๋ฅผ ๋ฃ์ผ๋ฉด ํ ๋จ์ด๋ฅผ ํด์ ํ๊ฒ ๋๋ค. ๊ทธ๋ฆฌ๊ณ  ์ด ๋จ์ด๋ yield ์ด๋ค.
  - yield๋ return๊ณผ ๊ฐ๋ค.

- ํ ๋น๋ ๋ณ์์ .next๋ฅผ ์ฌ์ฉํ์ฌ ๊ฐ์ ๋ถ๋ฌ์ฌ ์ ์๋ค.

```javascript
function* listPeople() {
    yield "Dal";
    yield "Flynn";
    yield "Mark";
    yield "Godkimchi";
    yield "Japan Guy";
}

const listG = listPeople();
```

```javascript
listG.next()
```

- ์ฒซ๋ฒ์งธ value์ธ dal๋ถํฐ ๋ฐํ๋๋ค. 
- ์ถ๋ ฅ๊ฐ์ done:false๋ generator๊ฐ ์์ง ๋๋์ง ์์์์ ์๋ฏธํ๋ค.
- ๋ง์ฝ ๋ค์ listG.next() ํธ์ถํ๋ค๋ฉด ๋ ๋ฒ์งธ value์ธ Flynn object์ ์ป์ ์ ์๋ค.



## Proxies

- proxy๋ฅผ filter์ฒ๋ผ ์๊ฐํ  ์ ์๋ค. 

- proxy๋ ๋ ๊ฐ์ input์ ์ทจํ๋๋ฐ ํ๋๋ target(์ฐ๋ฆฌ๊ฐ filter๋ฅผ ํ๊ณ  ์ถ์ object),  ๋ ๋ค๋ฅธ ํ๋๋ handler(userObj์ ํํฐ)๋ค.

  ```javascript
  const userObj = {
      username : "nico",
      age : 12,
      password : 1234
  }
  
  const userFilter = {};
  
  const filteredUser = new Proxy(userObj, userFilter);
  ```

  - fileredUser์ ํธ์ถํ๋ฉด ๊ธฐ๋ณธ์ ์ผ๋ก userObj๋ฅผ ์ป๋๋ค.

```javascript
const userObj = {
username : "nico",
age : 12,
password : 1234
}

const userFilter = {
get: () => {
console.log("Somebody is getting something");
},
set: () => {
console.log("Somebody wrote something");
}
};

const filteredUser = new Proxy(userObj, userFilter);
```

- filteredUser๋ฅผ ์์ฑํ๊ณ  proxy์๊ฒ targetObj๋ฅผ ์ฃผ๊ณ  ๊ทธ ๋ค์ userFilter๋ฅผ ์ฌ์ฉํ๋ค.

- userFilter ์์ ์ฐ๋ฆฌ๊ฐ ์ ์ํ ํจ์๋ค์ด ๊ธฐ์กด ๋ฉ์๋๋ฅผ ์์ด์ฐ๊ณ  ์ ๊ทผํ์ง ๋ชปํ๊ฒ๋ ๋ง์์ฃผ๊ณ  ์๋ค. 

- ๋์์ด ๊ฐ๋ก์ฑ์ง๋ค๋ ์๋ฏธ์์ trap์ด๋ผ๊ณ  ๋ถ๋ฅด๊ธฐ๋ ํ๋ค. 

  - get์ property value๋ฅผ ์ทจํ๋ ๊ฒ์ ๋ํ trap

    ```javascript
    const handler1 = {
        get: function(target, prop, receiver) {
            
        }
    }
    ```



---

# ๐ฑ ES 2020

## New ?? Operator 

- Nullish coalescing operator (??)
- ??๋ ||(or)์ ๊ฐ์ ๋ผ๋ฆฌ์ฐ์ฐ์์ด์ง๋ง ์ฝ๊ฐ์ ์ฐจ์ด๋ ์๋ค.
  - ||๋ ๋ณ์์ ๊ธฐ๋ณธ๊ฐ์ ์ค ๋ ์ ์ฉํ๋ค.
  - or ์ฐ์ฐ์๋ ๋ณ์์ ์๋ฌด๊ฒ๋ ์์ผ๋ฉด (False) ๋ค์์ ํ์ธํ๊ฒ ๋๋ค. ์ด๋ ๊ฒ ํด์ default ๊ฐ์ ๋ณ์์ ๋ฃ์ด์ค ์ ์๋ค.

```javscript
let name;
//undefined
console.log("hello", name)
//VM586:1 hello undefined
//undefined
console.log("hello", name ||  "anonymous")
//VM632:1 hello anonymous
```

- ๋ฌธ์ ๋ or์ฐ์ฐ์๋ boolean์ฐ์ฐ์์ฌ์ ๊ฑฐ์ง์ด๊ฑฐ๋ ์ฐธ์ธ ๊ฒ๋ง ํ๋จํ  ์ ์๋ค.

```javascript
//undefined
name= 0
//0
console.log("hello", name || "anonymous")
//VM889:1 hello anonymous
```

- name์ 0์ด๋ผ๋ ๊ฐ์ด ์์์๋ anonymous๊ฐ ์ถ๋ ฅ๋๋ค.
- nullish coalescing ์ฐ์ฐ์(??)๋ ์ด๋ฐ ๊ฒฝ์ฐ๋ฅผ ์ํด์ ๋ง๋ค์ด ์ก๋ค. 

- **??๋ ์ค์ง ๋ณ์ ๊ฐ์ด null์ด๊ฑฐ๋ undefined ์ผ๋๋ง ์๋**ํ๋ค. 

```javascript
console.log("hello", name ?? "anonymous")
//VM918:1 hello 0
```



## Optional Chaining

```javascript
console.log(lynn?.profile?.email?.provider?.name)
```

- && ๋ฅผ ์ฌ๋ฌ๋ฒ ์ฐ์ง ์์๋ ๋๋ค.
- lynn์ด ์กด์ฌํ๊ณ  lynn.profile์ด ์กด์ฌํ๊ณ  lynn.profie.email์ด ์กด์ฌํ๊ณ  ๊ทธ ๋ฐ์ provider์ ๊ทธ ๋ฐ์ name์ด ์กด์ฌํ๋ฉด name์ ์ถ๋ ฅํ๋ผ๋ ์ด์ผ๊ธฐ.

- ์ด๋ค object๊ฐ ๋ด๊ฐ ์์ํ ๊ฒ์ ๊ฐ์ง๊ณ  ์๋์ง ์๋์ง ํ์ ํ  ์ ์์ ๋ ์ฌ์ฉํ๋ฉด ์ข๋ค.



## padStart and padEnd

- padding์ ๋ฃ๋๋ค๋ ์ ์์ ๋ ๋ชจ๋ ๋น์ทํ๋ค.
- ๋ฌธ์์ด์๋งจ ์์ด๋ ๋งจ ๋ค์ padding์ ๋ฃ๋๋ค. 

```javscript
String(minutes).padStart(2, "0")
// ๋ง์ฝ minutes๊ฐ ๋ ์๋ฆฌ ์๊ฐ ์ ๋๋ค๋ฉด ๊ทธ ๋ถ๋ถ์ 0์ผ๋ก ๋งจ ์์ ์ฑ์ฐ๋ผ๋ ์ด์ผ๊ธฐ
// ์ฒซ ๋ฒ์งธ ์ธ์๋ ๋ฌธ์์ด์ ๊ธธ์ด๋ฅผ ๋ปํ๋ค. 

"5".padStart(5,"x")
//"xxxx5"
```

- padStart์ padEnd๋ ๊ฐ์ ๋ฐํํ๋ค. ์๋ณธ ๊ฐ์ ๋ณํ์ํค์ง ์๋๋ค.



## trim, trimStart, trimEnd

- trimStart๋ ๊ธฐ๋ณธ์ ์ผ๋ก ๊ทธ๋ฅ ์๋ฅด๋ ๊ธฐ๋ฅ์ด๋ค.
  - ๋ฌธ์ฅ ์์ ๋น์ด์๋ ๊ณต๊ฐ์ ๋ค ์๋ผ์ฃผ๋ ์ญํ ์ ํ๋ค.
- ์๋ถ๋ถ๊ณผ ๋ท๋ถ๋ถ ๋ชจ๋ ๊ณต๋ฐฑ์ ์ ๊ฑฐํ๊ณ  ์ถ๋ค๋ฉด trim์ ์ฌ์ฉํ๋ฉด ๋๋ค.
- trim์ string ์์ฒด๋ฅผ ๋ฐ๊พธ์ง ์๋๋ค. 
