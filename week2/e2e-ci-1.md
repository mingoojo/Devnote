# 3. E2E, CI

## E2E란?

E2E(end to end)test는 개발물을 사용자 관점에서 테스트 하는 방법이다. 페이지에서 원하는 텍스트가 출력되는지, 버튼 클릭시 올바른 동작을 수행하는 지 등을 테스트 한다.

### E2E프레임워크

E2E프레임 워크는 selenium, testCafe, cypress, codecept등이 있고 우리는 codecept를 사용하기 위한 세팅과 사용법을 알아보자!



## codeceptjs 세팅 및 사용법!

codeceptjs를 npx를 활용하여 설치하자!

```
npx create-codeceptjs .
```

이후 codeceptjs의 환경설정및 초기화를 해준다.

```
npx codeceptjs init
```

이렇게 하면 항목을 선택해가면서 초기세팅값을 잡아 줄 수있다.

```powershell
// 테스트를 원하는 폴더 선택
? Where are your tests located? /test/**/*_test.js
// 어떤 헬퍼를 사용할지 선택
? What helpers do you want to use? Playwright
// 스크린샷과 같은 자료 저장 폴더 지정
? Where should logs, screenshots, and reports to be stored? ./output
// 언어선택
? Do you want localization for tests? (See https://codecept.io/translation/ English (no localization)
// 기본 베이스 url 선택 - 개발환경에서의 테스트라 localhost로 지정한다.
? [Playwright] Base url of site to be tested (http://localhost)
// 브라우저 윈도우 선택
? [Playwright] Show browser window Yes
// 테스트 브라우져 = chromium
? [Playwright] Browser in which testing will be performed. Possible options: chromium,
•firefox or webkit chromium
```

테스트 폴더에 `home_test.ts`파일을 만들어서 테스트를 진행해보자!

```javascript
home_test.ts

Feature('Home');

Scenario('home page', ({I}) => {
	I.amOnPage('/');

	I.see('Hello, world!');

	I.seeElement('//img[@src= "/images/test.jpg"]');
});
```

이렇게 작성하고 npm run codeceptjs를 작동하면 알아서 홈페이지에 들어가 Hello, world!라는 문구를 확인 할 수 있는지 체크하고 테스트 통과 여부를 표시한다!



### 진행중 문제점

```
# 개발용 서버 실행
$ npm start

# E2E 테스트 실행
$ npm run codeceptjs
```

개발한 환경을 `localhost`에서 확인하기 위해서는 최소 2개의 터미널을 띄워두어야 한다. `npm start`명령어를 실행하기 위한 터미널과 , codecept를 구동하기 위한 터미널! 사실 문제점은 아니긴 하다! 터미널2개 열어두고 하면 잘 돌아가기 때문!!  근데 그냥 이게 맞나 싶다...
