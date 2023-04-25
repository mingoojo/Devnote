# EP.1

## React의 State

변경을 다루기 위한요소!!! 그냥 JS를 사용하지 않고, State를 사용하는 이유는 재랜더링때문이다. State가 변경될때 하위 컴포넌트까지 재랜더링이 일어난다.

state의 사용 기본 형태

```javascript
app.tsx
import { useState } from 'react';

export default function ProductsInCategory ({
let [statename, setstatename] = useState(1)

    return (
        <div></div>    
    )
} 
```

### state로 사용되어질 조건

* 변경이 일어날 요소
* props로 전달될 요소는 state가 아님.
* 다른 state나 props를 이용해 계산 가능하다면 state가 아님.

