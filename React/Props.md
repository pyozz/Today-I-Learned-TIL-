> Props : Properties의 줄임말로, 부모 컴포넌트가 자식 컴포넌트에게 데이터를 전달할 때 사용하는 객체

React에서는 UI를 여러 개의 컴포넌트로 나누어 개발합니다.

예를 들어 다음과 같은 버튼 컴포넌트가 있다고 해보겠습니다.

```javascript
function Button() {
  return <button>로그인</button>;
}
```

이 컴포넌트를 여러 곳에서 사용하면 모두 로그인이라는 동일한 버튼이 만들어집니다.

```javascript
<Button />
<Button />
<Button />
```

그런데 각각 다른 버튼을 만들고 싶다면 **props를 활용해 데이터를 전달**하여 다른 버튼을 만들 수 있습니다.

부모 컴포넌트에서 자식 컴포넌트를 사용할 때 원하는 값을 전달할 수 있습니다.

```javascript
function App() {
  return (
    <div>
      <Button text="로그인" />
      <Button text="회원가입" />
      <Button text="삭제" />
    </div>
  );
}
```

즉, Props를 사용하는 가장 큰 장점은 하나의 컴포넌트를 다양한 데이터와 함께 재사용할 수 있다는 것입니다.

<br />

### props는 객체로 전달된다

React에서 컴포넌트에 전달되는 Props는 **객체 형태**로 전달됩니다.

예들 들어,

```javascript
<Button text="로그인" color="blue" />
```

위와 같이 작성하면 개념적으로 다음과 같은 Props 객체가 전달됩니다.

```javascript
{
  text: "로그인",
  color: "blue"
}
```

그럼 컴포넌트에서는

```javascript
function Button(props) {
  console.log(props.text);
  console.log(props.color);

  return <button>{props.text}</button>;
}
```

처럼 사용할 수 있습니다.

또한 객체로 넘어오기 때문에 매개변수에서 구조 분해 할당으로도 props를 받을 수 있습니다.

<br />

### children

props와 비슷하게 부모 컴포넌트에서 자식 컴포넌트로 정보를 전달하는 방식인 children이 있습니다.

props는 데이터를 컴포넌트의 속성으로 전달했다면 children은 **컴포넌트의 여는 태그와 닫는 태그 사이에 작성한 내용을 전달하는 방식**입니다.

```javascript
<Button>로그인</Button>
```

여기서 '로그인'이 children으로 전달됩니다.

자식 컴포넌트에서는 아래처럼 사용할 수 있습니다.

```javascript
function Button({ children }) {
  return <button>{children}</button>;
}
```

중요한 점은 children은 props와 별개의 기능이 아닌 props 객체에 포함되는 특별한 props라는 것입니다.

제가 생각하는 props와 children을 사용하는 차이는 다음과 같습니다.

- JSX 마크업에 데이터 조각만 필요한 경우에는 props로
- &lt;button&gt; &lt;/button&gt;과 같이 열고 닫는 태그가 일반적일 때는 children으로

```javascript
// 열고 닫는 태그가 일반적이여서 children 방식으로 정보 전달
<Button>Components</Button>
```

```javascript
function Button({ children }) {
  return <button>{children}</button>;
}
```

<br />

### ...props 활용하기

```javascript
function Section({ title, children, ...props }) {
  return (
    <section {...props}>
      <h2>{title}</h2>

      {children}
    </section>
  );
}
```

여기서 title과 children은 Section 컴포넌트에서 직접 사용하기 위해 꺼낸 것입니다.<br />
...props는 title과 children을 제외한 **나머지 Props가 props 객체에 모입니다.**

따라서, props 객체에는 다음과 같은 값들이 들어갑니다.

```javascript
{
  id: "core-concepts",
  className: "section"
}
```

컴포넌트에서 직접 사용할 Props는 구조 분해 할당으로 꺼내고, <br />나머지 props는 Rest 문법(...props)으로 하나의 객체에 모은 뒤, Spread 문법({...props})을 사용하여 특정 JSX 요소에 한 번에 전달할 수 있습니다.

title과 children을 제외한 나머지 Props를 별도로 하나씩 작성하지 않아도 됩니다.

따라서 **컴포넌트의 유연성과 재사용성을 높일 수 있습니다.**
