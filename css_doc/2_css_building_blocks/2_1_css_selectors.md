※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [선택자란 무엇인가요?](#선택자란-무엇인가요)<br/>
- [선택자 목록](#선택자-목록)<br/>
- [선택자의 유형](#선택자의-유형)<br/>
  - [유형, Class 및 ID 선택자](#유형-class-및-id-선택자)<br/>
  - [속성 선택자](#속성-선택자)<br/>
  - [의사 Class 및 의사 요소](#의사-class-및-의사-요소)<br/>
  - [결합자](#결합자)<br/>

<br/>

# CSS 선택자

<br/>

> [목표] CSS에서 선택자는 스타일을 지정할 webpage의 HTML 요소를 대상으로 하는 데 사용됩니다. 사용 가능한 다양한 CSS 선택자가 있으며, 스타일을 지정할 요소를 선택할 때 세밀한 정밀도를 허용합니다. <b>이 글에서는 다양한 유형을 자세히 살펴보고 작동 방식을 살펴보겠습니다.</b>

<br/>

## 선택자란 무엇인가요?

<b style="color: orange;">CSS 선택자</b>는 CSS 규칙의 첫 번째 부분입니다. 선택자는 규칙 내부의 CSS 속성 값을 적용하기 위해 어떤 HTML 요소를 선택해야 하는지 browser에 알려주는 요소 및 기타 용어의 패턴입니다. 선택자에 의해 선택되는 요소를 <b style="color: orange;">선택자의 대상</b>이라고 합니다.

<img src="https://developer.mozilla.org/en-US/docs/Learn/CSS/Building_blocks/Selectors/selector.png" />

<br/>

## 선택자 목록

동일한 CSS를 사용하는 항목이 두 개 이상 있는 경우 개별 선택자를 선택자 목록으로 결합하여 규칙이 모든 개별 선택자에 적용되도록 할 수 있습니다.

```css
h1 {
  color: blue;
}

.special {
  color: blue;
}
```

```css
h1,
.special {
  color: blue;
}
```

선택자를 그룹화할 때 선택자 중 구문적으로 유효하지 않은 선택자가 있으면 전체 규칙이 무시됩니다.

```css
/* h1은 적용, ..special은 적용X */
h1 {
  color: blue;
}

..special {
  color: blue;
}
```

<br/>

## 선택자의 유형

선택자에는 몇 가지 다른 그룹이 있으며, 어떤 유형의 선택자가 필요한지 알면 작업에 적합한 도구를 찾는 데 도움이 됩니다.

### 유형, Class 및 ID 선택자

```css
h1 {
}

/* Class */
.box {
}

/* ID */
#unique {
}
```

### 속성 선택자

```css
a[title] {
}

a[href="https://example.com"]
{
}
```

### 의사 Class 및 의사 요소

```css
a:hover {
}

p::first-line {
}
```

### 결합자

최종 선택자 그룹은 문서 내의 요소를 대상으로 하기 위해 다른 선택자를 결합합니다.

```css
article > p {
}
```
