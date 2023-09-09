※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

# HTML text fundamentals

> [묙표] HTML의 주요 작업 중 하는 browser가 텍스트를 올바르게 표시할 수 있도록 텍스트 구조의 의미(semantics)를 제공하는 것입니다. <b>이번 글에서는 HTML을 사용하여 제목 및 단락을 추가하고, 단어를 강조하고, 목록을 만드는 등의 방법으로 텍스트 page를 구성하는 방법을 설명합니다.</b>

## 기본적인 것: 제목과 단락

대부분의 구조화 된 텍스트는 제목과 단락으로 구성됩니다.

- HTML에서 각 단락은 `<p>` 요소 안에 둘러싸여 있어야 합니다.
- 각 제목도 heading 요소 안에 둘러싸여 있어야 합니다.
  - heading 요소는 총 6개가 있습니다. - `<h1><h2><h3><h4><h5><h6>`

## 구조화된 계층을 구현하기

- 가급적이면 page 당 하나의 `<h1>`만 사용해야 합니다.
- 각 표제들을 계층적으로 올바른 순서로 사용해야 합니다.
- 6개의 heading을 사용할 수 있지만 꼭 필요한 것이 아니라면 한 page에 3개 이상을 사용하지 않도록 합니다. 많은 목차 레벨을 가진 문서는 다루기 힘들고 탐색하기 어렵습니다. 이러한 상황에서는 가능하다면 content를 여러 page로 나누는 것이 바람직합니다.

## 왜 우리는 구조가 필요할까요?

- webpage를 보는 user는 필요한 content를 빠르게 훑어보는 경향이 있고 자주 heading만 읽기도 합니다.
- 검색 엔진들은 당신의 page 내 heading을 page 검색 순위에 영향을 주는 중요한 키워드로 고려해 indexing 합니다.
- 심각한 시각 장애인들은 보통 webpage를 읽지 못합니다. 대신 screen reader를 사용해 듣습니다. 이 소프트웨어는 text content에 더 빠르게 접근할 수 있는 방안을 제공합니다. 사용된 다양한 기술 중 하나로, 그들은 heading을 읽어줌으로써 문서의 개요를 제공하며 그들의 사용자들이 필요로 하는 정보를 빠르게 찾을 수 있도록 합니다.
- content를 CSS로 꾸미거나, JavaScript로 흥미로운 일을 하게 하기 위해서, 관련 content를 감싸는 요소가 필요합니다.

## 우리는 왜 Semantic을 필요로 할까?

<b style="color: orange;">Semantic</b>은 정확한 요소를 사용하고 있는지, 우리의 content에 정확한 의미, 기능, 모습을 담았는지 확실히 하는 것

<br/>

# Lists

## Unordered Lists

```html
<ul>
  <li>milk</li>
  <li>eggs</li>
  <li>bread</li>
</ul>
```

결과

<ul>
  <li>milk</li>
  <li>eggs</li>
  <li>bread</li>
</ul>

## Ordered Lists

```html
<ol>
  <li>Drive to the end of the road</li>
  <li>Turn right</li>
  <li>Go straight across the first two roundabouts</li>
</ol>
```

결과

<ol>
  <li>Drive to the end of the road</li>
  <li>Turn right</li>
  <li>Go straight across the first two roundabouts</li>
</ol>

## List 내부의 List(Nesting Lists)

```html
<ol>
  <li>Eat Breakfast</li>
  <li>Take a Walk</li>
  <li>Supermarket</li>
  <li>
    <ul>
      <li>eggs</li>
      <li>milk</li>
    </ul>
  </li>
</ol>
```

결과

<ol>
  <li>Eat Breakfast</li>
  <li>Take a Walk</li>
  <li>Supermarket</li>
  <li>
    <ul>
      <li>eggs</li>
      <li>milk</li>
    </ul>
  </li>
</ol>

<br />

# 중요와 강조

## 중요(Emphasis)

글에서는 단어에 강세를 두기 위해 Italic 체로 표현하는 경향이 있습니다.

- HTML에서는 이러한 경우를 표시하기 위해 `<em>` 요소를 사용합니다.
- screen reader에 인식되면 다른 톤의 목소리로 표현됩니다.
- 단지 styling하기 위해 사용하는 것은 지양합니다.

```html
<p>I am <em>glad</em> you weren't <em>late</em>.</p>
```

결과

<p>I am <em>glad</em> you weren't <em>late</em>.</p>

## 강조(Strong Importance)

중요한 단어를 강조하기 위해 강세를 두고 말하거나 글자를 두껍게 표현합니다.

- HTML에서는 `<strong>` 요소를 사용합니다.
- screen reader에 인식되면 다른 톤의 목소리로 표현됩니다.
- 단지 styling하기 위해 사용하는 것은 지양합니다.<br/>
  -> styling을 위해서는 `<span>` 요소에 약간의 CSS를 더하거나 `<b>` 요소를 사용할 수 있습니다.

```html
<p>
  This liquid is <strong>highly toxic</strong> — if you drink it,
  <strong>you may <em>die</em></strong
  >.
</p>
```

결과

<p>
  This liquid is <strong>highly toxic</strong> — if you drink it,
  <strong>you may <em>die</em></strong>.
</p>

## Italic, Bold, UnderLine

Non-Semantic 표현에만 영향을 주는 이와 같은 요소들은 <b style="color: orange;">현재적 요소</b>로 알려져 있으며, 더 이상 사용되어서는 안됩니다.

- `<i>` (Italic) 요소<br/>ex) 외래어, 분류학 명칭, 전문 용어, 생각...
- `<b>` (Bold) 요소<br/>ex) 단어, 제품 이름, 주요 문장...
- `<u>` (UnderLine) 요소<br/>ex) 적절한 이름, 잘못된 철자...

```html
<!-- scientific names -->
<p>
  The Ruby-throated Hummingbird (<i>Archilochus colubris</i>) is the most common
  hummingbird in Eastern North America.
</p>

<!-- foreign words -->
<p>
  The menu was a sea of exotic words like <i lang="uk-latn">vatrushka</i>,
  <i lang="id">nasi goreng</i> and <i lang="fr">soupe à l'oignon</i>.
</p>

<!-- a known misspelling -->
<p>Someday I'll learn how to <u>spel</u> better.</p>

<!-- Highlight keywords in a set of instructions -->
<ol>
  <li><b>Slice</b> two pieces of bread off the loaf.</li>
  <li>
    <b>Insert</b> a tomato slice and a leaf of lettuce between the slices of
    bread.
  </li>
</ol>
```

결과

<!-- scientific names -->
<p>
  The Ruby-throated Hummingbird (<i>Archilochus colubris</i>) is the most common
  hummingbird in Eastern North America.
</p>

<!-- foreign words -->
<p>
  The menu was a sea of exotic words like <i lang="uk-latn">vatrushka</i>,
  <i lang="id">nasi goreng</i> and <i lang="fr">soupe à l'oignon</i>.
</p>

<!-- a known misspelling -->
<p>Someday I'll learn how to <u>spel</u> better.</p>

<!-- Highlight keywords in a set of instructions -->
<ol>
  <li><b>Slice</b> two pieces of bread off the loaf.</li>
  <li>
    <b>Insert</b> a tomato slice and a leaf of lettuce between the slices of
    bread.
  </li>
</ol>
