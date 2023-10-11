※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [HTMl에 CSS 적용하기](#html에-css-적용하기)<br/>
  - [외부 스타일 시트](#외부-스타일-시트)<br/>
  - [내부 스타일 시트](#내부-스타일-시트)<br/>
  - [인라인 스타일](#인라인-스타일)<br/>
- [선택자(Selectors)](#선택자selectors)<br/>
  - [우선 순위(Specificity)](#우선-순위specificity)<br/>
- [속성 및 값](#속성-및-값)<br/>
  - [함수(Function)](#함수function)<br/>
- [@rules](#rules)<br/>
- [속기(Shorthands)](#속기shorthands)<br/>
- [주석(Comments)](#주석comments)<br/>
- [공백(Whitespace)](#공백whitespace)<br/>

<br/>

# CSS의 구조

<br/>

> [목표] 언어 자체의 구조를 조금 더 깊이 살펴볼 차례입니다. 이미 여기에서 논의된 많은 개념들을 만났습니다. 나중에 혼란스러워하는 개념을 발견하면, 이 개념으로 돌아와서 요약할 수 있습니다.

<br/>

## HTML에 CSS 적용하기

가장 먼저 살펴볼 것은 CSS의 문서에 적용하는 세 가지 방법입니다.

### 외부 스타일 시트

CSS를 여러 page에 연결할 수 있으므로, CSS를 문서에 첨부하는 가장 일반적이고 유용한 방법이며, 모두 동일한 스타일 시트로 CSS 스타일을 지정할 수 있습니다. 대부분의 경우 site의 다른 page는 모두 거의 동일하게 보이기 때문에 기본 모양과 느낌에 동일한 규칙을 사용할 수 있습니다.

외부 스타일 시트는 CSS 확장자가 .css인 별도의 파일로 작성되고, HTML `<link>` 요소에서 참조하는 경우입니다.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>나의 CSS 실험</title>
    <link rel="stylesheet" href="styles.css" />
  </head>
  <body>
    <h1>헬로우 월드!</h1>
    <p>이것은 나의 첫 번째 CSS 예제입니다</p>
  </body>
</html>
```

```css
h1 {
  color: blue;
  background-color: yellow;
  border: 1px solid black;
}

p {
  color: red;
}
```

<br/>

## 내부 스타일 시트

내부 스타일 시트는 외부 CSS 파일이 없는 대신, HTML `<head>` 안에 포함된 `<style>` 요소 내부에 CSS를 배치합니다.

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>나의 CSS 실험</title>
    <style>
      h1 {
        color: blue;
        background-color: yellow;
        border: 1px solid black;
      }

      p {
        color: red;
      }
    </style>
  </head>
  <body>
    <h1>헬로우 월드!</h1>
    <p>이것은 나의 첫 번째 CSS 예제입니다</p>
  </body>
</html>
```

이는 일부 상황(CSS 파일을 직접 수정할 수 없는 content 관리 시스템을 사용하는 경우도 있지만)에서 유용할 수 있지만, CSS가 필요한 외부 스타일 시트만큼 효율적이지 않습니다 - website에서, CSS가 모든 page에서 반복되고 변경이 필요한 경우 여러 위치에서 update 됩니다.

<br/>

## 인라인 스타일

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
  </head>
  <body>
    <h1 style="color: blue; background-color: yellow; border: 1px solid black;">
      헬로우 월드!
    </h1>
    <p style="color: red;">이것은 나의 첫 번째 CSS 예제입니다</p>
  </body>
</html>
```

정말로 필요하지 않는 한, 사용하지 마세요! 유지 관리가 실제로 좋지 않으며(문서 당 동일한 정보를 여러 번 update 해야 할 수도 있음), 프레젠테이션 CSS 정보와 HTML 구조 정보를 혼합하여 코드를 읽고 이해하기 어렵게 만듭니다.

인라인 스타일이 더 일반적이거나 권장되는 곳이 몇 군데 있습니다. 작업 환경이 실제로 제한적인 경우(CMS로 HTML 본문만 편집할 수 있음), 이를 사용하는 것이 좋습니다. 또한 가능한 많은 전자 메일 client와 호환되도록 HTML 전자 메일에 많이 사용된 것을 볼 수 있습니다.

<br/>

## 선택자(Selectors)

선택자는 스타일을 적용하기 위해 HTML 문서에서 무언가를 대상으로 하는 방법입니다. 스타일이 적용되지 않으면 선택자가 일치해야 하는 것과 동일하지 않을 수 있습니다.

각 CSS 규칙은 선택자 또는 선택자 목록으로 시작하여 규칙을 적용해야 하는 요소 또는 요소 규칙을 browser에게 알려줍니다. 다음은 모두 유효한 선택자 또는 선택자 목록의 예입니다.

```css
h1
a:link
.maythings
*
.box p
.box p:first-child
h1, h2, .intro
```

### 우선 순위(Specificity)

두 선택자가 동일한 HTML 요소를 선택할 수 있는 경우가 종종 있습니다.

```css
.special {
  color: red;
}

p {
  color: blue;
}
```

```html
<p class="special">나는 무슨 색입니까?</p>
```

CSS 언어에는 충돌 시 어떤 규칙이 이기는지 제어하는 규칙이 있습니다 - 이러한 규칙을 <b style="color: orange;">계단식(Cascade)</b> 및 <b style="color: orange;">우선 순위(Specificity)</b>라고 합니다.

<br/>

## 속성 및 값

- <b style="color: orange;">속성(Properties)</b> <br/>
  : 변경할 스타일 기능을 나타내는 식별자입니다.
- <b style="color: orange;">값(Values)</b> <br/>
  : 지정된 각 속성에는 값이 지정되어 있으며, 이는 해당 스타일 기능을 변경하는 방법을 나타냅니다.

값과 쌍을 이루는 속성을 <b style="color: orange;">CSS 선언(Declaration)</b>이라고 합니다. CSS 선언은 <b>CSS 선언 블록</b> 안에 있습니다.

CSS 속성을 특정 값으로 설정하는 것은 CSS 언어의 핵심 기능입니다. CSS 엔진은 page의 모든 단일 요소에 적용할 선언을 계산하여 적절하게 배치하고 스타일을 지정합니다. 기억해야 할 것은 CSS에서 속성과 값이 모두 대소문자를 구분한다는 것입니다. 각 쌍의 속성과 값은 콜론(;)으로 구분됩니다.

> [중요] 속성을 알 수 없거나 지정된 속성에 대해 값이 유효하지 않은 경우, 선언이 유효하지 않은 것으로 간주되어 browser의 CSS 엔진에서 완전히 무시됩니다.

> [중요] CSS에서 언어의 불확실성이 발생하는 경우, 미국 맞춤법이 표준으로 합의되었습니다. 예를 들어 color는 항상 color여야 합니다. colour는 작동하지 않습니다.

### 함수(Function)

대부분의 값은 비교적 간단한 keyword 또는 숫자 값이지만, 함수의 형태를 취하는 몇 가지 가능한 값이 있습니다. calc() 함수를 예로 들 수 있습니다.

```html
<div class="outer"><div class="box">The inner box is 90% - 30px.</div></div>
```

```css
.outer {
  border: 5px solid black;
}

.box {
  padding: 10px;
  width: calc(90% - 30px);
  background-color: rebccapurple;
  color: white;
}
```

## @rules

CSS에 행동 방법에 대한 지침을 제공하는 특수 규칙입니다. 일부 <b style="color: #F2B705;">@rules</b>는 규칙 이름과 값으로 단순합니다. 예를 들어, 추가 스타일 시트를 기본 CSS 스타일 시트로 가져오려면 <b style="color: #F2B705;">@import</b>를 사용할 수 있습니다.

```html
@import "styles2.css";
```

접하게 될 가장 일반적인 <b style="color: #F2B705;">@rules</b> 중 하나는 <b style="color: #F2B705;">@media</b>입니다. 이는 특정 조건이 참일 때만 CSS를 적용할 수 있는 미디어 쿼리를 사용할 수 있습니다.

```css
body {
  background-color: pink;
}

@media (min-width: 30em) {
  body {
    background-color: blue;
  }
}
```

<br/>

## 속기(Shorthands)

<b style="color: #F2B705;">font</b>, <b style="color: #F2B705;">background</b>, <b style="color: #F2B705;">padding</b>, <b style="color: #F2B705;">border</b> 및 <b style="color: #F2B705;">margin</b> 등의 일부 속성은 <b style="color: orange;">속기 속성</b>이라고 불립니다 - 이는 여러 줄의 속성 값을 한 줄로 설정하여 시간을 절약하고 작업에서 코드를 깔끔하게 만들 수 있기 때문입니다.

```css
padding: 10px 15px 15px 5px;

padding-top: 10px;
padding-right: 15px;
padding-bottom: 15px;
padding-left: 5px;
```

<br/>

## 주석(Comments)

```css
/* CSS 주석 다는 법 */
/* 코드 편집기에서 주석을 검색할 수 있습니다. */
```

<br/>

## 공백(Whitespace)

HTML과 같은 방식으로 browser는 CSS 내부의 많은 공백을 무시하는 경향이 있습니다. 가독성을 돕기 위해 많은 공백이 있습니다.
