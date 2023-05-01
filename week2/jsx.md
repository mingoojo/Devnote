# 1. JSX

### JSX전에, XML이란?

XML(Extensible Markup Language:확장가능한 마크업언어)은 컴퓨터와 사람이 읽을 수 있는 방식으로 텍스트 지정된 자료형으로, HTML과 매우 비슷한 문자 기반의 마크업 언어이다. 그러나 XML은 HTML과 달리 태그를 미리 지정하지 않고, 사용자가 직접 정의 할 수 있다.



**XML의 특징**

XML의 중요한 특징은 다음과 같다.

1. XML은 다른 목적의 마크업 언어를 만드는 데 사용되는 다목적 마크업 언어이다.
2. XML은 다른 시스템끼리 다양한 종류의 데이터를 손쉽게 교환할 수 있도록 해준다.
3. XML은 새로운 태그를 만들어 추가해도 계속해서 동작하므로, 확장성이 좋다.
4. XML은 데이터를 보여주지 않고, 데이터를 전달하고 저장하는 것만을 목적으로 한다.
5. XML은 텍스트 데이터 형식의 언어로 모든 XML 문서는 유니코드 문자로만 이루어진다.

### JSX란?

XML같은 문법의 확장 개념으로, 자바스크립트의 확장 문법이다. XML과 비슷한 형태를 띄며 JSX로 작성된 코드는 브라우저에서 실행되기 전에 바벨과 같은 컴파일러를 사용하여 일반 자바스크립트 형태의 코드로 변환된다.

JSX는 리엑트로 프로젝트를 개발할 때 사용하는 언어이므로, 자바스크립트 문법은 아니다. 또한 JSX는 하나의 파일에 자바스크립트와 HTML을 동시에 작성할 수 있어서 편리하다. 또한 HTML과 비슷한 형태를 띄고 있기에 가독성이 좋다. 그리고, React에서만 사용되는 문법이 아니라 범용성도 좋다.

#### JSX문법의 형태

#### Example1

```javascript
//jsx코드
function App(){
	return(
    	<p> hello world</p>
    )
}
```

위의 형태는 React를 작성하다보면 가장 많이 보는 형태이다. 저 형태의 구문이 JSX형태의 구문이고, 컴파일러를 통해 자바스크립트의 언어로 변환된 코드는 아래와 같다.

```javascript
//변환된 js코드
function App() {
  return React.createElement("p", null, " hello world");
}
```

아래의 링크를 통해BABEL컴파일러를 통해  JSX를 자바스크립트 언어로 변환하는 것을 해볼 수 있다.

{% embed url="https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=false&corejs=3.21&spec=false&loose=false&code_lz=GYVwdgxgLglg9mABAQQA6oBQEoDeAoASACcBTKEIsDPRWxAgHgBMYA3APhru8YAsBGRDCaIAvIgDksKABsSE9rxIyZcRAHc4RGUwYB6AZ27d9LDl1pY8AXyA&debug=false&forceAllTransforms=false&modules=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=env%2Creact%2Cstage-2&prettier=false&targets=&version=7.21.4&externalPlugins=&assumptions=%7B%7D" %}

#### Example2

```javascript
//jsx코드
function App(){
	return(
    	<Greeting name="world" />
    )
}
```

```javascript
//변환된 js코드
function App() {
  return React.createElement(Greeting, { name: "world" });
}
```

#### Example3

```javascript
//jsx코드
function App(){
	return(
    	<Button type="submit">Send</Button>
    )
}
```

```javascript
//변환된 js코드
function App() {
  return React.createElement(Button, { type: "submit" }, "Send");
}
```

#### Example4

```javascript
//jsx코드
function App(){
	return(
    	<div className="test">
	    <p>Hello, world!</p>
	    <Button type="submit">Send</Button>
        </div>
    )
}
```

```javascript
//변환된 js코드
function App() {
  return React.createElement(
	"div",
	{ className: "test" },
	React.createElement("p", null, "Hello, world!"),
	React.createElement(Button, { type: "submit" }, "Send")
        );
}
```

#### Example5

```javascript
//jsx코드
function App(){
	return(
	<div>
		<p>Count: {count}!</p>
		<button type="button" onClick={() => setCount(count + 1)}>Increase</button>
	</div>
    )
}
```

```javascript
//변환된 js코드
function App() {
  return React.createElement(
	"div",
	null,
	React.createElement("p", null, "Count: ", count, "!"),
	React.createElement("button", { type: "button", onClick: () => setCount(count + 1) }, "Increase")
	);
}
```



이런식으로 JSX를 제외하고 React.createElement라는 자바스크립트의 문법을 활용하여 프로젝트를 만들어 갈 수도 있다. 그러나 프로젝트의 규모가 커지다 보면 JSX가 제공하는 편리함을 제외하고 프로젝트를 만들어 가기에 다소 힘들 수 있다. 즉 JSX는 프로젝트를 만들어가는 방식을 편리하게 해주는 **Syntactic sugar**라고 할 수 있고, 필수적인 것 아니다.

### Syntactic sugar

직역하면 문법적 설탕이라고 한다. 문법적인 기능은 그대로인데 사람이 직관적으로 쉽게 코드를 읽을 수 있게 만든다는 의미를 가지고 있다.

* 중복되는 로직을 간결하게 표현하기 위해 사용한다.



### React Element & React.createElement

React.createElement는 React 엘리먼트를 생성하는 자바스크립트의 문법이다. JSX는  React.createElement를 호출하는 편리한 문법이고, 즉 Syntactic suger이다. 그래서 JSX를 사용하지 않고도 React Element를 구성해 나갈 수 있다.

#### React.createElement의 문법

* 지금까지 위에서 예시로 해본 React.createElement의 기본 구조는 다음과 같다.

```javascript
React.createElement(태그명, 태그속성값, value값);}
```

첫번째 항목은 넣을 태그에 대한 파라미터이다. 흔히 \<div>, \<p>등과 같은 html태그가 있고, component로 사용되는 태그도 입력이 가능하다.

두번째 항목은 태그에 넣을 속성값이다. 여기서 입력하는 태그의 class, style, id 같은 값들을 지정해 줄 수가 있다. 형태는 오브젝트 자료형을 띄고 {id : 'hihi', class : 'byby'}와 같은 형태이다.

세번째 항목은 내용값, innerHTML이라고 생각하면 된다. 실제로 화면에 표시되는 내용을 입력하는 부분이다.

### React StrictMode

```javascript
main.tsx

root.render((
	<React.StrictMode>
		<App />
	</React.StrictMode>
));
```

위와 같이, 렌더링 과정에서 상위 노드로 React.StrintMode를 선언하면서 사용할 수 있다. Strict라는 말처럼 더욱 깐깐하게 렌더링을 실행하고, 그중 하나로 2번의 출력을 제공한다. 2번의 출력을 각각 비교함으로써, 디버그를 할 수 있다.\




### VDOM(Virtual DOM)이란?

직역하면 가상의 DOM이다. 'VDOM은 이상적이거나 가상적인 표현을 메모리에 저장하고 ReactDOM과 같은 라이브러리에 의해 실제 DOM과 동기화하는 프로그래밍 개념이다.'라고 React공식문서에 정의하고 있다.

```javascript
//reactDOM을 사용하는 방법!!
import ReactDOM from 'react-dom/client';
```

ReactDOM은 위의 코드를 활용해 실행한다. (실제 DOM과 동기화를 한다!)







### DOM이란?&#x20;

DOM은 간단히 말해 HTML문서를 브라우저가 이해할 수 있도록 만든 Tree 자료구조이다.&#x20;

DOM에 대해 더 알고 싶다면 아래의 링크로!!

{% content-ref url="../additional/undefined/1.-dom.md" %}
[1.-dom.md](../additional/undefined/1.-dom.md)
{% endcontent-ref %}



<figure><img src="../.gitbook/assets/image (2).png" alt=""><figcaption><p>브라우저의 동작방식</p></figcaption></figure>

### Reconciliation(재조정) 과정은 무엇인가?

DOM을 조작할때 VDOM을 활용하여 변경사항을 입력하는데, 그러면 React는 VDOM의 변경사항과 DOM의 기존 상황을 비교하여 작업을 처리하는데 이를 재조정(Reconciliation)이라고 한다. 결국 바로 변화를 입력하는 방식이 아니라 기존의 DOM과 비교하고 입력하기에 2번의 일을 하는 것과 같지만 이러한 과정을 거쳐 동작하고 있다.

### 결국 VDOM을 사용하는 이유

SPA(single page application)은 CSR(client side rendering)이라는 특징을 가지고 있기에, DOM조작이 자주 일어날 수 밖에 없다. React는 SPA를 만들기에 특화된 프레임워크이기에 DOM조작이 일어난다. 그렇기에 DOM조작이 비효율적으로 동작하거나, 유지보수가 힘들다면 사용에 불편함이 될 것이다. 이러한 상황을 막기 위해 VirtualDOM이 존재하며 효율적으로 DOM을 조작하는데 도움을 준다. 또한 **선언적API**를 가능케하여 더 나은 구조를 제공한다.&#x20;

* 선언적 API : 우리가 리액트에게 원하는 UI의 상태를 알려주면(선언적), 그 상태를 기반으로 DOM은 자동적으로 업데이트를 하는 것  = VDOM과 DOM을 비교해 변경사항이 있을시 화면에 변화를 나타낸다.

이렇다 저렇다 해도 결국 우리는 VDOM이 무엇인지, 어떻게 작동하는 지 알고 최적화를 하기 위해 노력해야 한다는 것이 중요하다.
