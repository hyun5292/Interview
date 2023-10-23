※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [벡터 그래픽이란?](#벡터-그래픽이란)<br/>
- [SVG란?](#svg란)<br/>
- [Page에 SVG 추가하기](#page에-svg-추가하기)<br/>
  - [빠른 방법: img 요소](#빠른-방법-img-요소)<br/>
  - [문제 해결 및 browser 간 지원](#문제-해결-및-browser-간-지원)<br/>
  - [HTML에 SVG 코드를 포함하는 방법](#html에-svg-코드를-포함하는-방법)<br/>
  - [iframe을 사용하여 SVG를 삽입하는 방법](#iframe을-사용하여-svg를-삽입하는-방법)<br/>

<br/>

# Web에 벡터 그래픽 추가하기

> [목표] 벡터 그래픽은 파일 크기가 작고 확장성이 뛰어나 확대하거나 큰 크기로 확대해도 픽셀이 깨지지 않기 때문에 여러 상황에서 매우 유용합니다. <b>이 글에서는 webpage에 벡터 그래픽을 삽입하는 방법을 살펴봅시다.</b>

<br/>

## 벡터 그래픽이란?

web에서는 래스터 이미지와 벡터 이미지 두 가지 유형의 이미지로 작업하게 됩니다.

- <b style="color: orange;">래스터 이미지</b>는 픽셀 그리드를 사용하여 정의하되, 래스터 이미지 파일에는 각 픽셀이 배치될 위치와 정확한 색상을 나타내는 정보가 포함되어 있습니다. 널리 사용되는 웹 래스터 형식에는 비트맵(.bmp), PNG(.png), JPEG(.jpg), GIF(.gif) 등이 있습니다.

- <b style="color: orange;">벡터 이미지</b>는 알고리즘을 사용하여 정의하되, 벡터 이미지 파일에는 컴퓨터가 화면에 렌더링할 때 이미지가 어떻게 보일지 계산하는 데 사용할 수 있는 모양 및 경로 정의가 포함되어 있습니다. SVG 형식을 사용하면 web에서 사용할 수 있는 강력한 벡터 그래픽을 만들 수 있습니다.

page를 확대하면 차이가 분명해집니다. PNG 이미지에는 각 픽셀의 위치에 대한 정보가 포함되어 있기 때문에 확대할수록 픽셀화 됩니다. 확대하면 각 픽셀의 크기가 커져 화면의 여러 픽셀을 채우므로 이미지가 뭉개져 보이기 시작합니다. 그러나 벡터 이미지는 이미지의 크기에 관계없이 알고리즘을 사용하여 이미지의 모양을 계산하고 크기가 커짐에 따라 값을 조정하기 때문에 계속 선명하게 보입니다.

또한 벡터 이미지 파일을 이미지의 모든 픽셀에 대한 정보를 개별적으로 저장하는 대신 몇 가지 알고리즘만 저장하면 되기 때문에 래스터 이미지 파일보다 훨씬 가볍습니다.

<br/>

## SVG란?

SVG는 벡터 이미지를 설명하기 위한 XML 기반 언어입니다. 기본적으로 HTML과 같은 markup 언어이지만, 이미지에 표시할 모양과 해당 모양에 적용할 효과를 정의하는 다양한 요소가 있다는 점입니다. SVG는 content가 아닌 그래픽을 markup하기 위한 것입니다. 가장 간단하게는 `<circle>`, `<rect>`와 같은 간단한 도형을 만들기 위한 요소가 있습니다. 고급 SVG 기능에는 `<feColorMatrix>`, `<animate>`, `<mask>` 등이 있습니다.

<br/>

```html
<svg
  version="1.1"
  baseProfile="full"
  width="300"
  height="200"
  xmlns="http://www.w3.org/2000/svg"
>
  <rect width="100%" height="100%" fill="black" />
  <circle cs="150" cy="100" r="90" fill="blue" />
</svg>
```

<br/>

텍스트 편집기에서 간단한 SVG를 직접 코딩할 수 있습니다. 그러나 복잡한 이미지의 경우 매우 어려워지기 시작합니다. SVG 이미지를 만들 때 대부분의 사람들은 Inkscape나 illustrator와 같은 벡터 그래픽 편집기를 사용합니다.

- 장점

  - 벡터 이미지의 텍스트는 계속 액세스할 수 있습니다.(SEO에도 도움이 됩니다.)
  - SVG는 이미지의 각 구성 요소가 CSS를 통해 스타일을 지정하거나 JavaScript를 통해 스크립트를 작성할 수 있는 요소가 있기 때문에 styling/scripting에 적합합니다.

- 단점
  - SVG는 매우 빠르게 복잡해져 파일 크기가 커질 수 있으며, 복잡한 SVG는 browser에서 처리하는 데 상당한 시간이 걸릴 수 있습니다.
  - SVG는 만들려는 이미지의 종류에 따라 래스터 이미지보다 만들기가 더 어려울 수 있습니다.

<br/>

## page에 SVG 추가하기

### 빠른 방법: img 요소

`<img>` 요소를 통해 SVG를 임베드하려면 예상대로 <b style="color: #F2B705;">src</b> 속성에서 참조하기만 하면 됩니다. <b style="color: #F2B705;">width</b> 또는 <b style="color: #F2B705;">height</b> 속성이 필요합니다.

<br/>

```html
<img
  src="equilateral.svg"
  alt="세 변이 모두 같은 삼각형"
  height="87"
  width="100"
/>
```

- 장점

  - <b style="color: #F2B705;">alt</b> 속성에 텍스트에 해당하는 기본 제공 이미지 구문을 빠르고 친숙하게 사용할 수 있습니다.
  - `<a>` 요소 안에 `<img>`를 중첩하여 이미지를 하이퍼링크로 쉽게 만들 수 있습니다.
  - SVG 파일은 browser에서 캐시할 수 있으며 나중에 로드 된 이미지를 사용하는 모든 page의 로딩 시간이 빨라집니다.

- 단점
  - JavaScript로 이미지를 조작할 수 없습니다.
  - CSS로 SVG content를 제어하러면 SVG 코드에 인라인 CSS 스타일을 포함해야 합니다. SVG 파일에서 호출된 외부 스타일시트는 적용되지 않습니다.
  - CSS 의사 클래스(ex, :focus)를 사용하여 이미지 스타일을 다시 지정할 수 없습니다.

<br/>

### 문제 해결 및 browser 간 지원

SVG를 지원하지 않는 browser(IE 8 이하, Android 2.3 이하)의 경우, <b style="color: #F2B705;">src</b> 속성에서 PNG 또는 JPG를 참조하고 <b style="color: #F2B705;">srcset</b> 속성(최신 browser만 인식)을 사용하여 SVG를 참조할 수 있습니다. 이 경우 지원 browser에서만 SVG를 로드하며, 이전 browser에서는 대신 PNG를 로드합니다.

```html
<img src="equilateral.png" alt="변이 같은 삼각형" srcset="equilateral.svg" />
```

<br/>

SVG를 CSS 배경 이미지로 사용할 수도 있습니다. 아래 코드에서 구형 browser는 인식하는 PNG를 그대로 사용하지만 최신 browser는 SVG를 로드합니다.

```css
background: url("fallback.png") no-repeat center;
background-image: url("image.svg");
background-size: contain;
```

<br/>

### HTML에 SVG 코드를 포함하는 방법

텍스트 편집기에서 SVG 파일을 열고 SVG 코드를 복사한 후 HTML 문서에 붙여 넣을 수도 있는데, 이를 <b style="color: orange;">SVG 인라인 넣기</b> 또는 <b style="color: orange;">인라이닝 SVG</b>라고도 합니다. SVG 코드 스니펫이 `<svg>` 시작 태그로 시작하고, `</svg>` 끝 태그로 끝나는지 확인하세요.

```html
<svg width="300" height="200">
	<rect width="100%" height="100%" fill="green">
</svg>
```

- 장점

  - SVG를 인라인에 넣으면 HTTP 요청이 절약되므로 로딩 시간을 조금 줄일 수 있습니다.
  - SVG 요소를 클래스 및 ID를 할당하고 SVG 내 또는 HTML 문서에 대한 CSS 스타일 규칙을 넣는 모든 위치에서 CSS로 스타일을 지정할 수 있습니다. 실제로 모든 SVG 프레젠테이션 속성을 CSS 속성으로 사용할 수 있습니다.
  - SVG 인라인은 일반 스타일시트에서도 SVG 이미지에 CSS 상호 작용(ex, :focus) 및 CSS 애니메이션을 사용할 수 있는 유일한 접근 방식입니다.
  - SVG markup을 `<a>` 요소로 감싸서 하이퍼링크로 만들 수 있습니다.

- 단점
  - 이 방법은 SVG를 한 곳에서만 사용하는 경우에만 적합합니다. 복제로 인해 resource 절약적인 유지 관리가 필요합니다.
  - 추가 SVG 코드는 HTML 파일의 크기를 증가시킵니다.
  - browser는 일반 이미지 자산을 캐시하는 것처럼 인라인 SVG를 캐시할 수 없으므로 이미지가 포함된 첫 page가 로드 된 후에는 이미지가 포함된 page가 더 빨리 로드되지 않습니다.
  - `<foreignObject>` 요소에 폴백을 포함할 수 있지만 SVG를 지원하는 browser는 여전히 풀백 이미지를 다운로드합니다. 구형 browser를 지원하기 위해 추가 오버헤드를 감수할 가치가 있는지를 잘 따져봐야 합니다.

<br/>

### iframe을 사용하여 SVG를 삽입하는 방법

webpage처럼 browser에서 SVG 이미지를 열 수 없습니다.

```html
<iframe src="triangle.svg" width="500" height="500" sandbox>
  <img src="triangle.png" alt="세 변이 길지 않은 삼각형" />
</iframe>
```

- 단점
  - iframe에는 대체 매커니즘이 있지만 browser는 iframe을 전혀 지원하지 않는 경우에만 대체를 표시합니다.
  - SVG와 현재 webpage의 origin이 같지 않으면 기본 webpage에서 JavaScript를 사용하여 SVG를 조작할 수 없습니다.
