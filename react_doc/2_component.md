# REACT DOCUMENT 정리

※모든 개념은 https://react.dev/에서 참고했습니다.※

[목차]<br/>

- [Components: UI building blocks](#components-ui-building-blocks)<br/>
  - [Component 정의하기](#component-정의하기)<br/>
    - [Step 1: Component Export하기](#step1-component-export-하기)<br/>
    - [Step2: 함수 정의하기](#step2-함수-정의하기)<br/>
    - [Step3: markup 추가하기](#step3-markup-추가하기)<br/>
- [Component Import와 Export 하기](#component-import와-export-하기)<br/>
  - [같은 파일에서 여러 Component들을 Import와 Export하기](#같은-파일에서-여러-component들을-import와-export-하기)<br/>

<br/>

## Components: UI building blocks

React는 markup, CSS 그리고 JavaScript를 재사용 가능한 UI 요소인 사용자 정의 Component로 결합할 수 있게 해줍니다.

<br/>

### Component 정의하기

전통적으로 webpage를 만들 때, 개발자들은 content를 markup하고 JavaScript를 사용해 상호작용을 더했습니다. React는 같은 기술을 사용하면서도 상호작용을 최우선으로 생각합니다: <b style="color: orange;">React Component</b>는 markup을 뿌릴 수 있는 JavaScript 함수입니다.

```javascript
export default function Profile() {
  return <img src="https://www.example.com/example.jpg" alt="예시 이미지" />;
}
```

#### Step1: Component Export 하기

`export default`는 기본적인 JavaScript syntax입니다. 이는 main function을 표시하고 다른 파일에서 import 할 수 있도록 도와줍니다.

#### Step2: 함수 정의하기

Component의 이름은 반드시 대문자로 시작해야합니다.

#### Step3: markup 추가하기

Component는 src와 alt 속성을 가진 `<img />` 태그를 return 합니다. `<img />` 태그는 HTML처럼 작성되었지만 사실 JavaScript입니다. 이 구문은 <b style="color: orange;">JSX</b>라 불리며 <b>markup을 JavaScript로 포함할 수 있게 도와줍니다.</b>

<br/>

## Component Import와 Export 하기

Component는 다른 Component들로 구성되도록 만들 수 있습니다. 하지만 더 많은 Component들이 중첩될 수록 다른 파일들로 분할하는 것이 나을 수도 있습니다. 이는 파일들을 파악하기 쉽고 더 많은 곳에 재사용할 수 있도록 만듭니다.

다음 세 단계로 Component를 다른 파일에서 사용할 수 있습니다.

1. Component를 작성할 새 JS 파일을 만듭니다.
2. 해당 파일에서 Component 함수를 <b>Export</b> 합니다.

```javascript
export default function Example() {}

//또는

function Example() {}

export default Example;
```

3. Component를 사용하고자 하는 파일에 <b>Import</b>합니다.

<br/>

### 같은 파일에서 여러 Component들을 Import와 Export 하기

한 파일에서 여러 Component들을 생성하고 사용할 수 있습니다. <b>한 파일에는 default export를 한 개만 작성할 수 있지만 다양한 이름의 export들은 가질 수 있습니다.</b>

default keyword를 사용하여 export 할 경우

```javascript
export default function ExampleA() {}
```

import 할 때 함수명을 바로 사용하지만

```javascript
import ExampleA from "./Example.js";
```

default keyword 없이 export 할 경우

```javascript
export function ExampleB() {}
```

중괄호를 사용하여 import 합니다.

```javascript
import { ExampleB } from "./Example.js";
```

<br/>

[목차로 이동](#react-document-정리)
