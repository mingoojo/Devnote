# Canvas 기초

## Canvas란?

컨버스는 HTML에서 제공하는 엘리먼트로써, 자바스크립트를 통해 그림을 그리고 애니메이션과 이벤트 처리 등을 구현할 수 있다.



### Canvas 생성하기

컨버스는 다른 엘리먼트들과 같이 `<canvas></canvas>`를 선언하여 생성할 수 있다. 그러나 컨버스는 js를 통해 여러가지 애니메이션 효과나 변화들을 넣어주기 위해 존재하기에, js를 통해 생성하고 관리하는 방식으로 구동해보자!

```javascript
index.html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
</head>
<body>
    <script src="./main.js"></script>
</body>
</html>
```

* 일단 main.js를 연동한 html파일을 하나 생성해주자!

```javascript
main.js
class App{
    constructor(){
        this.canvas = document.createElement('canvas') // 컨버스 엘리먼트생성
        document.body.appendChild(this.canvas) //컨버스 엘리먼트 body에 넣기
        this.canvas.width = this.canvas.parentElement.clientWidth; // 컨버스의 넓이는 부모의 넓이를 따라간다.
        this.canvas.height = this.canvas.parentElement.clientHeight; // 컨버스의 높이는 부모의 높이를 따라간다.
        this.ctx = this.canvas.getContext('2d')
        window.onresize = ()=>{
            this.setCanvasSize(); //브라우져 리사이징을 할때마다 컨버스의 높이와 크기를 변경하라.
        }
    }
    setCanvasSize(){
        this.canvas.width = this.canvas.parentElement.clientWidth;
        this.canvas.height = this.canvas.parentElement.clientHeight;
    }
}
window.onload = () => {
    new App
}
```

자바스크립트의 클래스를 활용하여 컨버스를 생성하도록 만들었다. 컨버스는 다양한 함수들로 변화를 해주기 때문에 기능이 많아질 수록 클래스를 활용하여 관리해주는게 좋다는 걸 깨닫는다.&#x20;

* 첫째로 클래스를 선언하고 윈도우가 온로드되면 클래스를 실행하도록한다.
* 둘째로 constructor를 활용하여 canvas의 기본 세팅을 해준다.

<figure><img src="../../.gitbook/assets/image (2) (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

이렇게 설정하고 크롬의 개발자 도구를 켜보면 다음과 같은 화면이 나온다. js를 활용하여 컨버스를 생성해보았다.



### 컨버스에 도형 그리기

컨버스에 무언가를 그리기 위해 constructor에 다른 함수를 연동시킨다.



```javascript
main.js
class App{
    constructor(){
        this.canvas = document.createElement('canvas')
        document.body.appendChild(this.canvas)
        this.canvas.width = this.canvas.parentElement.clientWidth;
        this.canvas.height = this.canvas.parentElement.clientHeight;
        this.ctx = this.canvas.getContext('2d')
        window.onresize = ()=>{
            this.setCanvasSize();
        }
        this.new1()
    }
    setCanvasSize(){
        this.canvas.width = this.canvas.parentElement.clientWidth;
        this.canvas.height = this.canvas.parentElement.clientHeight;
        this.new1()
    }

    new1(){
        this.ctx.beginPath(); // 도형그리기 시작
        this.ctx.rect(0, 0, 250, 260); //(0px, 0px부터 시작하는 250px * 260px짜리 사각형 그리기)
        this.ctx.fillStyle = "#FF0000"; // 내부 색 지정
        this.ctx.fill(); // 그리기
        this.ctx.closePath(); // 도형그리기 종료
    }
}
window.onload = () => {
    new App
}
```

이런 식으로 `constructor`와 `setCanvasSize`라는 함수에 `new1()`이라는 도형 그리기 함수의 실행명령을 같이 걸어주어, 도형이 계속 그려저 있도록 하였다.
