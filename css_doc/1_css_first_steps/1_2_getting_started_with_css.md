※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [HTML로 시작합니다](#html로-시작합니다)<br/>
- [문서에 CSS 추가하기](#문서에-css-추가하기)<br/>
- [HTML 요소 Styling](#html-요소-styling)<br/>
- [요소의 기본 동작 변경하기](#요소의-기본-동작-변경하기)<br/>
- [Class 추가하기](#class-추가하기)<br/>
- [문서에서의 위치에 따라 스타일 지정하기](#문서에서의-위치에-따라-스타일-지정하기)<br/>
- [상태에 따른 Styling](#상태에-따른-styling)

<br/>

# CSS 시작하기

<br/>

> [목표] <b>이 글에서는 간단한 HTML 문서를 가져와서 CSS를 적용하여 언어에 대한 실질적은 내용을 학습합니다.</b>

<br/>

## HTML로 시작합니다

아래 코드를 컴퓨터의 폴더에 <span style="color: black; background: #E7F3F8;">index.html</span>로 저장하십시오.

```html
<!DOCTYPE >
<html lang="ko-KR">
  <head>
    <meta charset="utf-8" />
    <title>CSS로 시작하기</title>
  </head>
  <body>
    <h1>레벨 1 제목입니다.</h1>

    <p>
      이것은 단락입니다. 본문에는 <span>span 요소</span>와
      <a href="http://example.com">링크</a>가 있습니다.
    </p>

    <p>이것은 두 번째 단락입니다. <em>강조된</em> 요소를 포함합니다.</p>

    <ul>
      <li>항목 하나</li>
      <li>항목 둘</li>
      <li>항목 셋</li>
    </ul>
  </body>
</html>
```

<br/>

## 문서에 CSS 추가하기

가장 먼저 해야 할 일은 HTML 문서에 사용하려는 CSS 규칙이 있다는 것을 알리는 것입니다.

HTML 문서와 같은 폴더에 파일을 만들고 <span style="color: black; background: #E7F3F8;">style.css</span>로 저장하세요.

<span style="color: black; background: #E7F3F8;">styles.css</span> 파일을 <span style="color: black; background: #E7F3F8;">index.html</span>에 링크하려면, HTML 문서의 `<head>` 안에 다음 행을 추가하세요.

```html
<link rel="stylesheet" href="styles.css" />
```

<br/>

## HTML 요소 Styling

이 작업은 요소 선택자(HTML 요소 이름과 직접 일치하는 선택자)를 대상으로 수행합니다.

```css
p {
  color: green;
}
```

선택자를 쉼표로 구분하여 여러 선택자를 한 번에 대상으로 지정할 수 있습니다.

```css
p,
li {
  color: green;
}
```

<br/>

## 요소의 기본 동작 변경하기

browser에서 기본 스타일을 포함하는 내부 스타일 시트가 있기 때문에 기본적으로 모든 page에 적용됩니다.

그러나, 종종 browser에서 선택한 것 이외의 것을 원할 것입니다. 변경하려는 HTML 요소를 선택하고 CSS 규칙을 사용하여 모양을 변경하면 됩니다.

<br/>

## Class 추가하기

다른 요소를 변경하지 않고 요소의 하위 부분을 선택할 수 있는 방법을 찾아야 합니다.
이를 수행하는 가장 일반적인 방법은 HTML 요소에 <b style="color: #F2B705;">class</b>를 추가하고 해당 <b style="color: #F2B705;">class</b>를 대상으로 하는 것입니다.

```html
<ul>
  <li>항목 하나</li>
  <li class="special">항목 둘</li>
  <li>항목 셋</li>
</ul>
```

CSS에서 마침표 문자로 시작하는 선택자를 작성하여 <b style="color: #F2B705;">special class</b>를 대상으로 할 수 있습니다.

```css
.special {
  color: orange;
  font-weight: bold;
}
```

때로는 HTML 요소 선택자 및 class 목록이 포함된 규칙이 표시됩니다.

```css
li.special {
  color: orange;
  font-weight: bold;
}
```

<br/>

## 문서에서의 위치에 따라 스타일 지정하기

이 문서에는 두 개의 `<em>` 요소가 있습니다. 하나는 단락 안에 있고 다른 하나는 목록 항목 안에 있습니다. `<li>` 요소 안에 중첩된 `<em>`만 선택하려면 <b style="color: orange;">descendant combinator</b>라는 선택자를 사용할 수 있습니다. 이 선택자는 단순히 두 개의 다른 선택자 사이에 공백의 형태를 취합니다.

```css
li em {
  color: rebeccapurple;
}
```

이 선택자는 `<li>`의 하위 요소인 `<em>` 요소를 선택합니다.

HTML의 동일한 계층 구조 수준에서 제목 바로 다음에 오는 단락의 스타일을 지정해 볼 수 있습니다. 선택자 사이에 +(<b style="color: orange;">adjacent sibling combinator</b>)를 배치 하십시오.

```css
h1 + p {
  font-size: 200%;
}
```

<br/>

## 상태에 따른 Styling

```css
a:link {
  color: pink;
}

a:visited {
  color: green;
}

a:hover {
  text-decoration: none;
}
```

<br/>

## 선택자와 결합자를 결합

여러 선택자와 결합자를 함께 결합할 수 있습니다.

```css
/* <aritcle> 내부의 <p> 안에 있는 모든 <span>을 선택합니다. */
article p span {
  ...;
}

/* <h1> 바로 뒤에 오는 <ul> 바로 뒤의 모든 <p>를 선택합니다. */
h1 + ul + p {
  ...;
}
```

여러 유형을 함께 결합할 수도 있습니다.

```css
body h1 + p .special {
  color: yellow;
  background-color: black;
  padding: 5px;
}
```

이것은 `<body>` 안에 있는 `<h1>` 바로 뒤에 오는 `<p>` 안에 있는 <b style="color: #F2B705;">special class</b>를 가진 요소를 styling합니다.
