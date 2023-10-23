※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [왜 반응형 이미지를 사용해야 할까요?](#왜-반응형-이미지를-사용해야-할까요)<br/>
- [반응형 이미지를 어떻게 만드나요?](#반응형-이미지를-어떻게-만드나요)<br/>
  - [해상도 전환: 다양한 크기](#해상도-전환-다양한-크기)<br/>
  - [해상도 전환: 동일한 크기, 다른 해상도](#해상도-전환-동일한-크기-다른-해상도)<br/>
  - [아트 디렉션](#아트-디렉션)<br/>
- [CSS나 JavaScript를 사용하면 안되는 이유가 무엇인가요?](#css나-javascript를-사용하면-안되는-이유는-무엇인가요)<br/>

<br/>

# 반응형 이미지

> [목표] <b>이 글에서는 화면 크기, 해상도 및 기타 기능이 매우 다양한 기기에서 잘 작동하는 이미지인 반응형 이미지의 개념에 대해 알아보고 이를 구현하는데 도움이 되는 HTML이 제공하는 도구를 살펴봅니다.</b> 이를 통해 다양한 기기에서 성능을 개선할 수 있습니다.

## 왜 반응형 이미지를 사용해야 할까요?

다양한 레이아웃에 대해 서로 다른 자른 이미지를 제공하려는 일반적인 문제를 <b style="color: orange;">아트 디렉션 문제</b>라고 합니다.

모바일 화면에서 page를 보는 경우 page에 큰 이미지를 삽입할 필요가 없습니다. 반대로 작은 래스터 이미지는 원래 크기보다 크게 표시되면 거칠게 보이기 시작합니다. browser는 사용자 device의 화면 크기에 따라 로드할 최적의 해상도를 결정할 수 있습니다. 이를 <b style="color: orange;">해상도 전환 문제</b>라고 합니다.

벡터 이미지가 이러한 문제를 해결해 줄 것이라고 생각할 수도 있고, 실제로 어느 정도는 파일 크기가 작고 크기가 잘 조정되므로 가능한 벡터 이미지를 사용하는 것이 좋습니다. 하지만 모든 이미지 유형에 적합한 것은 아닙니다. 벡터 이미지는 단순한 graphic, pattern, interface 요소 등에는 적합하지만 사진에서 볼 수 있는 디테일을 만들려면 매우 복잡해집니다.

<br/>

## 반응형 이미지를 어떻게 만드나요?

### 해상도 전환: 다양한 크기

동일한 이미지 content를 기기에 따라 더 크게 또는 더 작게 표시하고 싶을 때가 있습니다. 표준 `<img>` 요소는 일반적으로 browser에서 단일 소스 파일만 가리킬 수 있습니다.

```html
<img src="elva-fairy-800w.jpg" alt="요정 옷을 입은 엘바" />
```

<br/>

그러나 두 가지 속성(<b style="color: #F2B705;">srcset</b> 및 <b style="color: #F2B705;">sizes</b>)을 사용하여 browser가 올바른 이미지를 선택하는데 도움이 되는 힌트와 함께 여러 개의 소스 이미지를 제공할 수 있습니다.

```html
<img
  srcset="elva-fairy-480w.jpg 480w, elva-fairy-800w.jpg 800w"
  sizes="(max-width: 600px) 480px,
         800px"
  src="elva-fairy-800w.jpg"
  alt="요정 옷을 입은 엘바"
/>
```

<br/>

<b style="color: #F2B705;">srcset</b> 및 <b style="color: #F2B705;">sizes</b> 속성은 복잡해 보이지만 위와 같이 각 줄에 속성 값의 다른 부분을 사용하여 형식을 지정하면 이해하기가 그리 어렵지 않습니다. 각 값은 쉼표로 구분된 목록을 포함하며, 각 목록의 각 부분은 세 개의 하위 부분으로 구성됩니다.

<b style="color: #F2B705;">srcset</b>은 browser에서 선택할 수 있는 이미지 세트와 각 이미지의 크기를 정의합니다. 각 이미지 정보 세트는 쉼표로 이전 이미지와 구분됩니다.

1. <b>이미지 파일 이름</b>(elva-fairy-480w.jpg)
2. <b>공백</b>
3. <b>이미지의 고유 픽셀 너비</b>(480w), px 단위가 아닌 w 단위를 사용한다는 점에 유의하세요. 이미지의 고유 크기는 컴퓨터에서 이미지 파일을 검사하여 확인할 수 있는 실제 크기입니다.

<br/>

<b style="color: #F2B705;">sizes</b>는 일련의 미디어 조건을 정의하고 특정 미디어 조건에 해당할 때 어떤 이미지 크기를 선택하는 것이 가장 좋을지 알려주는데, 이 경우 각 쉼표 앞에 다음과 같이 작성합니다.

1. <b>미디어 조건</b>, 이에 대한 자세한 내용은 CSS 주제에서 배우겠지만, 지금은 미디어 조건이 화면이 될 수 있는 가능한 상태를 설명한다고 가정해보겠습니다. 이 경우 "viewport 너비가 600px 이하일 때"라고 말합니다.
2. <b>공백</b>
3. 미디어 조건이 참일 때 이미지가 채울 <b>슬롯의 너비</b>입니다.

<br/>

따라서 이러한 속성을 설정하면 browser는 다음과 같이 작동합니다.

1. 기기 너비를 확인합니다.
2. sizes 목록에서 어떤 미디어 조건이 가장 먼저 참인지 알아냅니다.
3. 해당 미디어 쿼리에서 지정된 슬롯 크기를 확인합니다.
4. 슬롯과 크기가 같은 srcset 목록에 참조된 이미지 또는 이미지가 없는 경우 선택한 슬롯 크기보다 큰 첫 번째 이미지를 로드합니다.

<br/>

viewport 너비가 480px인 지원 browser가 page를 로드하면 (max-width: 600px) 미디어 조건이 참이 되므로 browser는 480px 슬롯을 선택합니다. 고유의 너비(480w)가 슬롯 크기에 가깝기 때문에 elva-fairy-480w.jpg가 로드됩니다. 800px 사진은 디스크에서 128K인 반면 480px 버전은 63K에 불과하므로 절약할 수 있습니다.

<br/>

### 해상도 전환: 동일한 크기, 다른 해상도

여러 display 해상도를 지원하지만 모든 사람이 화면에서 동일한 실제 크기로 이미지를 보는 경우, 다소 쉬운 구문인 X-서술자 <b style="color: #F2B705;">sizes</b> 없이 <b style="color: #F2B705;">srcset</b>을 사용하여 browser가 적절한 해상도 이미지를 선택하도록 할 수 있습니다.

```html
<img
  srcset="elva-fairy-320w.jpg, elva-fairy-480w.jpg 1.5x, elva-fairy-640w.jpg 2x"
  src="elva-fairy-640w.jpg"
  alt="요정 옷을 입은 엘바"
/>
```

<br/>

### 아트 디렉션

<b style="color: orange;">아트 디렉션 문제</b>는 다양한 이미지 display 크기에 맞게 표시되는 이미지를 변경하려는 경우입니다. 예를 들어 desktop browser에서 볼 때 webpage에 사람이 가운데 있는 큰 풍경 사진이 포함되어 있다고 가정해 봅시다. mobile browser에서 볼 때는 동일한 이미지가 축소되어 이미지 속 사람이 매우 작아지고 잘 보이지 않습니다. mobile에서는 인물을 확대하여 더 작은 세로형 이미지를 표시하는 것이 더 좋을 것입니다.

```html
<img src="elva-800w.jpg" alt="달 엘바를 안고 서 있는 크리스" />
```

<br/>

`<picture>`로 해결해 봅시다. `<video>` 및 `<audio>`와 마찬가지로 `<picture>`요소는 browser가 선택할 수 있는 다양한 소스를 제공하는 여러 `<source>` 요소를 포함하는 wrapper이며, 그 뒤에 가장 중요한 `<img>` 요소가 있습니다.

```html
<picture>
  <source media="(max-width: 799px)" srcset="elva-480w-close-portrait.jpg" />
  <source media="(min-width: 800px)" srcset="elva-800w.jpg" />
  <img src="elva-800w.jpg" alt="딸 엘바를 안고 서 있는 크리스" />
</picture>
```

- `<source>` 요소에는 미디어 조건이 포함된 <b style="color: #F2B705;">media</b> 속성이 포함되어 있습니다. 첫 번째 <b style="color: #F2B705;">srcset</b> 예제와 마찬가지로 이러한 조건은 표시할 이미지를 결정하는 테스트이며, 참을 반환하는 첫 번째 이미지가 표시됩니다. 이 경우 viewport 너비가 799px 이하인 경우 첫 번째 `<source>` 요소의 이미지가 표시됩니다. viewport 너비가 800px 이상이면 두 번째 이미지가 표시됩니다.

- <b style="color: #F2B705;">srcset</b> 속성에는 표시할 이미지의 경로가 포함됩니다. 위의 `<img>`에서 살펴본 것처럼, `<source>`는 여러 이미지가 참조된 <b style="color: #F2B705;">srcset</b> 속성과 <b style="color: #F2B705;">sizes</b> 속성을 사용할 수 있습니다. 따라서 `<picture>` 요소를 통해 여러 이미지를 제공하면서 각 이미지의 해상도도 여러 개 제공할 수 있습니다. 현실적으로 이런 종류의 작업을 자주 수행하지는 않을 것입니다.

- 모든 경우에 `</picture>` 바로 앞에 <b style="color: #F2B705;">src</b> 및 <b style="color: #F2B705;">alt</b>와 함께 `<img>` 요소를 제공해야 하며, 그렇지 않으면 이미지가 표시되지 않습니다. 이는 미디어 조건 중 어느 것도 참을 반환하지 않을 때 적용되는 기본 사례와 `<picture>` 요소르 지원하지 않는 borwser를 위한 폴백을 제공합니다.

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images/picture-element-wide.png" alt="desktop 화면" />

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Multimedia_and_embedding/Responsive_images/picture-element-narrow.png" alt="mobile 화면" />

<br/>

### CSS나 JavaScript를 사용하면 안되는 이유는 무엇인가요?

browser가 page 로드를 시작하면 기본 구문 분석기가 apge의 CSS와 JavaScript를 로드하고 해석하기 전에 이미지를 다운로드하기 시작합니다. 이 매커니즘은 일반적으로 page 로드 시간을 단축하는데 유용하지만 반응형 이미지에는 도움이 되지 않으므로 srcset과 같은 솔루션을 구현해야 합니다.
