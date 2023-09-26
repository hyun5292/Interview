※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [iframes 자세히 보기](#iframes-자세히-보기)<br/>
  - [보안 문제](#보안-문제)<br/>
- [`<embed>`와 `<object>` 요소](#embed와-obejct-요소)<br/>

# `<object>`로부터 `<iframe>`까지 - 기타 임베딩 기술

> [목표] <b>webpage에 다양한 형태의 content를 넣을 수 있는 `<iframe>` 요소와 `<embed>` 요소, `<object>` 요소를 살펴보겠습니다.</b> `<iframe>` 요소는 다른 webpage를 삽입하기 위해, 다른 두 요소는 PDF 파일과 같은 외부 자원을 webpage에 추가하기 위해 사용합니다.

## iframes 자세히 보기

`<iframe>` 요소를 사용하면 현재 web 문서에 다른 web 문서를 삽입할 수 있습니다. 이는 직접 조작할 수 없거나 자체적인 버전을 구현하고 싶지 않은 외부 content를 여러분의 website에 포함할 때 아주 유용합니다.

`<iframe>`를 사용하기 전에 알고 있어야 할 보안 문제가 몇 가지 존재합니다.

```html
<head>
  <style>
    iframe {
      border: none;
    }
  </style>
</head>
<body>
  <iframe
    src="https://developer.mozilla.org/ko/docs/Glossary"
    width="100%"
    height="500"
    allowfullscreen
    sandbox
  >
    <p>
      <a href="/ko/docs/Glossary"> iframes을 지원하지 않는 브라우저용 링크 </a>
    </p>
  </iframe>
</body>
```

browser console 창을 보면 아래와 같은 에러 메시지를 확인할 수 있습니다.

> Refused to display 'https://developer.mozilla.org/' in a frame because it set 'X-Frame-Options' to 'deny'.

- <b>border: none</b><br/>: 이를 적용하면 `<iframe>`은 테두리 없이 표시됩니다. 적용하지 않으면 browser는 `<iframe>`은 기본적으로 테두리가 있는 상태로 표시하는데, 일반적으로 바람직하지 않습니다.

- <b style="color: #F2B705;">allowfullscreen</b><br/>: 이를 설정하면, `<iframe>`에서 Fullscreen API를 통해 전체 화면 모드를 실행할 수 있습니다.

- <b style="color: #F2B705;">src</b><br/>: `<video>`/`<img>`와 마찬가지로 삽입될 문서의 URL 경로를 저장합니다.

- <b style="color: #F2B705;">width와 height</b><br/>: `<iframe>` 요소에 원하는 너비와 높이를 설정할 수 있습니다.

- <b>대체 content</b><br/>: ` <iframe>``</iframe> ` 태그 사이에 대체 content를 추가하여 browser가 `<iframe>`을 지원하지 않는 경우 대체 content를 표시할 수 있습니다.

- <b style="color: #F2B705;">sandbox</b><br/>: IE 10 이상에서 지원되는 `<iframe>`의 다른 기능보다 이 특성은 상대적으로 최신 browser에서 작동하며 높은 보안 설정을 요구합니다.

> [참고] 속도를 향상 시키기 위해 메인 content가 완전히 로딩 된 이후에 JavaScript로 iframe의 <b style="color: #F2B705;">src</b> 속성을 설정하는 편이 좋습니다. webpage를 더 빠르게 이용할 수 있고 SEO 측정 시 중요한 지표인 webpage 로딩 시간을 단축할 수 있습니다.

### 보안 문제

iframe이 web 상에서 악의를 품은 사람들의 일반적인 공격 목표가 된다는 점입니다. 해커, 더 정확히는 크래커라 불리는 이 사람들은 iframe을 악용하여 webpage를 수정하거나, 사람들을 속여 사용자의 명의나 비밀번호 등 민감한 정보를 유출하려고 합니다. 이 때문에 enginner나 browser 개발자는 `<iframe>`을 더 안전하게 만들기 위해 다양한 보안 장치를 개발했습니다.

> [참고] <b style="color: #F2B705;">클릭재킹</b>은 iframe 공격 방식의 하나입니다. 눈에 보이지 않는 iframe을 web 문서에 삽입하거나, 해커들의 악성 website에 webpage를 삽입하여 사용자들의 활동을 빼돌립니다. 이는 사용자들의 잘못된 행동으로 유도하거나 민감한 데이터를 훔쳐내는 일반적인 기술입니다.

#### 필요한 경우에만 삽입하세요

#### HTTPS를 사용하세요

<b style="color: orange;">HTTPS</b>는 HTTP가 암호화된 버전입니다. 불가피한 경우를 제외하고는 항상 HTTPS를 사용하여 website를 전송해야 합니다.

1. HTTPS는 content가 전송 도중에 변조 될 위험을 줄여줍니다.
2. HTTPS 삽입된 content와 이를 포함하고 있는 문서를 서로에게 접근하는 것을 방지합니다.

#### 항상 <b style="color: #F2B705;">sandbox</b> 속성을 사용하세요

website를 악용하려는 사람들이 공격할 여지를 최소화하기 위해 삽입된 content에 대해서는 필요한 작업만 허용해야 합니다. 다른 코드 베이스에 영향을 미치지 않으면서도 특정 코드를 테스트하거나 적절하게 사용할 수 있도록 코드를 감싸고 있는 영역을 <b style="color: orange;">sandbox</b>라고 합니다.

#### CSP 지시어를 설정하세요

<b style="color: orange;">CSP</b>는 content 보안 정책을 나타내며 HTML 문서 보안을 개선하기 위해 고안된 일련의 HTTP 헤더를 제공합니다.

<b style="color: orange;">HTTPS 헤더</b>란 web server에서 webpage가 전송될 때 동반되는 metadata입니다. `<iframe>` 보안과 연관지어 말씀드리자면, 적절한 X-Frame-Options 헤더를 전송하도록 설정할 수 있습니다. 이렇게 하면 다른 website에서 webpage를 삽입하지 못하도록 만들어서 클릭재킹이나 다른 공격의 대상이 되는 일을 막을 수 있습니다.

<br/>

## `<embed>`와 `<obejct>` 요소

이 요소들은 PDF 같은 외부 content를 포함하기 위한 일반적인 임베딩 도구입니다.

하지만 이 요소를 사용하는 경우는 별로 없습니다. PDF를 표시하려면 webpage에 포함하기보다 보통 파일을 link로 연결하는 편이 좋습니다.

```html
<object data="mypdf.pdf" type="application/pdf" width="800" height="1200">
  <p>
    You don't have a PDF plugin, but you can
    <a href="mypdf.pdf">download the PDF file. </a>
  </p>
</object>
```

결과
<object data="mypdf.pdf" type="application/pdf" width="800" height="1200">

  <p>
    You don't have a PDF plugin, but you can
    <a href="mypdf.pdf">download the PDF file. </a>
  </p>
</object>
