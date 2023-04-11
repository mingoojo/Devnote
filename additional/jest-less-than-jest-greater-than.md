# Jest란? \<Jest작성해보기>

### Jest

Jest는 페이스북에서 개발한 테스팅 라이브러리로, 자바스크립트 기반의 테스팅에 사용된다.



### More

페이스북에서는 Jest를 단순한 테스팅 라이브러리가 아닌 “테스팅 프레임워크”라고 부르는 만큼 기존 자바스크립트 테스팅 라이브러리와는 차별점이 있다. Jest 이전에는 자바스크립트 코드를 테스트하라면 여러 가지 테스팅 라이브러리를 조합해서 사용하곤 했었다. 예를 들어, Mocha나 Jasmin을 Test Runner로 사용하고, Chai나 Expect와 같은 Test Matcher를 사용했으며, 또한 Sinon과 Testdouble 같은 Test Mock 라이브러리도 필요했었다. 하지만 Jest는 라이브러리 하나만 설치하면, Test Runner와 Test Matcher 그리고 Test Mock 프레임워크까지 제공해주기 때문에 상당히 편리하게 느껴진다.



### Jest 세팅하기

#### 폴더를 생성하고 NPM init한다.

```powershell
// 터미널
$ mkdir my-jest
$ npm init -y
```



#### jest 라이브러리 설치

Jest 라이브러리를 개발 의존성(-D)으로 설치한다.

```
// 터미널
$ npm install -D jest
```



#### package.json 수정

package.json 파일의 test항목을 수정한다.

```
// package.json

"scripts": {
  "test": "jest"
},
```

이렇게 한 후 터미널에 '$npm test'로 jest를 실행할 수 있다.



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

toXxx부분에 Matcher함수가 사용된다.

#### test.js 내용작성

```
// test.js
test("1 is 1", () => {
  expect(1).toBe(1);
});
```

#### npm test

터미널에  npm test를 입력하면 아래와 같은 화면이 나온다.

```
$ npm test

> my-jest@1.0.0 test /my-jest
> jest

 PASS  ./test.js
  ✓ 1 is 1 (3ms)

Test Suites: 1 passed, 1 total
Tests:       1 passed, 1 total
Snapshots:   0 total
Time:        0.868s, estimated 1s
Ran all test suites.
```



`npm test`를 실행하면 프로젝트 내에 모든 테스트 파일을 찾아서 테스트를 실행해준다. Jest는 기본적으로 `test.js`로 끝나거나, `__test__` 디렉터리 안에 있는 파일들은 모두 테스트 파일로 인식하는데, 만약 특정 테스트 파일만 실행하고 싶은 경우에는 `npm test <파일명이나 경로>`를 입력하면 된다.





[https://www.daleseo.com/](https://www.daleseo.com/) 참고

