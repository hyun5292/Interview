※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [HTML: HyperText Markup Language](#html-hypertext-markup-language)<br/>
- [HTML 요소 분석](#html-요소-분석)<br/>
  - [Nesting Elements](#nesing-elements)<br/>
  - [Empty Elements](#empty-elements)<br/>
- [HTML 문서 분석](#html-문서-분석)

<br/>

# HTML 시작하기

> [묙표] 이 글에서는 HTML의 절대적인 기본 사항을 다룹니다. 시작하는데 도움이 되도록 이 문서에서는 요소, 속성 및 여러분이 들어봤을 수 있는 기타 모든 중요한 용어를 정의합니다. 또한 이러한 내용이 HTML에 적합한 위치도 설명합니다. <b>HTML 요소의 구조, 일반적인 HTML page의 구조 및 기타 중요한 기본 언어 기능을 배우게 됩니다.</b>

<br/>

## HTML: HyperText Markup Language

<b style="color: #F23D3D">webpage와 content를 구조화하기 위해 사용하는 마크업 언어</b>입니다.

"<b style="color: orange">HyperText</b>" 언어는 tag로 둘러싸여 문서의 구조를 정의합니다. 문서의 골격에 해당하는 부분을 작성하는데 사용합니다.

`+` "<b style="color: green">markdown</b>" 언어는 markup 언어의 일종으로 읽고 쓰기에 쉽습니다.<br/>

- <b style="color: grey">펄(Perl) 스크립트</b><br/>: markdown 문서를 HTML 파일로 변환해주는 스크립트<br/>
  ex) SNS의 태그 기능, 위키 백과 편집 기능 등...

<br/>

## HTML 요소 분석

### 문단 요소

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started/grumpy-cat-small.png" alt="HTML 요소">

- 여는 태그(Opening Tag)
- 닫는 태그(Closing Tag)
- 콘텐츠(Content)
- 요소(Element)

<img src="https://developer.mozilla.org/en-US/docs/Learn/HTML/Introduction_to_HTML/Getting_started/grumpy-cat-attribute-small.png" alt="HTML 요소 속성">

- <b style="color: orange;">속성</b>은 실제 content로 표시되길 원하지 않는 추가적인 정보를 담고 있습니다.

### Nesing Elements

- <b style="color: orange">중첩(nesting)</b><br/>: 요소 안에 다른 요소를 넣는 것

### Empty Elements

conent가 없는 요소

```html
<img src="img 주소" alt="img 설명" />
```

<br/>

## HTML 문서 분석

```html
<!DOCTYPE html>
<html lang="ko">
  <head>
    <meta charset="utf-8" />
    <meta name="viewport" content="width=device-width" />
    <title>Page Title</title>
  </head>
  <body>
    <img src="img 주소" alt="img 설명" />
  </body>
</html>
```

- `<!DOCTYPE html>`<br/>: 필수 서문, doctype은 자동 오류 확인이나 다른 유용한 것을 의미하는 좋은 HTML로 인정받기 위해 HTML page가 따라야 할 일련의 규칙으로의 연결 통로로써 작동하는 것을 의미합니다.

- `<html></html>`<br/>: 루트(root) 요소. 문서의 고유 언어를 설정하는 <b style="color: #F2B705;">lang</b> 속성을 포함합니다.

- `<head></head>`<br/>: page를 조회하는 사람들에게 보여주는 content가 아닌 개발자가 HTML page에 포함하고 싶어하는 모든 재료들을 위한 container 역할을 합니다. keywords와 검색 결과에 표시되길 원하는 page 설명, content를 꾸미기 위한 CSS, 문자 집합 선언 등과 같은 것들을 포함합니다.

- `<meta charset="utf-8">`<br/>: 문서가 사용해야 할 문자 집합을 인간의 방대한 주류 기록 언어에 있는 대부분의 문자가 포함되어 있는 utf-8로 설정합니다.

- `<meta name="viewport" content="width=device-width">`<br/>: viewport 요소는 viewport의 너비에서 page가 렌더링 하도록 하며, mobile browser가 viewport보다 넓은 page를 렌더링 한 후 축소하는 것을 방지합니다.

- `<title></title>`<br/>: page의 제목을 설정합니다. 로드 된 page browser의 탭에 나타나는 제목입니다.

- `<body></body>`<br/>: page에 방문한 모든 web 사용자들에게 보여주길 원하는 모든 content를 담고 있습니다.
