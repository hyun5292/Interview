※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [CSS는 실제로 어떻게 작동합니까?](#css는-실제로-어떻게-작동합니까)<br/>
- [DOM 정보](#dom-정보)<br/>
- [실제 DOM 표현](#실제-dom-표현)<br/>
- [DOM에 CSS 적용하기](#dom에-css-적용하기)<br/>
- [Browser에서 인식하지 못하는 CSS를 발견하면 어떻게 됩니까?](#browser에서-인식하지-못하는-css를-발견하면-어떻게-됩니까)<br/>

<br/>

# CSS 작동 방식

<br/>

> [목표] <b>이 강의에서는 browser가 CSS와 HTML을 가져와서 webpage로 만드는 방법을 살펴보겠습니다.</b>

<br/>

## CSS는 실제로 어떻게 작동합니까?

1. browser는 HTML을 로드합니다.

2. HTML을 DOM으로 변환합니다.

3. 그러면 browser는 HTML 문서에 연결된 임베디드 이미지, 동영상, 링크된 CSS 같은 대부분의 resource들을 가져옵니다.

4. browser는 가져온 CSS를 구문 분석하고 선택자 유형별로 다른 규칙을 다른 버킷으로 정렬합니다. (예; 요소, Class, ID 등 찾은 선택자를 기반으로 DOM의 어느 노드에 어떤 규칙을 적용해야 할지 결정하고, 피리요에 따라 스타일을 첨부합니다.)(이 중간 단게를 <b style="color: orange;">렌더 트리</b>라고 합니다.)

5. 렌더 트리는 규칙이 적용된 후에 표시되어야 하는 구조로 배치됩니다.

6. page의 시각적 표시가 화면에 표시됩니다.(이 단계를 <b style="color: orange;">페인팅</b>이라고 합니다.)

<img src="https://developer.mozilla.org/ko/docs/Learn/CSS/First_steps/How_CSS_works/rendering.svg" />

<br/>

## DOM 정보

DOM은 트리와 같은 구조를 가지고 있습니다. markup 언어의 각 요소, 속성 및 텍스트는 트리 구조에서 DOM node가 됩니다. node는 다른 DOM node와의 관계에 의해 정의됩니다. 일부 요소는 자식 node의 부모이고 자식 node에는 형제가 있습니다.

DOM은 CSS와 문서의 내용이 만나는 곳이기 때문에 DOM을 이해하면 CSS를 설계, debug 및 유지 관리하는 데 도움이 됩니다. browser DevTools로 작업을 시작하면, 적용할 규칙을 보기 위해 항목을 선택할 때 DOM을 탐색하게 됩니다.

<br/>

## 실제 DOM 표현

```html
<p>
  사용해봅시다.
  <span>계단식</span>
  <span>스타일</span>
  <span>시트들</span>
</p>
```

```
p
├─ "사용해봅시다."
├─ SPAN
|  └─ "계단식"
├─ SPAN
|  └─ "스타일"
├─ SPAN
   └─ "시트들"
```

<br/>

## DOM에 CSS 적용하기

```html
<p>
  사용해봅시다.
  <span>계단식</span>
  <span>스타일</span>
  <span>시트들</span>
</p>
```

```css
span {
  border: 1px solid black;
  background-color: lime;
}
```

browser는 HTML을 구문 분석하고 그로부터 DOM을 생성하고, CSS를 구문 분석합니다. CSS에서 사용할 수 있는 유일한 규칙에는 span 선택자가 있으므로, browser는 CSS를 매우 빠르게 정렬할 수 있습니다. 이 규칙을 세 개의 `<span>` 각각에 적용한 다음 최종 시각적 표현을 화면에 표시합니다.

<br/>

## Browser에서 인식하지 못하는 CSS를 발견하면 어떻게 됩니까?

대답은 아무것도 하지 않으며, CSS의 다음 단계로 넘어갑니다. browser가 규칙을 구문 분석하고 이해하지 못하는 속성이나 값을 발견하면, 이를 무시하고 다음 선언으로 넘어갑니다. 오류가 발생하여 속성 또는 값의 철자가 틀렸거나 속성 또는 값이 너무 새롭고 browser가 아직 이를 지원하지 않는 경우, 다음 선언으로 넘어갑니다.
