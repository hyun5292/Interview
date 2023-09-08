※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

# head 태그에는 무엇이 있을까? HTML의 MetaData

> [묙표] HTML의 head는 page를 열 때 web browser에 표시되지 않습니다. head는 `<title>` 같은 page나 CSS의 링크, favicon, 다른 metadata 포함합니다. <b>이 글에서는 위 내용들과 그 이상에 대해 다룰 것입니다.</b>

## HTML head란?

page를 열 때 browser에 표시되는 `<body>` 요소와 다르게, head의 내용은 page에 표시되지 않습니다. 대신에 head의 내용이 하는 일은 page에 대한 metadata를 포함하는 것입니다.

<br/>

## 제목 달기

문서의 title을 추가하기 위해 사용됩니다. head는 body에서 최상위 부분에 들어가는 `<h1>` 요소와 헷갈릴 수 있습니다. `<h1>` 요소는 가끔 title을 가리키기도 하지만 이것은 엄연히 다릅니다.

- `<h1>` 요소는 일반적으로 page당 한 번씩 사용되는데, page content의 제목이나 뉴스의 헤드라인을 표시하기 위해서 page를 열 때 browser에 표시됩니다.
- `<title>` 요소는 HTML 문서 전체의 title 표현하기 위한 metadata입니다.

<br/>

## MetaData: `<meta>` 요소

데이터를 설명하는 데이터

### 문서의 character 인코딩을 특정하기

- `<meta charset="utf-8">`<br/>: 문서의 character encoding에 대해서 간단히 표시합니다. utf-8은 전세계적인 character 집합으로 많은 언어들과 문자들을 포함합니다.

### 저자와 설명을 추가

많은 `<meta>` 요소가 name과 content 속성을 가집니다.

- name은 meta 요소가 어떤 정보의 형태를 갖고 있는지 알려줍니다.
- content는 실제 metadata의 content입니다.

```html
<meta name="author" content="Chris Mills" />
<meta
  name="description"
  content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications."
/>
```

- page content 관련 keyword를 포함시키는 것은 검색 엔진에서 이 page가 더 많이 표시될 가능성이 생기게 할 수 있습니다.(SEO; Search Engine Optimization)

### Other types of metadata

- <b style="color: grey;">Open Graph Data</b><br/>: Facebook이 website에 더 풍부한 metadata를 제공하기 위해 발명한 metadata protocol입니다.

```html
<meta
  property="og:image"
  content="https://developer.mozilla.org/mdn-social-share.png"
/>
<meta
  property="og:description"
  content="The Mozilla Developer Network (MDN) provides
information about Open Web technologies including HTML, CSS, and APIs for both Web sites
and HTML5 Apps. It also documents Mozilla products, like Firefox OS."
/>
<meta property="og:title" content="Mozilla Developer Network" />
```

## 맞춤 아이콘 추가하기

- favicon

```html
<link rel="shortcut icon" href="favicon.ico" type="image/x-icon" />
```

<br/>

## HTML에 CSS와 JavaScript 적용하기

- CSS

```html
<link rel="stylesheet" href="my-css=file.css" />
```

- JavaScript
  : `<script>`는 head에 들어갈 필요가 없습니다. `</body>` tag 바로 앞, 문서 본문의 맨 끝에 넣는 것이 좋으며, JavaScript를 적용하기 전에 모든 HTML 내용을 browser에서 읽었는지 확인하는 것이 좋습니다. 액세스 과정에서 JavaScript가 아직 존재하지 않는 요소라고 판단하며 에러가 날 수 있습니다.

```html
<script src="my-js-file.js"></script>
```

<br/>

## 문서의 기본 언어 설정

page의 언어를 설정할 수 있습니다. 이 작업은 HTML tag에 lang 속성을 추가하여 수행할 수 있습니다.

```html
<html lang="ko"></html>
```
