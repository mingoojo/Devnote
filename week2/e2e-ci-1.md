# E2E, CI

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

Scenario('Visit the home page', ({I}) => {
	I.amOnPage('/');

	I.see('Hello, world!');

	I.seeElement('//img[@src= "/images/test.jpg"]');
});
```

이렇게 작성하고 npm run codeceptjs를 작동하면 알아서 홈페이지에 들어가 Hello, world!라는 문구를 확인 할 수 있는지 체크하고 테스트 통과 여부를 표시한다!

