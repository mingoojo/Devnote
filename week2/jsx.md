# JSX

### XML이란?

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

JSX는 리엑트로 프로젝트를 개발할 때 사용하는 언어이므로, 자바스크립트 문법은 아니다. 또한 JSX는 하나의 파일에 자바스크립트와 HTML을 동시에 작성할 수 있어서 편리하다. 또한 HTML과 비슷한 형태를 띄고 있기에 가독성이 좋다.

#### JSX문법의 형태

```javascript
main.tsx

function App() {
	return (
		<div>
			<div>Hello</div>
			<div>World!</div>
		</div>
	);
}
```

위의 형태는 React를 작성하다보면 가장 많이 보는 형태이다. 저 형태의 구문이 JSX형태의 구문이고, 컴파일러를 통해 자바스크립트의 언어로 변환된 코드는 아래와 같다.

```javascript
main.tsx

function App() {
  return React.createElement("div", null, React.createElement("h1", {
    id: "title"
  }, "hello world"));
}
```

아래의 링크를 통해BABEL컴파일러를 통해  JSX를 자바스크립트 언어로 변환하는 것을 해볼 수 있다.

{% embed url="https://babeljs.io/repl#?browsers=defaults%2C%20not%20ie%2011%2C%20not%20ie_mob%2011&build=&builtIns=false&corejs=3.21&spec=false&loose=false&code_lz=GYVwdgxgLglg9mABAQQA6oBQEoDeAoASACcBTKEIsDPRWxAgHgBMYA3APhru8YAsBGRDCaIAvIgDksKABsSE9rxIyZcRAHc4RGUwYB6AZ27d9LDl1pY8AXyA&debug=false&forceAllTransforms=false&modules=false&shippedProposals=false&circleciRepo=&evaluate=false&fileSize=false&timeTravel=false&sourceType=module&lineWrap=true&presets=env%2Creact%2Cstage-2&prettier=false&targets=&version=7.21.4&externalPlugins=&assumptions=%7B%7D" %}

### Syntactic sugar

직역하면 문법적 설탕이라고 한다. 문법적인 기능은 그대로인데 사람이 직관적으로 쉽게 코드를 읽을 수 있게 만든다는 의미를 가지고 있다.

* 중복되는 로직을 간결하게 표현하기 위해 사용한다.

### React Element

### React.createElement

React.createElement는 React 엘리먼트를 생성하는 자바스크립트의 문법이다. JSX는  React.createElement를 호출하는 편리한 문법이고, 즉 Syntactic suger이다.

### React StrictMode

### VDOM(Virtual DOM)이란?

* DOM이란?
* DOM과 Virtual DOM의 차이

### Reconciliation(재조정) 과정은 무엇인가?

### React에서 JSX를 사용하는 목적
