# VDOM

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

{% content-ref url="../additional/undefined/dom.md" %}
[dom.md](../additional/undefined/dom.md)
{% endcontent-ref %}



<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>브라우저의 동작방식</p></figcaption></figure>

### Reconciliation(재조정) 과정은 무엇인가?

DOM을 조작할때 VDOM을 활용하여 변경사항을 입력하는데, 그러면 React는 VDOM의 변경사항과 DOM의 기존 상황을 비교하여 작업을 처리하는데 이를 재조정(Reconciliation)이라고 한다. 결국 바로 변화를 입력하는 방식이 아니라 기존의 DOM과 비교하고 입력하기에 2번의 일을 하는 것과 같지만 이러한 과정을 거쳐 동작하고 있다.

### 결국 VDOM을 사용하는 이유

SPA(single page application)은 CSR(client side rendering)이라는 특징을 가지고 있기에, DOM조작이 자주 일어날 수 밖에 없다. React는 SPA를 만들기에 특화된 프레임워크이기에 DOM조작이 일어난다. 그렇기에 DOM조작이 비효율적으로 동작하거나, 유지보수가 힘들다면 사용에 불편함이 될 것이다. 이러한 상황을 막기 위해 VirtualDOM이 존재하며 효율적으로 DOM을 조작하는데 도움을 준다. 또한 **선언적API**를 가능케하여 더 나은 구조를 제공한다.&#x20;

* 선언적 API : 우리가 리액트에게 원하는 UI의 상태를 알려주면(선언적), 그 상태를 기반으로 DOM은 자동적으로 업데이트를 하는 것  = VDOM과 DOM을 비교해 변경사항이 있을시 화면에 변화를 나타낸다.

이렇다 저렇다 해도 결국 우리는 VDOM이 무엇인지, 어떻게 작동하는 지 알고 최적화를 하기 위해 노력해야 한다는 것이 중요하다.

