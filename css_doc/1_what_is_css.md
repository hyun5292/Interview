※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [CSS란 무엇입니까?](#css란-무엇입니까)<br/>
- [CSS 구문](#css-구문)<br/>
- [CSS Modules](#css-modules)<br/>
  - [CSS Specifications](#css-specifications)<br/>
- [Browser 지원](#browser-지원)<br/>

# CSS란 무엇인가?

<br/>

> [목표] CSS(Cascading Style Sheets)를 사용하면 멋진 webpage를 만들 수 있지만, 어떻게 작동할까요? <b>이 글에서는 CSS가 무엇인지 설명하고 CSS에 대한 몇 가지 주요 용어를 다룹니다.</b>

<br/>

## CSS란 무엇입니까?

<b style="color: orange;">CSS</b>는 사용자에게 문서를 표시하는 방법을 지정하는 언어입니다 - 스타일, 레이아웃 등.

문서는 일반적으로 markup 언어를 사용하여 구성된 텍스트 파일입니다 - HTML이 가장 일반적인 markup 언어이지만, SVG 또는 XML과 같은 다른 markup 언어를 사용할 수도 있습니다.

CSS는 매우 기본적인 텍스트 문서 styling에 사용될 수 있습니다.

<br/>

## CSS 구문

CSS는 규칙 기반 언어입니다 - webpage의 특정 요소 또는 요소 그룹에 적용할 스타일 그룹을 지정하는 규칙을 정의합니다.

```css
h1 {
  color: red;
  font-size: 5em;
}
```

- CSS 규칙은 선택자와 함께 열립니다. 스타일을 지정할 HTML 요소를 선택합니다.

- 그런 다음 중괄호가 있습니다.

- 중괄호 안에는 <b>속성</b>과 <b>값</b> 쌍의 형태를 취하는 하나 이상의 선언이 있습니다. 콜론 앞에 속성을 명시합니다. 그리고 콜론 뒤에 속성의 값을 명시합니다.

- 각각의 쌍은 우리가 선택하려는 요소의 속성을 명시합니다. 그리고 해당 속성에 부여할 값을 지정합니다.

CSS 속성은 지정되는 속성에 따라 허용되는 값이 다릅니다.

CSS 스타일 시트에는 차례로 작성된 여러 규칙이 포함됩니다.

<br/>

## CSS Modules

CSS를 사용하여 스타일을 지정할 수 있는 것이 너무 많으므로, 언어는 module로 분류됩니다.

### CSS Specifications

모든 web 표준 기술은 표준 조직이 게시한 명세서라는 거대한 문서로 정의됩니다. 그리고 해당 기술들이 어떻게 작동하는지 정확하게 정의합니다.

CSS는 다르지 않습니다 - W3C 내에서 CSS Working Group이라는 곳에서 개발했습니다.

<br/>

## Browser 지원

CSS가 지정되면 하나 이상의 browser가 이를 구현한 경우에만 webpage를 개발하는데 유용합니다. 이것은 CSS 파일의 명령을 화면에 출력할 수 있는 것으로 바꾸도록 코드가 작성되었음을 의미합니다. 모든 browser가 동시에 기능을 구현하는 것은 드문 일이므로 일반적으로 일부 browser에서는 CSS의 일부를 사용할 수 있고, 다른 browser에서는 사용할 수 없는 경우가 있습니다. 이러한 이유로, 구현 상태를 확인할 수 있는 것이 유용합니다.

browser 지원 상태는 모든 MDN CSS 속성 page에 <b style="color: orange;">browser 호환성</b>이라는 이름을 가진 표에 표시됩니다.
