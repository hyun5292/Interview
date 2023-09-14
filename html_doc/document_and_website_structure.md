※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [문서의 기본 Section](#문서의-기본-section)<br/>
- [Content 구조화를 위한 HTML](#content-구조화를-위한-html)<br/>
- [HTML 레이아웃 요소에 대한 자세한 내용](#html-레이아웃-요소에-대한-자세한-내용)<br/>
  - [Non-semantic wrappers](#non-semantic-wrappers)<br/>
  - [줄 바꿈 및 수평선](#줄-바꿈-및-수평선)<br/>
  - [`<br>`: 줄 바꿈 요소](#br-줄-바꿈-요소)<br/>
  - [`<hr>`: 주제 별 휴식 요소](#hr-주제-별-휴식-요소)<br/>
- [간단한 웹 사이트 기획하기](#간단한-웹-사이트-기획하기)<br/>

# 문서 및 웹사이트 구조

> [목표] page의 개별 부분을 정의하는 것 외에도 HTML은 website 영역을 정의하는 데 사용되는 다양한 블록 수준의 요소를 자랑합니다. <b>이 글에서는 기본 website 구조를 계획하는 방법과 이 구조를 나타내는 HTML을 작성하는 방법을 살펴봅니다.</b>

## 문서의 기본 Section

webpage는 서로 꽤 다르게 보일 수 있지만 page가 전체 화면 비디오나 게임을 표시하거나 일종의 예술 프로젝트의 일부이거나 구조가 잘못되지 않는 한 유사한 표준 구성 요소를 공유하는 경향이 있습니다.

- <b style="color: orange;">Header</b><br/>: 일반적으로 상단에는 큰 제목, 로고 및 태그 라인이 포함된 큰 조각이 있습니다. 이는 일반적을 webpage마다 동일하게 유지됩니다.
- <b style="color: orange;">Navigation bar</b><br/>: site의 주요 section에 대한 link 일반적으로 menu, link 또는 tab으로 표시됩니다. header와 마찬가지로 이 content는 일반적으로 한 webpage에서 다른 webpage까지 일관성을 유지합니다. website 탐색이 일관되지 않으면 사용자가 혼란스럽고 좌절감을 느끼게 됩니다. 많은 web 디자이너는 탐색 모음을 개별 구성 요소가 아닌 header의 일부로 간주하지만 이는 필수 사항이 아닙니다. 실제로 일부 사람들은 두 기능을 분리하면 screen header가 더 잘 읽을 수 있기 때문에 두 기능을 분리하는 것이 접근성에 더 좋다고 주장합니다.
- <b style="color: orange;">Main Content</b><br/>: 특정 webpage의 고유한 content가 대부분 포함되어 있는 중앙의 큰 영역입니다. 이것은 page마다 확실히 달라지는 website의 한 부분입니다.
- <b style="color: orange;">Sidebar</b><br/>: 일부 주변 정보, link, 인용문, 광고 등 일반적으로 이는 기본 content에 포함된 내용과 관련이 있지만 또한 보조 navigation 시스템과 같이 반복되는 요소를 찾을 수 있는 경우도 있습니다.
- <b style="color: orange;">Footer</b><br/>: 일반적으로 작은 글씨, 저작권 고지 또는 연락처 정보가 포함된 page 하단의 조각입니다. header와 같은 일반적인 정보를 넣는 곳이지만 일반적으로 해당 정보는 website 자체에 중요하거나 부차적인 정보가 아닙니다. 바닥 글은 인기 있는 content에 빠르게 액세스할 수 있는 link를 제공하여 SEO 목적으로도 사용되기도 합니다.

<br/>

## Content 구조화를 위한 HTML

올바른 CSS를 사용하면 거의 모든 요소를 사용하여 다양한 section을 둘러싸서 원하는 대로 보이게 할 수 있습니다. 하지만 이전에 논의한 것처럼 semantic을 존중하고 올바른 작업에 올바른 요소를 사용해야 합니다.

- Header: `<header>`
- Navigation: `<nav>`
- Main Content: `<main>`
  - 다양한 content 하위 section: `<article>`, `<section>`, `<div>`
- Sidebar: `<aside>`
- Footer: `<footer>`

<br/>

## HTML 레이아웃 요소에 대한 자세한 내용

- `<main>`은 page에 고유한 content 용입니다. page 당 한 번만 사용하고, `<body>` 안에 넣으세요. 다른 요소 내에 중첩되어서는 안됩니다.
- `<article>`은 page의 나머지 부분 없이도 그 자체로 의미가 있는 관련 content 블록을 포함합니다.
- `<section>`은 `<article>`과 유사하지만 단일 기능 또는 테마를 구성하는 page의 단일 부분을 그룹화하는데 더 적합합니다. 각 section을 제목으로 시작하는 것이 모범 사례로 간주됩니다. 또한 상황에 따라 `<article>`을 여러 `<section>`으로 나누거나 `<section>`을 여러 `<article>`로 나눌 수 있습니다.
- `<aside>` main content와 직접적으로 관련 없지만 간접적으로 관련 있는 추가적인 정보를 제공하는 content를 포함합니다.
- `<header>`는 소개 content 그룹을 나타냅니다. `<body>`의 하위인 경우 webpage의 전역 header를 정의하지만 `<article>` 또는 `<section>`의 하위인 경우 해당 section에 대한 특정 header를 정의합니다.
- `<nav>`는 page에 대한 main navigation 기능을 포함합니다. 보조 link는 포함되지 않습니다.
- `<footer>`는 page에 대한 마지막 content 그룹을 나타냅니다.

### Non-semantic wrappers

때로는 일부 항목을 그룹화하거나 일부 content를 wrapping 하기 위한 semantic 의미 요소를 찾을 수 없는 상황에 직면하게 될 것입니다. 때로는 요소 세트를 그룹화하여 일부 CSS 또는 JavaScript를 사용하여 모든 요소에 단일 entity로 영향을 미치기를 원할 수도 있습니다. 이와 같은 경우를 위해 HTML은 `<div>` 및 `<span>` 요소를 제공합니다. 쉽게 targeting 할 수 있도록 일종의 레이블을 제공하려면 적절한 속성 class와 함께 이러한 항목을 사용하는 것이 좋습니다.

### 줄 바꿈 및 수평선

가끔 사용하고 알고 싶은 두 가지 요소는 `<br>`, `<hr>` 입니다.

### `<br>`: 줄 바꿈 요소

단락에 줄 바꿈을 만듭니다.

### `<hr>`: 주제 별 휴식 요소

텍스트의 주제 별 변경을 나타내는 수평선을 문서에 만듭니다.

<br/>

## 간단한 웹 사이트 기획하기

1. 대부분의 page에는 공통되는 몇 가지 요소(navigation, footer...)가 있다는 점을 명심하세요. 모든 page에 공통적으로 적용하고 싶은 내용을 기록해 두세요.
2. 각 page의 구조가 어떻게 보이길 원하는 지에 대한 대략적인 스케치를 그리세요. 각 블록이 무엇인지 확인하세요.
3. website에 추가하고 싶은 다른 content를 상상하세요.
4. 이 content들을 그룹으로 정렬해서 어떤 부분들이 다른 page들에 함께 있을 지에 대한 아이디어를 제공합니다.
5. 대략적인 sitemap을 그려보세요 - site에 대한 각 page 별 풍선을 만들고 page 간에 흐름을 선으로 그리세요. homepage는 가운데 있고 전부는 아니더라도 대부분은 연결될 것입니다. 예외는 있어도 작은 site의 대부분의 page들은 main navigation에 있을 것입니다. 어떻게 표시될 수 있는 지에 대한 메모를 포함할 수도 있습니다.
