※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [WebPage에 어떻게 이미지를 넣을까?](#webpage에-어떻게-이미지를-넣을까)<br/>
  - [대체 텍스트](#대체-텍스트)<br/>
  - [너비와 높이](#너비와-높이)<br/>
  - [이미지 title](#이미지-title)<br/>
- [Media assets and licensing](#media-assets-and-licensing)<br/>
  - [라이선스 타입 이해하기](#라이선스-타입-이해하기)<br/>
    - [모든 권리 보유](#모든-권리-보유)<br/>
    - [허용](#허용)<br/>
    - [공개 도메인/CC0](#공개-도메인cc0)<br/>
    - [허가된 라이선스 이미지 검색하기](#허가된-라이선스-이미지-검색하기)<br/>
- [figures 및 figure captions으로 이미지에 주석 달기](#figures-및-figure-captions으로-이미지에-주석-달기)<br/>
- [CSS 배경 이미지](#css-배경-이미지)

<br/>

# HTML의 이미지

> [목표] 고려해 볼 수 있는 다른 유형의 멀티미디어가 있지만 단순한 이미지를 webpage에 삽입하는 데 사용되는 `<img> `요소로 쉽게 시작해 보겠습니다. <b>이 글에서는 기초 내용부터 심층적으로 사용하는 방법, `<figure>`를 사용하여 caption을 주석으로 추가하는 방법, CSS 배경 이미지와 관련된 사용 방법을 자세히 설명합니다.</b>

## WebPage에 어떻게 이미지를 넣을까?

이미지를 website에 넣기 위해서 `<img>` 요소를 사용합니다. 이것은 텍스트 내용이나 클로징 태그를 갖지 않는 void element이며, <b style="color: #F2B705;">src</b>와 <b style="color: #F2B705;">alt</b>가 있어야 유용합니다. <b style="color: #F2B705;">src</b> 속성은 페이지에 삽입하려는 이미지의 URL을 포함합니다. `<a>` 요소의 <b style="color: #F2B705;">href</b> 속성과 마찬가지로 <b style="color: #F2B705;">src</b> 속성은 상대 URL 또는 절대 URL일 수 있습니다. <b style="color: #F2B705;">src</b> 속성이 없으면 이미지 요소에 불러올 이미지가 없습니다.

<br/>

```html
<img src="images/dinosaur.jpg" alt="Dinosaur" />
```

<br/>

> [참고] 검색 엔진은 이미지 파일 이름을 읽고 SEO에 포함합니다. 따라서 그 내용을 설명하는 파일 이름을 사용하세요.

<br/>

절대 URL을 사용하는 것은 추천하지 않습니다. site에서 사용할 이미지를 호스팅 해야 하는데, 이는 간단한 설정에서는 website의 이미지를 HTML과 동일한 server에 보관하는 것을 의미합니다. 또한 유지보수 측면에서 절대 URL보다 상대 URL을 사용하는 것이 더 효율적입니다. 고급 설정에서는 CDN을 사용하여 이미지를 전송할 수 있습니다.

<br/>

> [경고] 다른 website에 호스팅 된 이미지를 허가 없이 <b style="color: #F2B705;">src</b> 속성으로 가리키지 마세요. 이를 “<b style="color: orange;">핫링크</b>”라고 합니다. 누군가 내 page를 방문할 때 이미지를 전송하는 대역폭 비용을 다른 사람이 지불하게 되므로 비윤리적인 행위로 간주됩니다. 또한 이미지가 삭제되거나 부끄러운 이미지로 변경되는 것을 제어할 수 없습니다.

> [참고] `<img>`와 `<video>`와 같은 요소들을 대체 요소라고 하기도 합니다. 그 이유는 요소의 내용 크기가 요소 그 자체가 아니라, 외부적인 요소(이미지나 비디오)에 의해 결정되기 때문입니다.

### 대체 텍스트

<b style="color: #F2B705;">alt</b> 속성은 이미지에 대한 텍스트 설명으로, 인터넷 연결이 느려서 이미지를 보거나 표시할 수 없는 경우 또는 렌더링 하는데 시간이 오래 걸리는 상황에서 사용할 수 있습니다.

<br/>

대체 텍스트가 필요한 이유

- 사용자가 시각적인 장애를 가지고 있는 경우 screen reader가 그 내용을 읽어줄 수 있습니다.
- 파일 명을 잘못 적거나 경로 이름을 잘못 적었을 수도 있습니다.
- 아직까지도 텍스트만 지원되는 browser를 사용하는 사용자들이 있기 때문에 이미지 지원이 안되는 사용자도 있습니다.
- 텍스트를 제공하여 검색 엔진이 이를 활용할 수 있도록 할 수 있습니다.
- 사용자가 데이터 전송량과 방해 요소를 줄이기 위해 고의적으로 이미지를 꺼 놓았을 수도 있습니다.

<br/>

<b style="color: #F2B705;">alt</b> 속성 안에 작성해야 하는 것

- <b>꾸밈 요소</b><br/>
  : 꾸미는 이미지를 위해서 CSS 배경 이미지를 사용하는 것이 좋습니다. 하지만 HTML을 사용해야 한다면, <b style="color: #F2B705;">alt=””</b>를 추가하세요. 만약 이미지가 content의 일부가 아니라면, screen reader는 그것을 읽는 데 시간을 낭비하지 않을 것입니다.
  <br/>

- <b>내용</b><br/>
  : 이미지가 중요한 정보를 제공한다면, 간단한 <b style="color: #F2B705;">alt</b> 텍스트나 더 좋은 방법으로, 모든 사람들이 볼 수 있는 메인 텍스트에 동일한 정보를 제공하세요. 메인 텍스트에 의해 충분히 설명되고 있다면, <b style="color: #F2B705;">alt=””</b>를 사용할 수 있습니다.
  <br/>

- <b>링크</b><br/>
  : 만약 이미지를 `<a>` 태그 안에 넣는다면, 이미지를 link로 만들기 위해서, 여전히 접근 가능한 link 텍스트를 제공해야 합니다. 이러한 경우에는, `<a>` 요소 안에 작성하거나, 이미지의 <b style="color: #F2B705;">alt</b> 속성 안에 작성할 수 있습니다.
  <br/>

- <b>텍스트</b><br/>
  : 텍스트를 이미지 안에 넣어서는 안됩니다. 예를 들어, 메인 헤딩이 drop-shadow가 필요하다면, 텍스트를 이미지 안에 넣는 대신 CSS를 사용하세요. 하지만, 피할 수 없다면 <b style="color: #F2B705;">alt</b> 속성 안에 텍스트를 제공해야 합니다.

### 너비와 높이

<b style="color: #F2B705;">width</b> 및 <b style="color: #F2B705;">height</b> 속성을 사용하여 이미지의 너비와 높이를 지정할 수 있습니다. 이들은 단위 없이 정수고 제공되며, 픽셀 단위로 이미지의 너비와 높이를 나타냅니다.

<br/>

```html
<img
  src="images/dinosaur.jpg"
  alt="The head and torso of a dinosaur skeleton;
          it has a large head with long sharp teeth"
  width="400"
  height="341"
/>
```

<br/>

너비와 높이를 사용하는 좋은 이유가 있습니다. page의 HTML과 이미지는 별도의 HTTP(s) 요청으로 browser에 의해 가져온 별개의 resource입니다. browser가 HTML을 받자마자, 그것은 사용자에게 표시하기 시작합니다. 이미지가 아직 받아지지 않았다면, browser는 HTML만 렌더링하고 이미지가 받아지면 page를 update 할 것입니다.

<br/>

browser가 HTML을 다운로드 받자마자, browser는 page를 보여주기 시작할 것입니다.

<br/>

이미지가 불러와지면, browser는 이미지를 page에 추가할 것입니다. 이미지가 공간을 차지하기 때문에, browser는 텍스트를 아래로 내려서 이미지를 위에 맞추어야 합니다.

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML/no-size.png" alt="이미지 width & height 속성 추가 전">

<br/>

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Images_in_HTML/size.png" alt="이미지 width & height 속성 추가 후">

<br/>

> [노트] 그럼에도 불구하고, HTML 속성을 사용하여 이미지의 실제 크기를 지정하는 것이 좋은 습관이지만, 이미지의 크기를 조정하는 데 사용해서는 안 됩니다. 만약 이미지의 크기를 조정해야 한다면, CSS를 사용하세요.

### 이미지 title

link와 마찬가지로, 이미지에 <b style="color: #F2B705;">title</b> 속성을 추가하여, 필요한 경우 추가적인 정보를 제공할 수 있습니다.

<br/>

```html
<img
  src="images/dinosaur.jpg"
  alt="The head and torso of a dinosaur skeleton;
          it has a large head with long sharp teeth"
  width="400"
  height="341"
  title="A T-Rex on display in the Manchester University Museum"
/>
```

<br/>

그러나 이 방법은 추천되지 않습니다. title에는 접근성 문제가 많습니다. 주로 screen reader 지원을 예측할 수 없고, 대부분의 browser는 마우스를 올려야만 표시됩니다.

<br/>

지원하는 정보 같은 경우 이미지에 첨부하는 것보다는, 본문에 포함하는 것이 좋습니다.

<br/>

## Media assets and licensing

이미지들(그리고 다른 미디어 자산들)은 여러 라이선스 타입들 아래에서 찾을 수 있습니다. 당신이 만드는 site에 이미지를 사용하기 전에 당신이 그것을 소유하고 있거나, 사용할 수 있는 권한이 있거나, 또는 소유자의 라이선스 조건을 준수하는지 확인하세요.

### 라이선스 타입 이해하기

#### 모든 권리 보유

음악, 책 또는 소프트웨어와 같은 원본 작업물의 창작자들은 종종 그들의 작업물을 닫힌 저작권 보호 아래에서 발표합니다. 이것은 기본적으로 그들이 그들의 작업물을 사용하는 독점적인 권리를 가지고 있다는 것을 의미합니다. 당신이 저작권 보호 이미지를 사용하고 싶다면, 다음 중 하나를 해야 합니다.

- 명시적으로 작성된 허가를 저작권 보유자로부터 얻으세요.
- 사용하기 위해 라이선스 비용을 지불하세요.
- 관할 지역에서 공정 사용 또는 공정 거래로 간주되는 경우에만 사용하세요.

저작권자들은 저작물에 저작권 표시 또는 라이선스 조건을 포함시키는 것이 필수적이지 않습니다. 저작권은 저작물이 유형화 된 매체에 창작되면 자동으로 발생합니다. 그래서 당신이 온라인에서 이미지를 찾고, 저작권 표시나 라이선스 조건이 없다면, 가장 안전한 방법은 모든 권리가 보호되는 저작권에 의해 보호된다고 가정하는 것입니다.

<br/>

#### 허용

MIT, BSD 또는 적절한 CC(Creative Commons) 라이선스와 같은 허용 라이선스에 따라 이미지를 공개하는 경우, 라이선스 비용을 지불하거나 사용을 위한 허가를 요청할 필요가 없습니다. 그럼에도 불구하고, 당신은 라이선스에 따라 다양한 라이선스 조건을 충족해야 합니다.

- 이미지의 원본 소스에 대한 link를 제공하고, 그것의 창작자에게 크레딧을 제공합니다.
- 변경 사항이 있는지 표시합니다.
- 이미지를 사용하여 만든 모든 2차 작업물을 원본과 동일한 라이선스 하에 공유합니다.
- 2차 작업물을 공유하지 않습니다.
- 이미지를 상업적인 작업물에 사용하지 않습니다.
- 이미지를 사용하는 모든 릴리즈와 함께 라이선스의 사본을 포함합니다.

> [참고] ”<b style="color: orange;">copyleft</b>”라는 용어를 허용 라이선스의 문맥에서 만날 수 있습니다. Copyleft 라이선스는 2차 작업물이 원본과 동일한 라이선스 하에 공개되어야 한다고 규정합니다.

<br/>

#### 공개 도메인/CC0

공개된 도메인은 때때로 “권리가 보호되지 않음”이라고 불립니다. 저작권이 적용되지 않으며 허가 없이 사용할 수 있고 라이선스 조건을 충족할 필요가 없습니다. 저작물은 저작권의 만료 또는 특정 권리 포기와 같은 다양한 방법으로 공개 도메인에 들어갈 수 있습니다.

공개된 도메인에 작업물을 놓는 가장 효과적인 방법 중 하나는 CC0라는 특정 creative commons 라이선스를 사용하는 것입니다. 이것은 명확하고 모호하지 않은 법적 도구를 제공합니다.

공개된 도메인을 사용할 때, 이미지가 공개된 도메인에 있는 것임을 증명하고 기록해 두세요. 예를 들어, 라이선스가 명확하게 표시된 원본 소스의 스크린 샷을 찍고, 라이선스 요구사항과 함께 이미지를 획득한 website에 page를 추가하는 것을 고려해보세요.

<br/>

#### 허가된 라이선스 이미지 검색하기

찾고 있는 이미지에 대한 설명과 관련된 라이선스 조건을 포함해서 이미지를 검색하세요. 예를 들어, “노란 공룡”을 검색할 때 “공개 도메인 이미지”, “공개 도메인 이미지 라이브러리”, “오픈 라이선스 이미지” 또는 비슷한 용어를 검색어에 추가하세요.

어떤 검색 엔진은 허가된 라이선스 이미지를 찾는 데 도움을 주는 도구를 가지고 있습니다. Google을 사용할 때, 이미지를 검색하기 위해 “이미지” 탭을 클릭하고, “도구”를 클릭하세요. 그러면 툴바에 “사용 권한” dropdown이 나타납니다.

이미지 repository site(ex, Flickr, ShutterStock, Pixabay)는 허가된 라이선스 이미지만 검색할 수 있도록 검색 옵션을 제공합니다.

## figures 및 figure captions으로 이미지에 주석 달기

caption에 대해 말하자면, 이미지에 caption을 추가하는 몇 가지 방법이 있습니다.

<br/>

```html
<div class="figure">
  <img
    src="images/dinosaur.jpg"
    alt="The head and torso of a dinosaur skeleton;
            it has a large head with long sharp teeth"
    width="400"
    height="341"
  />

  <p>A T-Rex on display in the Manchester University Museum.</p>
</div>
```

<br/>

이것도 좋습니다. 필요한 content를 포함하고 있습니다. CSS를 사용해서 멋지게 styling할 수 있습니다. 하지만 여기에는 문제가 있습니다. 이미지와 caption을 의미론적으로 연결하는 것이 없습니다. 이것은 screen reader에 문제를 일으킬 수 있습니다.

<br/>

더 나은 방법은 HTML `<figure>`와 `<figcaption>` 요소를 사용하는 것입니다. 이것들은 정확히 이 목적을 위해 만들어졌습니다. 즉, figure에 대한 의미론적인 컨테이너를 제공하고, figure를 caption과 명확하게 연결하는 것입니다.

<br/>

```html
<figure>
  <img
    src="images/dinosaur.jpg"
    alt="The head and torso of a dinosaur skeleton;
            it has a large head with long sharp teeth"
    width="400"
    height="341"
  />

  <figcaption>
    A T-Rex on display in the Manchester University Museum.
  </figcaption>
</figure>
```

<br/>

> [참고] 접근성의 관점에서, caption과 alt 텍스트는 다른 역할을 합니다. caption은 이미지를 볼 수 있는 사람들에게도 도움이 되지만, alt 텍스트는 이미지가 없을 때와 같은 기능을 제공합니다. 따라서 caption과 alt 텍스트는 같은 것을 말해서는 안됩니다. 왜냐하면 이미지가 없을 때 둘 다 나타나기 때문입니다.

<br/>

figure는 이미지일 필요가 없습니다. figure는 다음과 같은 독립적인 content 단위입니다.

- 이미지의 의미를 간략하고 이해하기 쉬운 방식으로 표현합니다.
- page의 선형 흐름에서 여러 곳에 배치될 수 있습니다.
- 본문을 지원하는 필수적인 정보를 제공합니다.

<br/>

## CSS 배경 이미지

이미지를 webpage에 삽입하기 위해 CSS도 사용할 수 있습니다. CSS <b style="color: #F2B705;">background-image</b> 속성과 다른 <b style="color: #F2B705;">background-\*</b> 속성들은 배경 이미지의 위치를 제어하는 데 사용됩니다.

<br/>

임베디드 이미지는 HTML 이미지보다 위치 지정과 제어가 훨씬 쉽습니다. CSS 배경 이미지는 장식용입니다. page에 예쁜 것을 추가하여 시각적으로 더욱 향상시키고 싶다면 괜찮습니다. 하지만 이러한 이미지는 의미가 없습니다. 텍스트 대체가 없으며, screen reader에서도 보이지 않습니다. 이 부분에서 HTML 이미지가 빛을 발합니다.
