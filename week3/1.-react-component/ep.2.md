# EP.2

## React 예제로 연습해보자!

{% embed url="https://react.dev/learn/thinking-in-react" %}

## 선수지식

#### 반복문 등과 같은 선수 지식!

{% embed url="https://app.gitbook.com/o/aC7kAbQsee1CDu38FYh1/s/NFcheQASnhWo33ChDiGR/additional/undefined/tip/undefined" %}

#### React props

부모 컴포넌트와 자식 컴포넌트 사이의 자료를 주고 받는 방법!

```jsx
const products = [
	{ category: "Fruits", price: "$1", stocked: true, name: "Apple" },
	{ category: "Fruits", price: "$1", stocked: true, name: "Dragonfruit" },
	{ category: "Fruits", price: "$2", stocked: false, name: "Passionfruit" },
	{ category: "Vegetables", price: "$2", stocked: true, name: "Spinach" },
	{ category: "Vegetables", price: "$4", stocked: false, name: "Pumpkin" },
	{ category: "Vegetables", price: "$1", stocked: true, name: "Peas" }
  ]

export default function App(){
  return(
    <>
      <App2 products = {products}/> //App2는 App의 자식요소로 products라는 자료를 받는다.
    </>
  )
}

export function App2({products}){
  return(
    <div>{products[0].name}</div> //App()을 통해 products자료를 받아서 사용한다.
  )
}
```

위와 같은 방법으로 부모로부터 자료를 받아서 사용할 수 있다.

이제 파일을 Atomic Design으로 컴포넌트를 나누어보는 실습을 해보자!



아래의 실습링크를 확인해보자!

{% embed url="https://github.com/mingoojo/MT-week3.git" %}
