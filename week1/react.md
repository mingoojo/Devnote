# react

### React의 특징

* 리액트는 컴포넌트 단위의 인터페이스를 만드는 것에 특화되어 있다.
* 리액트는 javascript기반의 프레임워크로 javascript에서 사용하는 문법을 사용 할 수 있다.
* 인터랙션으로 반응한다. 즉 실시간으로 렌더링을 하기에 부드럽게 내용의 변화를 보여줄 수 있다.



### 렌더링

리엑트에서 렌더링이란 컴포넌트가 UI를 구성하도록 작업을 요청하는 것을 의미한다.



#### 렌더링 과정

리엑트에서 렌더링 개념은 Root DOM(\<div id = 'root'>\</div>)로부터 시작해 플래그가 있는 모든 컴포넌트를 찾아서 렌더링을 진행하는 것을 의미한다.

```
// index.html

<body>
    <div id="root"></div>
</body>
```

index.html에서 렌더링 된 컴포넌트들이 표현될 위치는 body의 id=root값을 갖는 곳이다.



```
// main.tsx
function Greeting() {
  return (
    <p>Hello, world!</p>
  );
}

function main() {
  const element = document.getElementById('root');

  if (!element) {
    return;
  }

  const root = ReactDOM.createRoot(element);
  root.render(<Greeting />);
}

main();
```

Greeting()이라는 함수를 main()의 root.render에 컴포넌트로 입력하여 index.html의 root부분에 그려낸다.



### 리렌더링

리액트에선 초기에 한번 렌더링을 진행하고, 그 이후에 특정 조건이 발생하면 다시 렌더링을 진행하는 리렌더링이라고 한다.

#### React가 리렌더링을 하는 조건

* 내부 상태(state)변경시
* 부모에게 받는 값(props)변경시
* 부모 컴포넌트가 리렌더링 되는 경우

결국 리엑트에서 리렌더링은 모든 상태 변경에서 시작된다.

