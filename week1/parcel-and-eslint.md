# 5. Parcel & ESLint

### parcel이란?

특별한 설정없이 바로 사용 가능한 빌드 도구. SWC를 사용해 기존 도구보다 빠르다.(Vite도 빠름)

* SWC : RUST로 짜여진 컴파일러로, 속도와 성능 개선에 초점을 맞추고 있으며, 기존의 Babel 등의 트랜스파일러를 압도적으로 뛰어넘는 성능을 보여준다.



#### &#x20;Parcel 기본 설정!

* package.json에 "main": "main.js"대신에 "source": "./index.html"입력하기!

npm start를 했을때 폴더의 index.html을 기본으로 실행해 준다.

* npm install -D parcel-reporter-static-files-copy 후 touch .parcelrc로 파일 생성 후 아래의 내용을 넣어준다.

```
{
  "extends": ["@parcel/config-default"],
  "reporters":  ["...", "parcel-reporter-static-files-copy"]
}
```

이후 static폴더를 생성하고, 폴더안에 이미지 파일을 넣으면 자유롭게 사용 가능하다.

#### 빌드 + 정적 서버 실행

npx parcel build

npx servor dist

전체 파일을 빌드하고 servor를 활용해 실제 배포되는 형태를 점검할 수 있다.



### ESLint

자바스크립트 코드에서 발견되는 문제시되는 패턴들을 식별하기 위한 정적 코드 분석 도구, 한마디로 문제를 발견하는 도구이다. 아래와 같은 기능을 도와 줄 수 있다.

* 스타일 통일
* 잠재적 문제 발견
* Best Practice추천 >>> 일관성 있는 코드를 작성할 수 있다, 최신 트렌드의 코드로 작성된다.

Lint : 소스 코드를 분석하여 프로그램 오류, 버그, 스타일 오류, 의심스러운 구조체에 표시(flag)를 달아놓기 위한 도구들을 가리킨다.

package.json script에 "lint": "eslint --fix --ext .js,.jsx,.ts,.tsx ."를 작성 후, npm run lint로 자동 수정이 가능하다.



#### vscode에서 자동 lint되게 하기

프로젝트에 .vscode폴더를 생성, settings.json파일 생성

```json
{
   "editor.rulers": [
      80
  ],
    "editor.codeActionsOnSave": {
      "source.fixAll.eslint": true
    }
}
```

아래와 같이 작성하고 세이브하면 자동으로 저장할때마다 npm run lint를 작동시킨다.
