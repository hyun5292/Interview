※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- []()<br/>

<br/>

# Type, Class, and ID selectors

<br/>

> [목표] <b>이 단원에서는 일을 하면서 가장 자주 사용하게 될 가장 간단한 선택자 중 일부를 살펴봅시다.</b>

<br/>

## 유형 선택자

<b style="color: orange;">유형 선택자</b>는 문서에서 HTML 태그/요소를 선택하기 때문에 <b>태그 이름 선택자</b> 또는 <b>요소 선택자</b>라고도 합니다.

```css
span {
  background-color: yellow;
}

strong {
  color: rebeccapurple;
}

em {
  color: rebeccapurple;
}
```

<br/>

## 범용 선택자

<b>범용 선택기는 별표(\*)로 표시됩니다.</b> 문서의 모든 항목을 선택합니다. (또는 다른 요소 및 하위 연결자와 함께 연결된 경우 상위 요소 내부).

```css
* {
  margin: 0;
}
```

### 범용 선택자를 사용하여 선택자를 더 쉽게 읽을 수 있도록 만들기

범용 선택자의 한 가지 용도는 선택자를 더 읽기 쉽게 만들고 수행하는 작업의 측면에서 더 명확하게 만드는 것입니다. 예를 들어, 직계 자식을 포함하여 부모의 첫 번째 자식인 `<article>` 요소의 자손 요소를 선택하고 굵게 표시하려면, `:first-child` 의사 class를 사용할 수 있습니다.

```css
article :first-child {
  font-weight: bold;
}
```

그러나, 이 선택자는 다른 요소의 첫 번째 자식인 `<article>` 요소를 선택하는 `article:first-child`와 혼동될 수 있습니다.

이러한 혼란을 피하기 위해 `:first-chlid` 의사 class에 범용 선택자를 추가할 수 있으므로 선택자가 수행하는 작업이 더 명확해집니다. `<article>` 요소의 첫 번쨰 자식인 어떤 요소 또는 `<article>`의 모든 하위 요소의 첫 번째 자식인 어떤 요소를 선택합니다.

```css
article *:first-child {
  font-weight: bold;
}
```

<br/>

## Class 선택자

<b>class 선택자는 점(.) 문자로 시작합니다.</b> 해당 class가 적용된 문서의 모든 항목이 선택됩니다.

```css
.highlight {
  background-color: yellow;
}
```

### 특정 요소에 대한 Targeting Class

class가 적용된 특정 요소를 대상으로 하는 선택자를 만들 수 있습니다.

```css
span.highlight {
  background-color: yellow;
}

h1.highlight {
  background-color: yellow;
}
```

### 하나 이상의 Class가 적용된 경우 요소를 대상으로 지정

요소에 여러 class를 적용하고 개별적으로 대상을 지정하거나 선택자의 모든 class가 있는 경우에만 요소를 선택할 수 있습니다. 이는 site에서 다양한 방식으로 결합할 수 있는 component를 구축할 떄 유용할 수 있습니다.

```css
.notebox {
  border: 4px solid #666;
  padding: 0.5em;
}

.notebox.warning {
  border-color: orange;
  font-weight: bold;
}

.notebox.danger {
  border-color: red;
  font-weight: bold;
}
```

<br/>

## ID 선택자

<b>id 선택자는 점 문자가 아닌 #으로 시작</b>하지만, class 선택자와 동일한 방식으로 사용됩니다. 그러나 id는 page 당 한 번만 사용할 수 있으며, 요소에는 하나의 id 값만 적용할 수 있습니다. id가 설정된 요소를 선택할 수 있으며, 요소와 id가 일치하는 경우에만 요소를 대상으로 하는 유형 선택자를 id 앞에 둘 수 있습니다.

```css
#one {
  background-color: yellow;
}

h1#heading {
  color: rebeccapurple;
}
```
