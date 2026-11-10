### 리액트 컴포넌트란?

리액트에서는 웹 페이지 전체를 하나의 코드로 작성하지 않고, 화면을 여러 개의 작은 단위로 나누어 개발합니다. 이때 화면을 구성하는 각각의 독립적인 단위를 **컴포넌트**라고 합니다.

컴포넌트는 **화면을 구성하는 UI의 조각**이라고 할 수 있습니다.

예를 들어 하나의 웹 페이지가 다음과 같이 구성되어 있다고 생각해 보겠습니다.

```javascript
App
├── Header
├── Main
│   ├── Banner
│   └── ProductList
│       ├── Product
│       ├── Product
│       └── Product
└── Footer
```

전체 페이지를 하나의 코드로 작성하는 것이 아니라 Header, Main, Product, Footer와 같이 역할에 따라 나누어 작성할 수 있습니다.

이렇게 나누면 각각의 컴포넌트를 독립적으로 관리하고 필요한 곳에서 재사용할 수 있습니다.

<br />

### 컴포넌트는 함수로 만들 수 있다

리액트에서는 가장 일반적으로 **함수를 이용하여 컴포넌트를 생성**합니다. <br />
이때 일반적으로 html 태그와 구분하기 위해 **대문자로 시작하는 이름**을 사용합니다.

```javascript
function Header() {
  return <header>Header</header>;
}
```

위 코드에서 Header 함수가 하나의 컴포넌트입니다. <br />
그리고 다른 컴포넌트에서 다음과 같이 사용할 수 있습니다.

```javascript
function App() {
  return (
    <div>
      <Header />
    </div>
  );
}
```

여기서 &lt;Header/&gt;는 HTML 태그가 아니라 직접 만든 Header 컴포넌트를 사용하는 것입니다.

즉, 컴포넌트는 일반적인 HTML 태그처럼 JSX에서 사용할 수 있습니다.

<br />

### 컴포넌트는 jsx를 반환한다

일반적인 자바스크립트 함수는 특정 값을 반환합니다.

```javascript
function add(a, b) {
  return a + b;
}

console.log(add(10, 20)); // 30
```

반면 리액트 컴포넌트는 일반적으로 **JSX를 반환**합니다.

```javascript
function App() {
  return <h1>Hello React!</h1>;
}
```

JSX는 자바스크립트 코드 안에서 HTML과 유사한 문법을 사용할 수 있도록 해주는 문법입니다

<br />

### 컴포넌트를 사용하는 이유

컴포넌트를 사용하는 가장 큰 이유는 **코드를 재사용하고 관리하기 쉽게 만들기 위해서**입니다.

예를 들어 쇼핑몰에서 상품을 보여주는 UI가 있다고 생각해 보겠습니다.

```javascript
function Product() {
  return (
    <div>
      <h2>상품 이름</h2>
      <p>30,000원</p>
    </div>
  );
}
```

이렇게 Product 컴포넌트를 만들어 놓으면 필요한 곳에서 반복해서 사용할 수 있습니다.

```javascript
function App() {
  return (
    <div>
      <Product />
      <Product />
      <Product />
    </div>
  );
}
```

만약 상품의 UI를 수정해야 한다면 Product 컴포넌트만 수정하면 됩니다. <br />
따라서 컴포넌트를 적절하게 나누면 코드의 **재사용성**과 **유지보수성**을 높일 수 있습니다
