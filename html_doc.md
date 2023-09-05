# HTML DOCUMENT

[참고 사이트]<br/>
※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다. ※<br/>

- [Markup & Markdown](https://blog.cordelia273.space/15)

<br/><br/>

# HTML: HyperText Markup Language

Web page와 content를 구조화하기위해사용하는 마크업 언어입니다.

"HyperText"는 single 사이트 내에서또는 여러 사이트들 간에, Web page를서로 연결하는 Link들을 가리킵니다.

"Markup" 언어는 Tag로 둘러싸여문서의 구조를 정의합니다. 문서의골격에 해당하는 부분을 작성하는데 사용합니다.

- "MarkDown" 언어는 Markup 언어의일종으로 읽고 쓰기에 쉽습니다.
  - 펄(Perl) 스크립트
    : MarkDown 문서를 HTML 파일로 변환해주는 스크립트
    ex) SNS의 태그 기능, 위키 백과 편집 기능 등...

<br/><br/>

# HTML 요소 분석

<br/>

## 문단 요소

<img src="https://developer.mozilla.org/ko/docs/Learn/HTML/Introduction_to_HTML/Getting_started/grumpy-cat-small.png" alt="HTML 문단 요소" />

- 여는 태그 (Opening Tag)
- 닫는 태그 (Closing Tag)
- 콘텐츠 (Content)
- 요소 (Element)

<img src="https://developer.mozilla.org/ko/docs/Learn/HTML/Introduction_to_HTML/Getting_started/grumpy-cat-attribute-small.png" alt="HTML 속성" />

- 속성은 실제 Content로 표시되길 원하지 않는 추가적인 정보를 담고 있습니다.

<br/>

## 요소 중첩

- 중첩 (nesting)<br/>
  : 요소 안에 다른 요소를 놓는 것

<br/>

## 빈 요소

Content가 없는 요소

```html
ex) <img src="img 주소" alt="img 설명" />
```

<br/><br/>

# HTML 문서 해부

```html
<!DOCTYPE html>
<html>
  <head>
    <meta charset="utf-8" />
    <title>Test Page</title>
  </head>
  <body>
    <img src="image 주소" alt="image 설명" />
  </body>
</html>
```

- `<!DOCTYPE html>`<br/>
  : 필수 서문, DOCTYPE은 자동 오류 확인아니 다른 유용한 것을 의미하는 좋은 HTML로 인정받기 위해 HTML 페이지가 따라야 할 일련의 규칙으로의 연결 통로로써 작동하는 것을 의미했습니다.
- `<html></html>`<br/>
  : 루트(root) 요소. 문서의 고유 언어를 설정하는 lang 속성을 포함합니다.
- `<head></head>`<br/>
  : 페이지를 조회하는 사람들에게 보여주는 Content가 아닌 개발자가 HTML 페이지에 포함하고 싶어하는 모든 재료들을 위한 Container 역할을 합니다. Keywords와 검색 결과에 표시되길 원하는 Page 설명, Content를 꾸미기 위한 CSS, 문자 집합 선언 등과 같은 것들을 포함합니다.
- `<meta charset="utf-8">`<br/>
  : 문서가 사용해야 할 문자 집합을 인간의 방대한 주류 기록 언어에 있는 대부분의 문자가 포함되어 있는 utf-8으로 설정합니다.
- `<title></title>`<br/>
  : Page의 제목을 설정합니다. 로드 된 브라우저의 탭에 나타나는 제목입니다.
- `<body></body>`<br/>
  : Page에 방문한 모든 Web 사용자들에게 보여주길 원하는 모든 Content를 담고 있습니다.

<br/><br/>

# head 태그에는 무엇이 있을까? HTML의 메타데이터

<br/>

## 제목 달기

head는 body에서 최상위 부분에 들어가는 `<h1>` 요소와 헷갈릴 수 있습니다.

- `<h1>` 요소는 일반적으로 Page당 한 번씩 사용되는데, Page 내용물의 제목이나 뉴스의 헤드라인을 표시하기 위해서 Page를 열 때 브라우저에 표시됩니다.
- `<title>`은 (문서의 Content가 아니라) HTML 문서 전체의 title을 표현하기 위한 meta data입니다.

<br/>

## 메타데이터: <meta> 요소

데이터를 설명하는 데이터

- `<meta charset="utf-8" />`<br/>
  : 문서의 character encoding에 대해서 간단히 표시합니다. utf-8은 전세계적인 character 집합으로 많은 언어과 문자들을 포함합니다.

## 저자와 설명을 추가

많은 `<meta>` 요소가 name과 content 속성을 가집니다.

- name은 메타 요소가 어떤 정보의 형태를 갖고 있는지 알려줍니다.
- content는 실제 meta data의 content입니다.

```html
<meta name="author" content="Chris Mills" />
<meta
  name="description"
  content="The MDN Learning Area aims to provide
complete beginners to the Web with all they need to know to get
started with developing web sites and applications."
/>
```

- Page Content 관련 Keyword를 포함시키는 것은 검색 엔진에서 이 Page가 더 많이 표시될 가능성이 생기게 할 수 있습니다.(SEO; Search Engine Optimization)

## Other types of metadata

- Open Graph Data<br/>: Facebook이 웹 사이트에 더 풍부한 metadata를 제공하기 위해 발명한 metadata protocol입니다.

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
<link rel="shorcut icon" href="favicon.ico" type="image/x-icon" />
```

## HTML에 CSS와 JavaScript 적용하기

- CSS

```html
<link rel="stylesheet" href="my-css-file.css" />
```

- JavaScript<br/>: `<script>`는 head에 들어갈 필요가 없습니다. `</body>` 태그 바로 앞, 문서 본문의 맨 끝에 넣는 것이 좋으며, JavaScript를 적용하기 전에 모든 HTML 내용을 Browser에서 읽었는지 확인하는 것이 좋습니다. 액세스 과정에서 JavaScript가 아직 존재하지 않는 요소라고 판단하여 에러가 날 수 있습니다.

```html
<link src="my-js-file.js"></script>
```

## 문서의 기본 언어 설정

페이지의 언어를 설정할 수도 있습니다. 이 작업은 lang attribute를 여는 HTML 태그에 추가하여 수행할 수 있습니다.

```html
<html lang="ko"></html>
```
