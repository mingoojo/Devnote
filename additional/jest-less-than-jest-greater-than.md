# Jest에 대하여

### Jest

Jest는 페이스북에서 개발한 테스팅 라이브러리로, 자바스크립트 기반의 테스팅에 사용된다.



### More

페이스북에서는 Jest를 단순한 테스팅 라이브러리가 아닌 “테스팅 프레임워크”라고 부르는 만큼 기존 자바스크립트 테스팅 라이브러리와는 차별점이 있다. Jest 이전에는 자바스크립트 코드를 테스트하라면 여러 가지 테스팅 라이브러리를 조합해서 사용하곤 했었다. 예를 들어, Mocha나 Jasmin을 Test Runner로 사용하고, Chai나 Expect와 같은 Test Matcher를 사용했으며, 또한 Sinon과 Testdouble 같은 Test Mock 라이브러리도 필요했었다. 하지만 Jest는 라이브러리 하나만 설치하면, Test Runner와 Test Matcher 그리고 Test Mock 프레임워크까지 제공해주기 때문에 상당히 편리하게 느껴진다.



### Jest 세팅하기

#### 폴더를 생성하고 npm init한다.

```powershell
// 터미널
$ mkdir my-jest
$ cd my-jest
$ npm init -y
```



#### jest 라이브러리 설치

Jest 라이브러리를 개발 의존성(-D)으로 설치한다.

```
// 터미널
$ npm install -D jest
```



#### package.json 수정

`package.json` 파일의 test항목을 수정한다.

```
// package.json

"scripts": {
  "test": "jest"
},
```

이렇게 한 후 터미널에 `npm test`로 jest를 실행할 수 있다.



### 테스트 코드 작성해보기

#### 테스트 파일 생성하기

```
// 터미널
$touch test.js
```

#### test.js 의 기본형 설정하기

jest를 활용한 테스트파일은 다음과 같은 형식으로 작성된다.

```
test("테스트 설명", () => {
  expect("검증 대상").toXxx("기대 결과");
});
```

`toXxx`부분에 Matcher함수가 사용된다.

#### test.js 내용작성

```
// test.js
test("adding", () => {
  expect(1+2).toBe(3);
});
```

**1+2의 값이 3이 되는가?** 라는 뜻을 가진 테스트 내용이다.

#### npm test

터미널에  `npm test`를 입력하면 테스트의 값이 통과가 되는지 안되는지를  평가한다. `test.js`에 **1+2의 값이 3이 되는가?** 라는 테스트값을 입력후 `npm test`을 입력하면 아래와 같이 나온다.

```
$ npm test

> jesttest@1.0.0 test
> jest

 PASS  ./test.js
  √ adding (1 ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        0.373 s, estimated 1 s
Ran all test suites.
```



`npm test`를 실행하면 프로젝트 내에 모든 테스트 파일을 찾아서 테스트를 실행해준다. Jest는 기본적으로 `test.js`로 끝나거나, `__test__` 디렉터리 안에 있는 파일들은 모두 테스트 파일로 인식하는데, 만약 특정 테스트 파일만 실행하고 싶은 경우에는 `npm test <파일명이나 경로>`를 입력하면 된다.



### Matcher함수의 종류!

#### toEqual() <a href="#toequal" id="toequal"></a>

아래와 같은 함수에 1이라는 값을 넣으면 `` email: `user1@test.com` ``이 나오는지 확인하는데, `toBe()` Matcher를 사용하면 에러가 난다.

```
function getUser(id) {
  return {
    email: `user${id}@test.com`
  };
}


test("EditEmail", () => {
    expect(getUser(1)).toBe({
      email: `user1@test.com`
    });
  });
```

이러한 경우 `toEqual()`로 Matcher부분을 교체하면 통과하게됩니다.

```
function getUser(id) {
  return {
    email: `user${id}@test.com`
  };
}


test("EditEmail", () => {
    expect(getUser(1)).toEqual({
      email: `user1@test.com`
    });
  });
  
  
$ npm test

> my-jest@1.0.0 test /my-jest
> jest

 PASS  ./test.js
  ✓ EditEmail (3ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        0.91s, estimated 1s
Ran all test suites.
```

#### toBeTruthy(), toBeFalsy() <a href="#tobetruthy-tobefalsy" id="tobetruthy-tobefalsy"></a>

느슨한 타입 기반 언어인 자바스크립트는, 자바같은 강한 타입 기반 언어처럼 `true`와 `false`가 boolean 타입에 한정되지 않는다. 따라서 숫자 `1`이 `true`로 간주되고, 숫자 `0`이 `false`로 간주되는 것과 같이 모든 타입의 값들을 `true` 아니면 `false` 분류하려는 규칙이 있다.`toBeTruthy()`는 검증 대상이 이 규칙에 따라 `true`로 간주되면 테스트 통과이고, `toBeFalsy()`는 반대로 `false`로 간주되는 경우 테스트가 통과됩니다.

```
test("booleantest", () => {
  expect(0).toBeFalsy();  //통과 
  expect("0").toBeTruthy(); //통과
});
```

위에 값 '0'은 `falsy`한 값이다. 자바스크립트에서 `false`, `null`, `undefined`, `0`, `NaN`, '  '는 `falsy`한 값이라 `toBeFalsy()`라는 Matcher에 통과하고, 아래의 `'0'`은 숫자 0이 아니라 0(string)이라 `toBeTruthy()`라는 Matcher에 통과한다.



#### toHaveLength(), toContain() <a href="#tohavelength-tocontain" id="tohavelength-tocontain"></a>

특정 배열에 길이를 체크할때 `toHaveLength()`라는 Matcher를 사용하고, 배열에 특정항목이 포함되어 있는지 확인할때 `toContain()` Matcher를 사용한다.

```
colorAry = ['red', 'green', 'yellow']
test('arrayinfo', ()=>{
  expect(colorAry).toHaveLength(3); // colorAry의 배열의 갯수가 3개이다.
  expect(colorAry).toContain('red'); // colorAry에 'red'가 포함되어 있다.
  expect(colorAry).not.toContain('white'); // colorAry에 'white'가 포함되어 있지 않다.
});
```

[https://www.daleseo.com/](https://www.daleseo.com/) 참고

