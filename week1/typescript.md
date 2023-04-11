# typescript

### typescript속 REPL사용법

```
// 터미널
npx ts-node
```

터미널 속에서 REPL을 사용가능!



### typescript 문법

#### 타입지정

```
let name:string;
let age:number;
```

위와 같이 선언하면 'name'이라는 변수는 스트링만 입력이 가능하고 , 'age'라는 변수는 숫자만 입력이 가능하다.



```
let human:{
    name:string;
    age:number;
}
```

이렇게 지정해두면 위와 마찬가지로 'name'이라는 변수는 스트링만 입력이 가능하고 'age'라는 변수는 숫자만 입력이 가능하다. 다른 항목(예를 들면 id)와 같은 항목을 입력하면 에러가 난다.



#### type사용

타입은 변수를 지정해주는 ''var'의 위치에 'type'을 입력하여 선언하고, 아래와 같이 작성된다.

```
type Human = {
  name: string;
  age: number;
};

let boy: Human;

boy = { name: '홍길동', age: 13 };
boy
{ name: '홍길동', age: 13 }
```



#### interface 사용

interface또한 요소에 타입을 지정하는 방법으로, 아래와 같은 형식으로 작성된다.

```
interface Person {
  name: string;
  age: number;
};

let girl: Person;

girl = { name: '홍길동', age: 13 };
girl
{ name: '홍길동', age: 13 }
```

이렇게 'girl'이라는 변수를 지정하고 호출하면 '{ name: '홍길동', age: 13 }'과 같은 결과가 호출된다.



#### 함수에서 타입지정하는 방

```
function add(x: number, y: number): number {
  return x + y;
}

add(1, 2)
```

위와 같이 타입을 지정하면 x에 숫자가 들어가고 y에 숫자가 들어가 x+y라는 답변을 number의 형태로 호출한다.



#### 배열에서 타입지정하는 방법

<pre><code><strong>let numbers: number[];
</strong>numbers = [1, 2, 3];

let numbers2: [string, number];
numbers2 = ['hp', 123];
</code></pre>

위에서 'numbers'의 항목은 전부 숫자로 구성되어있고, 'numbers2'는 첫번째항목은 스트링, 두번째 항목을 숫자로 더욱 깐깐하게 배열을 관리할 수 있다.



#### :any

어떠한 형태의 자료가 들어와도 상관없는 느슨한 방식의 타입지정법이다.

```
let numbers:any[]
numbers = [1, 2, 3]
numbers = [1, 2, '3']
```

2가지경우 모두 오류가 발생하지 않는다.



#### 타입추론

```
const name: string = '홍길동';

const name = '홍길동';
```

따로 string이라는 타입을 지정해주지 않아도 아래처럼 'name'을 홍길동이라는 스트링으로 지정하면 'name'은 스트링을 받는 변수라고 추론하게 된다.



#### union type

합집합이라는 뜻처럼 '또는(or)'을 의미하는 | 기호로 사용된다.

```
type bool = true | false;

let flag: bool;

flag = true;

flag = false;
```

'bool'은 true 또는 false라고 지정해주면 'bool'에 속하는 'flag'는 true와 false로 모두 지정 가능하다. 이러한 유니온타입은 매개변수를 제한할때 사용하기 좋다.

```
type Category = 'food' | 'toy' | 'bag';

function fetchProducts({ category }: { category: Category }) {
  console.log(`Fetch ${category}`);
}
```

```
let target: string | number;

target = '홍길동';

target = 13;

target = null;

target = undefined;


let targetName: string | undefined;

targetName = '홍길동';

targetName = undefined;
```

위에서 'target'에 null과 undefined는 에러가 발생한다. 'targetName'변수와 같이 선언을하면 '홍길동', 'undefined' 모두 오류가 발생하지 않지만 'undefined'는 직접적으로 사용이 되는 경우는 크게 없고, 매개변수에서 사용된다. 그러나 물음표 기호를 사용하여 Optional Parameter로 처리하는 방식도 있다.

```
function greeting(name?: string): string {
  return `Hello, ${name || 'world'}`;
}
```

이렇게 선언을 해주면, name이 입력되면 'Hello ${name}'이 출력되고 입력되지 않으면(즉 undefined이면) 'Hello World'가 출력된다. 아래처럼 기본값을 잡아 줄 수도 있다.

```
function greeting2(name: string = 'world'): string {
  return `Hello, ${name}`;
}
```

greeting과 greeting2에 같은 파라미터를 입력하면 같은 값이 나온다.



#### 오브젝트에서의 활용

```
type Human = {
  name: string;
  age?: number;
};

function greeting({ name, age }: Human): string {
  return age ? `${name} (${age})` : name;
}

greeting()

greeting({ name: '홍길동' })

greeting({ name: '홍길동', age: 13 })
```



#### Intersection Type

타입을 확장하는 가장 간단한 방법!

```
type Human = {
  name: string;
  age: number;
};

type Creature = {
  hp: number;
  mp: number;
};

type Person = Human & Creature;

let person: Person;

person = { name: '홍길동', age: 13, hp: 256, mp: 16 };
```

위와 같이 person은 'Human'이기도 하며 'Creature'이기도 하다. 그러므로 'name', 'age', 'hp', 'mp'의 모든 항목을 입력하여야 오류없이 출력이 되고, 그렇기에 변수에 추가적인 항목을 입력하는데 좋다. 그 말은 , 타입을 확장하는 방법이라는 뜻이다.



Typescript는 실시간 오류검사를 위해 사용하는 언어로, 프로젝트가 커지면서 오류의 발생부분을 찾는게 힘들어 질때 가장 효율적이고, functional하게 작동될 수 있다!
