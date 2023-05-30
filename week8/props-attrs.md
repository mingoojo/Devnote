# 5.props와 attrs

### 학습 키워드

* props
* attrs

## props

CSS in JS는 컴포넌트 단위로 구성된다. 그래서 props를 전달하여 props값을 파라미터로 css의 변화를 줄 수 있다.

#### 공식문서의 예제

```tsx
import styled from 'styled-components';


//파라미터로 전달되는 값의 타입을 지정해주고, 그 값을 제네릭타입으로 잡아준다.
type InputProps = {
  $inputColor?:string;
}

const Input = styled.input<InputProps>`
  padding: 0.5em;
  margin: 0.5em;
  color: ${(props) => (props.$inputColor || '#BF4F74')}; //함수의 형태로 값을 잡아준다.
  background: papayawhip;
  border: none;
  border-radius: 3px;
`;

export default function Test() {
  return (
    <div>
      <Input defaultValue="@probablyup" type="text" />
      <Input defaultValue="@geelen" type="text" $inputColor="rebeccapurple" />
    </div>
  );
}

```

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption></figcaption></figure>

위에 예시는렇게  `$inputColor`를 통해 서로 다른 컬러를 출력한다. 여기에 `onclick`과 같은 이벤트로 추가적인 변화를 줄 수 있다.



```tsx
import styled from 'styled-components';
import { useBoolean } from 'usehooks-ts';

type ParagraphProps={
  active:boolean
}

const Paragraph = styled.p<ParagraphProps>`
  color: ${(props) => (props.active ? '#F00' : '#888')};
  button{
    color: red;
  }
`;

export default function Test() {
  const { value: active, toggle } = useBoolean(false);
  function handleClick() {
    toggle();
  }
  return (
    <div>
      <Paragraph active={active}>
        <button type="button" onClick={handleClick}>test</button>
        testText
      </Paragraph>
    </div>
  );
}

```

`onClick`이벤트로 `useBoolean`을 toggle해주고 그에 따라 `testText`의 컬러가 달라지게 표현할 수 있다.



## attrs

attrs를 사용하면 속성을 나타낼 수 있다. input이나 button의 타입을 반복적으로 잡는 경우 사용하기 좋다.



```tsx
import styled from 'styled-components';

//타입을 기본 속성으로 전달한다.
const Button = styled.button.attrs({
  type: 'button',
})`
  border: 1px solid #888;
  color: ${(props) => (props.color ? props.color : 'blue')};
  cursor: pointer;
`;

export default Button;

```

#### 공식문서의 예제

```tsx
const Input = styled.input.attrs(props => ({
  type: "text",
  $size: props.$size || "1em",
}))<{ $size?: string; }>`
  color: #BF4F74;
  font-size: 1em;
  border: 2px solid #BF4F74;
  border-radius: 3px;

  /* here we use the dynamically computed prop */
  margin: ${props => props.$size};
  padding: ${props => props.$size};
`;

render(
  <div>
    <Input placeholder="A small text input" />
    <br />
    <Input placeholder="A bigger text input" $size="2em" />
  </div>
);
```
