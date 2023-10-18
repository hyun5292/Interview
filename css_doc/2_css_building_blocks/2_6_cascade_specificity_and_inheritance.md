※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [규칙 충돌](#규칙-출동)<br/>
  - [계단식(cascade)](#계단식cascade)<br/>
  - [우선 순위(specificity)](#우선-순위specificity)<br/>
  - [속성(Inheritance)](#속성inheritance)<br/>
- [상속 이해하기](#상속-이해하기)<br/>
  - [상속 제어하기](#상속-제어하기)<br/>
  - [모든 속성 값 재설정](#모든-속성-값-재설정)<br/>
- [계단식 이해하기](#계단식-이해하기)<br/>
  - [계단식 이해하기 - 소스 순서](#계단식-이해하기---소스-순서)<br/>
  - [우선 순위(specificity)](#계단식-이해하기---우선-순위specificity)<br/>
  - [!important](#important)<br/>
- [CSS 위치의 영향](#css-위치의-영향)<br/>
- [요약하자면](#요약하자면)<br/>

<br/>

# 계단식 및 상속

<br/>

> [목표] <b>이 수업의 목적은 CSS가 HTML에 적용되는 방법과 충돌을 해결하는 방법을 제어하는 CSS의 가장 기본적인 개념에 대한 이해를 발전시키는 것입니다.</b>

<br/>

## 규칙 출동

어느 시점에서, project를 진행하다 보면 요소에 적용해야 할 CSS가 작동하지 않는다는 것을 알게 될 것입니다. 일반적으로 문제는 동일한 요소에 적용할 수 있는 두 가지 규칙을 작성했다는 것입니다. <b style="color: orange;">계단식(cascade)</b>과 밀접하게 관련된 <b style="color: orange;">우선 순위(specificity)</b> 개념은 그러한 충돌이 있을 때 적용되는 규칙을 제어하는 메커니즘입니다. 어떤 규칙에 따라 요소를 원하는 스타일로 만들지 못할 수도 있으므로 이러한 메커니즘의 작동 방식을 이해해야 합니다.

<b style="color: orange;">상속(inheritance)</b> 개념도 중요합니다. 기본적으로 일부 CSS 속성은 현재 요소의 부모 요소에 설정된 값을 상속하지만, 일부는 그렇지 않습니다. 또한 예상치 못한 일부 동작이 발생할 수 있습니다.

<br/>

### 계단식(Cascade)

stylesheet cascade - 매우 간단한 수준에서 이는 CSS 규칙의 순서가 중요하다는 것을 의미합니다. 동일한 우선 순위를 갖는 두 칙이 적용될 때, CSS에서 마지막에 나오는 규칙이 사용될 것입니다.

<br/>

### 우선 순위(Specificity)

우선 선위는 여러 규칙에 따른 선택자가 있지만, 여전히 동일한 요소에 적용될 수 있는 경우, browser가 어떤 규칙을 적용할 지 결정하는 방법입니다. 기본적으로 선택자의 선택이 얼마나 구체적인지 측정합니다.

- 요소 선택자는 덜 구체적입니다<br/>
  -> page에 나타나는 해당 유형의 모든 요소를 선택하므로 점수가 낮아집니다.
- class 선택자는 보다 구체적입니다.<br/>
  -> 특정 class 속성 값이 있는 page의 요소만 선택하므로 점수가 높아집니다.

<br/>

### 속성(Inheritance)

부모 요소에서 설정된 일부 CSS 속성 값은 자식 요소에 의해 상속되며, 일부는 그렇지 않습니다.

<br/>

## 상속 이해하기

```css
.main {
  color: rebeccapurple;
  border: 2px solid #ccc;
  padding: 1em;
}

.special {
  color: black;
  font-weight: bold;
}
```

```html
<ul class="main">
  <li>Item One</li>
  <li>
    Item Two
    <ul>
      <li>2.1</li>
      <li>2.2</li>
    </ul>
  </li>
  <li>
    Item Three
    <ul class="special">
      <li>
        3.1
        <ul>
          <li>3.1.1</li>
          <li>3.1.2</li>
        </ul>
      </li>
      <li>3.2</li>
    </ul>
  </li>
</ul>
```

<br/>

### 상속 제어하기

CSS는 상속을 제어하기 위한 4가지 특수 범용 속성 값을 제공합니다.

- <b style="color: #F2B705;">inherit</b><br/>
  : 선택한 요소에 적용된 속성 값을 부모 요소의 속성 값과 동일하게 설정합니다.

- <b style="color: #F2B705;">initial</b><br/>
  : 선택한 요소에 적용된 속성 값을 browser의 기본 stylesheet에서 해당 요소의 해당 속성에 설정된 값과 동일하게 설정합니다. browser의 기본 stylesheet에서 값을 설정하지 않고 속성이 자연스럽게 속성되면 속성 값이 대신 inherit 되도록 설정합니다.
- <b style="color: #F2B705;">unset</b><br/>
  : 속성을 natural 값으로 재설정됩니다. 즉, 속성이 자연적으로 상속되면 inherit 된 것처럼 작동하고 그렇지 않으면 initial처럼 작동합니다.

> [참고] browser 지원이 제한된 새로운 값인 revert도 있습니다.

```css
body {
  color: green;
}

.my-class-1 a {
  color: inherit;
}

.my-class-2 a {
  color: initial;
}

.my-class-3 a {
  color: unset;
}
```

```html
<ul>
  <li>Default <a href="#">link</a> color</li>
  <li class="my-class-1">Inherit the <a href="#">link</a> color</li>
  <li class="my-class-2">Reset the <a href="#">link</a> color</li>
  <li class="my-class-3">Unset the <a href="#">link</a> color</li>
</ul>
```

<br/>

### 모든 속성 값 재설정

CSS 속기 속성을 <b style="color: #F2B705;">all</b>로 사용하면 이러한 상속 값 중 하나를 거의 모든 속성에 한 번에 적용할 수 있습니다. 이 값은 상속 값 중 하나 일 수 있습니다. 스타일에 대한 변경 사항을 취소하여 새로운 변경을 시작하기 전에 알려진 시각 지점으로 돌아갈 수 있는 편리한 방법입니다.

```css
blockquote {
  background-color: orange;
  border: 2px solid blue;
}

.fix-this {
  all: unset;
}
```

```html
<blockquote>
  <p>This blockquote is styled</p>
</blockquote>

<blockquote class="fix-this">
  <p>This blockquote is not styled</p>
</blockquote>
```

<br/>

## 계단식 이해하기

이제 HTML 구조에 깊게 중첩된 단락이 본문에 적용된 CSS와 동일한 색상인 이유를 이해하고, 소개 수업에서 문서의 어느 시점에서 CSS를 변경하는 방법에 대해 이해합니다 - 요소에 CSS를 할당하거나 class를 만들지 여부, 이제 여러 요소가 요소를 styling 할 수 있는 경우, CSS에서 적용할 CSS 규칙을 어떻게 정의하는지 올바르게 살펴보겠습니다.

여기에는 중요도의 내림차순으로 나열된 세 가지 요소가 있습니다.

1. Importance
2. 우선 순위
3. 소스 순서

<br/>

### 계단식 이해하기 - 소스 순서

정확히 동일한 가중치를 갖는 규칙이 두 개 이상인 경우, CSS에서 마지막에 오는 규칙이 우선합니다. 이것을 요소 자체가 마지막 요소가 승리하고 요소를 styling 할 때까지 초기 요소를 덮어 쓰는 규칙에 가깝다고 생각할 수 있습니다.

<br/>

### 계단식 이해하기 - 우선 순위(Specificity)

규칙이 stylesheet에서 나중에 나오지만 이전의 충돌하는 규칙이 적용되는 상황이 발생합니다. 이는 이전 규칙이 더 높은 우선 순위를 갖기 때문입니다 - 보다 구체적이기 때문에, browser에서 요소를 스타일해야 하는 규칙으로 선택하고 있습니다.

여기서 주목할 점은 선택자 및 선택한 항목에 적용되는 규칙에 대해 생각하고 있지만, 덮어쓰는 전체 규칙이 아니라 동일한 속성일 뿐입니다.

이 동작은 CSS에서 반복을 피하는 데 도움이 됩니다. 일반적인 방법은 기본 요소의 일반 스타일을 정의한 다음, 다른 요소에 대한 class를 작성하는 것입니다.

이제 browser가 우선 순위를 계산하는 방법을 살펴보겠습니다. 기본적으로 포인트 단위의 가치가 다른 유형의 선택자에 부여되며, 이를 합산하면 특정 선택자의 가중치가 부여되며, 이는 다른 잠재적 일치 항목에 대해 평가할 수 있습니다.

1. Thousands<br/>
   : 선언이 Inline 스타일인 <b style="color: #F2B705;">style</b> 속성 안에 있으면, 열에서 1점을 얻습니다. 이러한 선언에는 선택자가 없으므로 그 우선 순위는 항상 1000입니다.
2. Hundreds<br/>
   : 전체 선택자에 포함된 각 ID 선택자에 대해 이 열에서 1점을 얻습니다.
3. Tens<br/>
   : 이 선택란에서 전체 선택자 내에 포함된 각 class 선택자, 속성 선택자 또는 pseudo-class(의사 class)에 대해 이 열에서 1점을 얻습니다.
4. Ones<br/>
   : 이 항목에서 각 요소 선택자 또는 전체 선택자 내에 포함된 pseudo-element(의사 요소)에 대해 1점을 얻습니다.

> [참고] 범용 선택자(\*), 결합자(+, >, ~, ") 및 부정 pseudo-class(:not)의 우선 순위에 영향을 미치지 않습니다.

```css
/* 1. specificity: 1-0-1 */
#outer a {
  background-color: red;
}

/* 2. specificity: 2-0-1 */
#outer #inner a {
  background-color: blue;
}

/* 3. specificity: 1-0-4 */
#outer div ul li a {
  color: yellow;
}

/* 4. specificity: 1-1-3 */
#outer div ul .nav a {
  color: white;
}

/* 5. specificity: 0-2-4 */
div div li:nth-child(2) a:hover {
  border: 10px solid black;
}

/* 6. specificity: 0-2-3 */
div li:nth-child(2) a:hover {
  border: 10px dashed black;
}

/* 7. specificity: 0-3-3 */
div div .nav:nth-child(2) a:hover {
  border: 10px double black;
}

a {
  display: inline-block;
  line-height: 40px;
  font-size: 20px;
  text-decoration: none;
  text-align: center;
  width: 200px;
  margin-bottom: 10px;
}

ul {
  padding: 0;
}

li {
  list-style-type: none;
}
```

```html
/* 1. specificity: 1-0-1 */ #outer a { background-color: red; } /* 2.
specificity: 2-0-1 */ #outer #inner a { background-color: blue; } /* 3.
specificity: 1-0-4 */ #outer div ul li a { color: yellow; } /* 4. specificity:
1-1-3 */ #outer div ul .nav a { color: white; } /* 5. specificity: 0-2-4 */ div
div li:nth-child(2) a:hover { border: 10px solid black; } /* 6. specificity:
0-2-3 */ div li:nth-child(2) a:hover { border: 10px dashed black; } /* 7.
specificity: 0-3-3 */ div div .nav:nth-child(2) a:hover { border: 10px double
black; } a { display: inline-block; line-height: 40px; font-size: 20px;
text-decoration: none; text-align: center; width: 200px; margin-bottom: 10px; }
ul { padding: 0; } li { list-style-type: none; }
```

### !important

위의 모든 계산을 무효화하는 데 사용할 수 있는 특별한 CSS가 있지만, 중요하게 생각해야 합니다. 이것은 특정 속성과 가치를 가장 구체적으로 만들어 계단식의 일반적인 규칙을 무시하는데 사용됩니다.

<b>반드시 필요한 경우가 아니면 절대 사용하지 않는 것이 좋습니다.</b> 계단식이 정상적으로 작동하는 방식을 변경하므로, CSS 스타일 문제를 해결하기 어렵습니다.

<br/>

## CSS 위치의 영향

CSS 선언의 중요성은 지정된 stylesheet에 따라 다릅니다 - 사용자가 stylesheet를 설정하여 개발자의 스타일을 재정의할 수 있습니다. 예를 들어, 사용자가 시각 장애인일 수 있으며, 쉽게 읽을 수 있도록 방문하는 모든 webpage의 글꼴 크기를 일반 크기의 두 배로 설정할 수 있습니다.

<br/>

## 요약하자면

충돌 선언은 다음 순서로 적용되며, 이후 선언은 이전 선언보다 우선합니다.

1. 사용자 에이전트 stylesheet의 선언<br/>
   (ex; 다른 스타일이 설정되지 않은 경우 사용되는 browser의 기본 스타일)
2. 사용자 stylesheet의 일반 선언<br/>
   (사용자가 설정한 사용자 정의 스타일)
3. 작성자 stylesheet의 일반적인 선언<br/>
   (web 개발자가 설정한 스타일)
4. 작성자 스타일 목록에서 중요한 선언
5. 사용자 stylesheet의 중요한 선언
