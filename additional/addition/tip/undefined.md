# 반복문

## 반복문

### 기본형태(for문)

```javascript
let arr = [10, 20, 30, 40, 50]
for(let i = ; i<arr.length; i++){
    console.log(arr[i]) //  10, 20, 30, 40, 50이 차례로 console창에 찍힘
    console.log(i) // 0, 1, 2, 3, 4가 차례로 콘솔창에 찍힘
}
```

이 내용을 가지고 배열을 만들고 싶다면?

```javascript
let arr = [10, 20, 30, 40, 50]
let arr2 = []
let arr3 = []
for(let i = ; i<arr.length; i++){
    arr2.push(arr[i])
    arr3.push(arr[i]+1)
}
console.log(arr2) // [10, 20, 30, 40, 50]
console.log(arr3) // [10, 21, 32, 43, 54]
```

이거 조금 더 짧게는 못씀??

### 1. forEach()

```javascript
let arr = [10, 20, 30, 40, 50]
let arr2 = []
let arr3 = []
arr.forEach((a, i)=>{
    arr2.push(arr[i]) //또는 arr2.push(a)
    arr3.push(arr[i]+1) //또는 arr3.push(a+1)
})
console.log(arr2) // [10, 20, 30, 40, 50]
console.log(arr3) // [10, 21, 32, 43, 54]
```

forEach문을 활용하여 더 짧게 줄일 수 있다. 여기서 파라미터 a는 `arr`의 각항목을 의미하고(10, 20, 30 같은 값) i는 각항목의 순서을 의미한다.

여기서 더 줄일수는 없는가? 나는 arr2와 arr3같은 값이 빈값으로 존재하는게 싫다. 그냥 저기다가 함수를 넣을수는 없는가? 그렇다면 map함수를 써보자.

### 2. map()

```javascript
let arr = [10, 20, 30, 40, 50]
let arr2 = arr.map((a, i)=>{
  return a
})
console.log(arr2) // [10, 20, 30, 40, 50]
```

이런식으로 작성하면 더욱 간결하게 작성이 가능하다. 뭔가 forEach랑의 차이점이 무엇인지 모르겠다고 생각이 들 수도 있지만 map함수는 return문을 활용하여 반복을 돌린 값을 array자료형으로 받아볼 수 있다.

이제 `arr`중에서 20의 배수값만 찾아서 array로 받아보고 싶다... 그렇다면 어떻게 작성할까? if문을 활용하면 이렇게 작성을 할 수 있다.

```javascript
let arr = [10, 20, 30, 40, 50]
let arr2 = []
arr.forEach((a, i)=>{
  if(a%20 == 0){
    arr2.push(a)
  }
})
console.log(arr2) // [20, 40]
```

더 쉽게 작성하고 싶다... 눈에 안들어옴... 가독성 좋게 만들어보자!! filter함수를 활용해서!

### 3. filter()

```javascript
let arr = [10, 20, 30, 40, 50]
let arr2 = arr.filter((a, i)=>{
  return (a%20 == 0) // 만약 a%20이 0이면 return 하라는 뜻
})
console.log(arr2) //[20,40]
```

filter함수를 활용하면 이렇게 `array`자료 중 특정 조건에 맞는 값만 출력하는 게 가능하다.

filter와 비슷한 개념을 사용하는 것이 find()이다. 이건 조건에 맞는 값 중 가장 순번이 빠른 값을 찾아준다.

### 4. find() <a href="#find" id="find"></a>

```js
let arr = [10, 20, 30, 40, 50]
let arr2 = arr.find((a, i) => {
    return (a % 20 === 0)
})
console.log(arr2) // 20
```

find함수를 활용하면 다른 함수들과는 다르게 `array`값이 아닌 `number`, `string`과 같은 값이 얻어진다.

### 5. Reduce() : 결국 반복문의 꽃

위에 모든 기능들은 결국 이 함수 하나로 끝난다... 이걸로 모든 기능을 다 구현할 수 있다.. 하지만 기능이 많다는 건 파라미터 값이 많아지고, 식이 복잡하고.. 아무튼 이해하기 힘들다는 뜻이다. 그러나 배워두면 참 좋다!

#### 사칙연산 중 덧셈만 해보자

기본부터 배워보자! reduce를 활용하여 항목의 값을 더해보자.

```javascript
//모든 항목의 합을 구하자!
let arr = [10, 20, 30, 40, 50]
let sum = arr.reduce((acc, cur, i, ar) => {
  return acc + cur
}) // acc는 누적값, cur은 현재값, i는 인덱스(다른 함수의 i와 같다), ar는 arr전체를 의미한다.
console.log(sum) // 150출력
```

여기서 acc값은 기본적으로 arr\[0]값을 갖는다. 그러므로 cur은 arr\[1]값부터 들어오고 i도 1부터 시작된다. 나는 이게 불편하다고 생각이 된다면 마지막에 ,0 값을 추가하자! 이렇게!

```javascript
//acc를 0부터 하려면??
let arr = [10, 20, 30, 40, 50]
let sum = arr.reduce((acc, cur, i, ar) => {
  return acc + cur
}, 0) //<<여기 이렇게 0을 기입하면 acc값은 0부터 시작이다.
console.log(sum) // 150출력
```

이렇게 되면 cur, i값모두 arr\[0]번부터 시작된다. 결과 값은 같지만 내용이 다르다. 반복문이 도는 횟수도 1회의 차이를 같게 된다.&#x20;

#### 특정값의 갯수 구하기

```javascript
let alps = ["a", "a", "c", "c", "c"];
let modAlps = alps.reduce((acc, cur) => {
 if (acc[cur]) {
    acc[cur] += 1;
  } else {
    acc[cur] = 1; // acc.cur이 없으면 선언함
  }
  return acc;
 }, {}); // acc의 초기값 = 오브젝트로 선언
 console.log(modAlps); // {a: 2, c: 3}
```

해설을 해보자 `modAlps`라는 함수는 5바퀴 돌아간다. 각 항목별로! `acc`의 초기값은 `{}`으로 빈 오브젝트 자료형이다. 그렇다면 첫바퀴가 돌아갈때는 이렇게 될것이다.

```javascript
//loop1
let alps = ["a", "a", "c", "c", "c"];
let modAlps = alps.reduce((acc, cur) => {
 if (acc[cur]) {
    acc[cur] += 1; // acc값에 alps[0])(a)값이 할당되어 있지 않다. {}형태이니 이건 패스
  } else {
    acc[cur] = 1; // acc값에 alps[0])(a) 값이 없으니{a : 1}라는 키-값쌍이 들어갈것이다.
  }
  return acc;
 }, {});
 console.log(modAlps); // {a: 1}
```

이후 2바퀴째!

```javascript
//loop2
let alps = ["a", "a", "c", "c", "c"];
let modAlps = alps.reduce((acc, cur) => {
 if (acc[cur]) {
    acc[cur] += 1; // acc값에 alps[1])(a)값이 할당되어 있다. {a: 1}형태이니 +1해준다
  } else {
    acc[cur] = 1;
  }
  return acc;
 }, {});
 console.log(modAlps); // {a: 2}
```

이런식으로 5바퀴를 돌리면

```javascript
//roop1
console.log(modAlps); // {a: 1}
//roop2
console.log(modAlps); // {a: 2}
//roop3
console.log(modAlps); // {a: 2, c: 1}
//roop4
console.log(modAlps); // {a: 2 c: 2}
//roop5
console.log(modAlps); // {a: 2 c: 3}
```

이렇게 해서 `{a: 2, c: 3}`이라는 오브젝트 값을 얻을 수 있다!

이외에도 다양한 방식으로 reduce()함수를 사용가능하다. 몸에 익히기 위해 최대한 예제를 `reduce()`를 활용하여 풀어보도록하자
