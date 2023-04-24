# Testing Library

## jest

Jest는 페이스북에서 개발한 테스팅 라이브러리로, 자바스크립트 기반의 테스팅에 사용된다. 거이 모든 것을 갖춘 테스팅 도구



### 기본 테스트 코드

```
touch src/main.test.ts

test("테스트 설명", () => {
  expect("검증 대상").toXxx("기대 결과");
});
```

작성 후에 npm test를 하면 위에 코드가 맞는지 검사를 해준다. test코드에 이름, 검증대상, 기댓값이 필요하다.

```
test("test", () => {
  expect(1+2).toBe(3);
});

//터미널
npm test //입력!!

src/main.test.ts
Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        0.1 s, estimated 1 s
Ran all test suites. // 출력
```

아래와 같이 1+2의 값이 3이라고 출력

package.json에 "watch:test": "jest --watchAll"을 입력해두었기에, npm jest --watchAll을 입력하면 변경후 저장할때마다 터미널창에 내용을 띄운다



#### describe + it  활용

describe를 사용해서 작은 단위의 테스트 코드를 그룹화할 수 있다. 테스트 코드들은 it으로 구분한다.

```
describe("테스트 설명", () => {
    it('rename', () => {
        expect(add(1, 2)).toBe(3);
    });
    
    it('rename2', () => {
        expect(add(3, 2)).toBe(5);
    });
});
```

#### 비교 Matcher : toBeGreaterThan(),  toBeLessThan()

기댓값의 크기를 비교할때 사용할 수 있다.

```
describe("테스트 설명", () => {
    context('2개의 양수가 주어졌을때', ()=>{
        it('rename', () => {
            expect(add(1, 2)).toBeGreaterThan(2);
            expect(add(1, 2)).toBeGreaterThan(4);
    }});
});
```

'2개의 양수가 주어졌을때, 더한 값은 1보다 크다.', '2개의 양수가 주어졌을때, 더한 값은 4보다 작다.' 두가지를 테스트 하는 코드이다.



### React Testing Library

리엑트작업중에 만들어진 컴포넌트의 타당성(?)을 테스트하는 방식

```
//Greeting.tsx
export default function Greeting({name}:{name:string}){
    return (
        <p>Hello, {name}</p>
    )
}
```

#### case. 1 : 'greeting'이 잘 렌더링 되는지 확인하는 방법

```
//Greeting.test.tsx
import { render, screen } from "@testing-library/react"
import Greeting from "./greeting"

test('greeting', ()=>{
    render(<Greeting name='world'/>)
})
```

#### case. 2 : 'greeting'의 렌더링 값이 'Hello, world'인지 확인하는 방

```
//Greeting.test.tsx
import { render, screen } from "@testing-library/react"
import Greeting from "./greeting"

test('greeting', ()=>{
    render(<Greeting name='world'/>)
    screen.getByText('Hello, world')
})
```

#### case. 3 : 'greeting'의 렌더링 값에 'hi'가 포함되어있는지 확인하는 방법

```
//Greeting.test.tsx
import { render, screen } from "@testing-library/react"
import Greeting from "./greeting"

test('greeting', ()=>{
    render(<Greeting name='world'/>)
    screen.getByText(/hi/) //정규식 문법을 활용!
})
```

getByText 대신 quaryByText를 쓰면 에러가 아닌, 없으면 없는 걸로 나온다.



### TDD(Test Driven Development)

* 테스트 주도적 개발이라는 뜻이다.
* 기능을 업그레이드 할때마다 다른 것도 테스트를 다시 해봐야한다.&#x20;
* 작성한 코드가 원하는 값이 나오는 지 확인후 적용하는 방식으로 개발을 이끌어간다.



#### Testing 라이브러리 사용해보니...

테스팅 도구는 처음 사용해 보았다. 그래서 그런지, 최대한 많은 것을 적을려고 했다. 이외에도 많은 테스트 방식, 비교법이 있는것 같다. 따로 jest를 공부해야겠다.



