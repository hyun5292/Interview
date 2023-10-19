# REACT DOCUMENT 정리

※모든 개념은 https://react.dev/에서 참고했습니다.※

[목차]<br/>

- [JSX로 Markup 작성하기](#jsx로-markup-작성하기)<br/>
  - [JSX: JavaScript 속에 markup 넣기](#jsx-javascript-속에-markup-넣기)<br/>
  - [JSX의 규칙](#jsx의-규칙)<br/>
    - [1. 단일 root 요소 반환](#1-단일-root-요소-반환)<br/>
    - [2. tag 닫기](#2-tag-닫기)<br/>
    - [3. camelCase](#3-camelcase)<br/>
- [중괄호 속 JSX의 JavaScript](#중괄호-속-jsx의-javascript)<br/>
  - [따옴표로 문자열 전달하기](#따옴표로-문자열-전달하기)<br/>
  - [중괄호 사용하기](#중괄호-사용하기)<br/>
    - [중괄호를 사용하는 위치](#중괄호를-사용하는-위치)<br/>
  - [중첩 중괄호 사용하기: JSX 내부 CSS와 다른 객체들](#중첩-중괄호-사용하기-jsx-내부-css와-다른-객체들)<br/>

<br/>

## JSX로 Markup 작성하기

<b style="color: orange;">JSX</b>는 <b>HTML과 같은 markup을 JavaScript 파일 안에 작성하기 위한 JavaScript syntax extension</b>입니다.

<br/>

### JSX: JavaScript 속에 markup 넣기

Web은 HTML, CSS, JavaScript로 이루어집니다. 그동안은, 개발자들이 content는 HTML, 디자인은 CSS, logic은 JavaScript로 분류해왔습니다.

하지만 web은 점점 상호작용하고, logic이 content를 결정하게 되었습니다. JavaScript는 HTML을 담당하게 되었습니다. <b>이것이 React가 logic과 markup을 component라는 한 공간 안에서 함께 rendering 하게 된 이유입니다.</b>

<br/>

### JSX의 규칙

#### 1. 단일 root 요소 반환

여러 element들을 반환하려면, 하나의 tag로 감싸주어야 합니다.

```javascript
return (
  <div>
    <h1>This is the Example</h1>
    <img src="https://www.example.com/example.jpg" alt="예시 이미지" />
  </div>
);
```

`<div></div>`로 감싸주는 대신 `<></>`로 감싸줄 수 있습니다. 이를 <b style="color: orange;">Fragment</b>라고 부르는데, <b>browser HTML 트리에 흔적을 남기지 않고 그룹화할 수 있습니다.</b>

> [JSX 태그들을 그룹화 하는 이유]
> JSX는 HTML처럼 보이지만 내부적으로는 일반 JavaScript 객체들로 변환합니다. 함수는 배열로 그룹화 하지 않는 이상 여러 개의 객체들을 반환할 수 없습니다.

#### 2. tag 닫기

JSX는 반드시 닫아야 합니다:`<img />`처럼 혼자 쓰일 수도 있고, `<h1>example</h1>`처럼 태그로 감쌀 수도 있습니다.

#### 3. camelCase

JSX는 JavaScript로 작성되고 JSX로 작성된 모든 속성들은 JavaScript 객체의 key가 됩니다. Component에서, 종종 속성들을 변수로 사용하고 싶을 것입니다. 하지만 JavaScript는 변수명에 제한이 있습니다. 그렇기 때문에, React에서 HTML과 SVG 속성들은 camelCase로 작성되어야 합니다. 예를 들어, class는 예약어이기 때문에 React에서는 해당 DOM 속성의 이름을 따서 className으로 대체됩니다.

<br/>

## 중괄호 속 JSX의 JavaScript

JSX는 logic과 content를 같은 위치에 유지하면서 JavaScript 파일 안에 HTML 같은 markup을 사용할 수 있도록 도와줍니다. 때때로 약간의 JavaScript logic을 추가하거나 markup에 동적 속성을 참조하고 싶을 수도 있습니다. 이 경우 JSX에 중괄호를 사용할 수 있습니다.

<br/>

### 따옴표로 문자열 전달하기

JSX에 문자열 속성을 전달할 경우, 작은 따옴표나 큰 따옴표를 사용할 수 있습니다.
만약 src나 alt를 동적으로 지정하고 싶다면, 따옴표("")를 중괄호로 대체하여 JavaScript의 변수를 사용할 수 있습니다.

```javascript
export default function Example() {
  const addr = "https://www.example.com/example.jpg";
  const desc = "example";
  return <img className="example" src={addr} alt={desc} />;
}
```

<br/>

### 중괄호 사용하기

JSX는 JavaScript를 사용하는 방법 중 하나입니다. 이것은 중괄호를 사용하여 JavaScript를 사용할 수 있도록 해준다는 의미입니다.

모든 JavaScript 표현식은 중괄호 안에서 작동합니다.

```javascript
const today = new Date();

function formData(date) {
  return new Intl.DateTimeFormat("en-US", { weekday: "long" }).format(data);
}

export default function TodoList() {
  return <h1>To Do List for {formatDate(today)}</h1>;
}
```

#### 중괄호를 사용하는 위치

1. <b>text</b>로써 JSX 태그 안에 바로 사용하기
2. <b>속성</b>으로써 사용하기

<br/>

### 중첩 중괄호 사용하기: JSX 내부 CSS와 다른 객체들

문자열, 숫자 및 기타 JavaScript 표현식 외에도 JSX에서 객체를 전달할 수 있습니다. 객체들은 또한 중괄호 안에 게시됩니다. 더욱이 JSX 안에서 JS 객체를 전달하려면 객체를 또 다른 중괄호로 감싸야 합니다.

```javascript
export default function TodoList() {
  return (
    <ul
      style={{
        backgroundColor: "black",
        color: "pink",
      }}
    >
      <li>To do 1</li>
      <li>To do 2</li>
      <li>To do 3</li>
    </ul>
  );
}
```

<br/>

[목차로 이동](#react-document-정리)
