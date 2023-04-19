# 웹 표준을 준수하는 방법

### 1. DOCTYPE 선언

웹 페이지의 최상단에 DOCTYPE을 선언하여 웹 페이지가 어떤 버전의 HTML, XHTML을 사용하는지 명시한다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>HTML !DOCTYPE declaration</title>
</head>
```

### 2. 시맨틱 태그 사용

시맨틱 태그 또는 'Semantic Markup'로, `<header>`, `<nav>`, `<section>`, `<footer>`등의 태그를 사용하여 웹페이지의 구조를 명확하게 표현 가능하다.

```html
<body>
  <header>
    <h1>시맨틱 태그 예제</h1>
    <nav>
      <ul>
        <li><a href="#">메뉴1</a></li>
        <li><a href="#">메뉴2</a></li>
        <li><a href="#">메뉴3</a></li>
      </ul>
    </nav>
  </header>
  
  <section>
    <h2>섹션 1</h2>
    <p>본문 내용입니다.</p>
  </section>
  <footer>
    <p>저작권 © 2021 Upstage. All Rights Reserved.</p>
  </footer>
</body>

```

### **3. CSS 스타일 시트 사용**

CSS 스타일 시트를 사용하여 디자인과 레이아웃을 분리하고, 웹 페이지의 내용과 디자인을 분리하여 유지보수 및 확장성을 높일 수 있다.

```html
<!DOCTYPE html>
<html lang="ko">
<head>
    <meta charset="UTF-8">
    <title>HTML !DOCTYPE declaration</title>
    <link href="test.css" rel="stylesheet"> <!-- css 파일 분리 -->
</head>
```

### **4. 웹 접근성 고려**

웹 페이지를 만들 때 모든 사용자가 쉽게 접근할 수 있도록 웹 접근성을 고려해야 한다. 예를 들어, 시각 장애인이 스크린 리더를 사용하여 웹 페이지를 읽을 수 있도록 `alt` 속성을 사용하여 이미지에 대한 설명을 제공하거나, 키보드만으로 모든 기능을 사용할 수 있도록 tabindex 속성을 사용하는 등의 세심한 작업이 필요하다.

```html
<img src="./main.jpg" alt="웹페이지로고">
```

### 웹표준 검사 사이트

아래의 사이트는 웹 표준을 검사하는 사이트이다.

{% embed url="https://validator.w3.org/" %}

{% embed url="https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-%EC%9B%B9-%ED%91%9C%EC%A4%80%EC%9D%98-%EC%9D%B4%ED%95%B4" %}
