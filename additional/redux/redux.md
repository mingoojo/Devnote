# Redux 개념

## Redux란?

> Redux는 자바스크립트 앱을 위한 예측 가능한 상태 컨테이너이다.

먼저 리액트에서의 리덕스를 사용하는 이유는 전역적인 상태를 관리하기 위함이 가장 크다. props를 통해 state를 drilling해줄 필요 없이 사용이 가능하다는 것이 가장 큰 장점이 아닐까 싶다.



### **Redux의 기본 개념**

#### **1. Single source of truth**

* 동일한 데이터는 항상 같은 곳에서 가지고 온다.
* 스토어를 통한 데이터 공간을 이용한다.

#### **2. State is read-only**

* 리액트에서는 setState 메소드를 활용해야만 상태 변경이 가능하다.
* 리덕스에서도 액션이라는 객체를 통해서만 상태를 변경할 수 있다.

#### **3. Changes are made with pure functions**

* 변경은 순수함수로만 가능하다.
* 리듀서와 연관되는 개념이다.
* Store(스토어) – Action(액션) – Reducer(리듀서)

<figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

