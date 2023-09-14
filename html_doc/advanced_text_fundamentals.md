※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [설명 목록](#설명-목록)<br/>
- [인용](#인용)<br/>
  - [인용 부호(Blockquotes)](#인용-부호blockquotes)<br/>
  - [인라인 인용(Inline Quotations)](#인라인-인용inline-quotations)<br/>
  - [인용(Citations)](#인용citations)<br/>
- [약어(Abbreviations)](#약어abbreviations)<br/>
- [연락처 세부 정보 Markup](#연락처-세부-정보-markup)<br/>
- [위 첨자와 아래 첨자(Superscript and Subscript)](#위-첨자와-아래-첨자superscript-and-subscript)<br/>
- [컴퓨터 코드를 표현](#컴퓨터-코드를-표현)<br/>
- [시간과 날짜 Markup](#시간과-날짜-markup)<br/>

# 고급 텍스트 서식

> [목표] HTML text fundamentals에서 다루지 않은 많은 요소들이 있습니다. 덜 알려졌지만, 여전히 알아두면 좋습니다. <b>인용문, 설명 목록, 컴퓨터 코드 및 기타 관련 텍스트, 아래 첨자와 위 첨자, 연락처 정보 등을 마크업하는 방법에 대해 알아봅시다</b>.

## 설명 목록

목적은 항목 집합과 관련 설명(ex; 용어 및 정의, 질문 및 답변)을 markup하는 것입니다.

- 설명 목록은 다른 목록 유형과 다른 wrapper를 사용합니다.
  - `<dl>` 또한 각 용어는 `<dt>` 요소로 wrapping 되고 각 설명은 `<dd>` 요소로 wrapping 됩니다.

```html
<dl>
  <dt>soliloquy</dt>
  <dd>
    In drama, where a character speaks to themselves, representing their inner
    thoughts or feelings and in the process relaying them to the audience (but
    not to other characters.)
  </dd>
  <dt>monologue</dt>
  <dd>
    In drama, where a character speaks their thoughts out loud to share them
    with the audience and any other characters present.
  </dd>
</dl>
```

결과

<dl>
  <dt>soliloquy</dt>
  <dd>
    In drama, where a character speaks to themselves, representing their inner
    thoughts or feelings and in the process relaying them to the audience (but
    not to other characters.)
  </dd>
  <dt>monologue</dt>
  <dd>
    In drama, where a character speaks their thoughts out loud to share them
    with the audience and any other characters present.
  </dd>
</dl>

## 인용

### 인용 부호(Blockquotes)

블록 수준 content section이 다른 곳에서 인용된 경우 이를 표시하기 위해 `<blockquote>` 태그로 이를 wrapping하고 <b style="color: #F2B705;">cite</b> 속성에 인용 소스를 가리키는 URL을 포함해야 합니다.

```html
<p>Here is a blockquote:</p>
<blockquote
  cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote"
>
  <p>
    The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or
    <em>HTML Block Quotation Element</em>) indicates that the enclosed text is
    an extended quotation.
  </p>
</blockquote>
```

결과

<p>Here is a blockquote:</p>
<blockquote
	cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/blockquote" >
	<p>
    The <strong>HTML <code>&lt;blockquote&gt;</code> Element</strong> (or
    <em>HTML Block Quotation Element</em>) indicates that the enclosed text is
    an extended quotation.
  </p>
</blockquote>

### 인라인 인용(Inline Quotations)

`<q>` 요소를 사용한다는 점 외에는 정확히 같은 방법으로 적용합니다.

```html
<p>
  The quote element — <code>&lt;q&gt;</code> — is
  <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">
    intended for short quotations that don't require paragraph breaks.
  </q>
</p>
```

결과

<p>
  The quote element — <code>&lt;q&gt;</code> — is
  <q cite="https://developer.mozilla.org/en-US/docs/Web/HTML/Element/q">
    intended for short quotations that don't require paragraph breaks.
  </q>
</p>

### 인용(Citations)

<b style="color: #F2B705;">cite</b> 속성은 유용해 보이지만, browser, screen readers 등등 많은 것에 되지 않습니다. JavaScript나 CSS를 사용하지 않는 이상 browser에 cite 요소를 보여줄 방법이 없습니다. page에 인용문의 출처를 표시하려면 link나 다른 적절한 방법을 통해 표시해야 합니다.

```html
<p>
  According to the
  <a href="/en-US/docs/Web/HTML/Element/blockquote">
    <cite>MDN blockquote page</cite></a
  >:
</p>
```

결과

<p>
  According to the
  <a href="/en-US/docs/Web/HTML/Element/blockquote">
    <cite>MDN blockquote page</cite></a>:
</p>

<br/>

## 약어(Abbreviations)

약어나 두문자어는 `<abbr>` 요소로 둘러쌉니다. 둘 중 하나를 포함하는 경우, 처음 사용 시 일반 텍스트로 용어 전체 확장을 제공하고 `<abbr>`을 사용하여 약어를 표시합니다. 이는 모든 user에게 약어의 의미를 알려주면서 content를 알리거나 표시하는 방법에 대한 힌트를 제공합니다.

```html
<p>
  I think <abbr title="Reverend">Rev.</abbr> Green did it in the kitchen with
  the chainsaw.
</p>
```

결과

<p>
	I think <abbr title="Reverend">Rev.</abbr> Green did it in the kitchen with
  the chainsaw.
</p>

<br/>

## 연락처 세부 정보 Markup

HTML에는 연락처 세부 정보를 markup하는 `<address>` 요소가 있습니다.

```html
<address>
  <p>
    Chris Mills<br />
    Manchester<br />
    The Grim North<br />
    UK
  </p>

  <ul>
    <li>Tel: 01234 567 890</li>
    <li>Email: me@grim-north.co.uk</li>
  </ul>
</address>
```

결과

<address>
  <p>
    Chris Mills<br />
    Manchester<br />
    The Grim North<br />
    UK
  </p>

  <ul>
    <li>Tel: 01234 567 890</li>
    <li>Email: me@grim-north.co.uk</li>
  </ul>
</address>

> [참고] `<address>` 요소는 오직 가장 가까운 `<article>`이나 `<body>`로 싸여있는 연락처 정보에만 사용되어야 합니다. site에 연락처 정보를 포함하기 위해 site의 footer나 article 안에 포함하는 것이 옳지만, content와 관련 없는 주소 목록은 markup 하지 않습니다.

<br/>

## 위 첨자와 아래 첨자(Superscript and Subscript)

날짜, 화학식, 수학 방정식과 같은 항목을 표시할 때 올바른 의미를 갖기 위해 위 첨자 `<sup>`와 아래 첨자 `<sub>`를 사용해야 하는 경우가 있습니다.

```html
<p>My birthday is on the 25<sup>th</sup> of May 2001.</p>
<p>
  Caffeine's chemical formula is
  C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>.
</p>
<p>If x<sup>2</sup> is 9, x must equal 3 or -3.</p>
```

결과

<p>My birthday is on the 25<sup>th</sup> of May 2001.</p>
<p>
  Caffeine's chemical formula is
  C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>.
</p>
<p>If x<sup>2</sup> is 9, x must equal 3 or -3.</p>

<br/>

## 컴퓨터 코드를 표현

- `<code>`<br/>: 컴퓨터 코드의 일반적인 부분을 markup 하는 데 사용됩니다.
- `<pre>`<br/>: 공백 유지(일반적으로 코드 블록) - 텍스트 내에 들여쓰기나 과도한 공백을 사용하면 browser는 이를 무시하고 렌더링 된 page에 표시되지 않습니다. 그러나 텍스트를 `<pre></pre>` 태그로 묶으면 공백은 텍스트 편집기에서 보는 것과 동일하게 렌더링됩니다.
- `<var>`<br/>: 변수 이름을 구체적으로 표시합니다.
- `<kbd>`<br/>: 컴퓨터에 입력된 키보드 입력을 표시하는 데 사용됩니다.
- `<samp>`<br/>: 컴퓨터 프로그램의 출력을 markup 하는 데 사용됩니다.

```html
<p>My birthday is on the 25<sup>th</sup> of May 2001.</p>
<p>
  Caffeine's chemical formula is
  C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>.
</p>
<p>If x<sup>2</sup> is 9, x must equal 3 or -3.</p>
```

결과

<p>My birthday is on the 25<sup>th</sup> of May 2001.</p>
<p>
  Caffeine's chemical formula is
  C<sub>8</sub>H<sub>10</sub>N<sub>4</sub>O<sub>2</sub>.
</p>
<p>If x<sup>2</sup> is 9, x must equal 3 or -3.</p>

<br/>

## 시간과 날짜 Markup

HTML은 또한 `<time>` 기계가 읽을 수 있는 형식으로 시간과 날짜를 표시하는 요소를 제공합니다.

```html
<!-- Standard simple date -->
<time datetime="2016-01-20">20 January 2016</time>
<!-- Just year and month -->
<time datetime="2016-01">January 2016</time>
<!-- Just month and day -->
<time datetime="01-20">20 January</time>
<!-- Just time, hours and minutes -->
<time datetime="19:30">19:30</time>
<!-- You can do seconds and milliseconds too! -->
<time datetime="19:30:01.856">19:30:01.856</time>
<!-- Date and time -->
<time datetime="2016-01-20T19:30">7.30pm, 20 January 2016</time>
<!-- Date and time with timezone offset -->
<time datetime="2016-01-20T19:30+01:00">
  7.30pm, 20 January 2016 is 8.30pm in France
</time>
<!-- Calling out a specific week number -->
<time datetime="2016-W04">The fourth week of 2016</time>
```

결과

<!-- Standard simple date -->

<time datetime="2016-01-20">20 January 2016</time>

<!-- Just year and month -->

<time datetime="2016-01">January 2016</time>

<!-- Just month and day -->

<time datetime="01-20">20 January</time>

<!-- Just time, hours and minutes -->

<time datetime="19:30">19:30</time>

<!-- You can do seconds and milliseconds too! -->

<time datetime="19:30:01.856">19:30:01.856</time>

<!-- Date and time -->

<time datetime="2016-01-20T19:30">7.30pm, 20 January 2016</time>

<!-- Date and time with timezone offset -->
<time datetime="2016-01-20T19:30+01:00">
  7.30pm, 20 January 2016 is 8.30pm in France
</time>
<!-- Calling out a specific week number -->
<time datetime="2016-W04">The fourth week of 2016</time>
