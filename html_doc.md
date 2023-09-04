# HTML DOCUMENT

[참고 사이트]<br/>
※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※<br/>

- [Markup & Markdown](https://blog.cordelia273.space/15)

<br/><br/>

# HTML: HyperText Markup Language

    Web page와 content를 구조화하기 위해사용하는 마크업 언어입니다.

    "HyperText"는 single 사이트 내에서 또는 여러 사이트들 간에, Web page를 서로 연결하는 Link들을 가리킵니다.

    "Markup" 언어는 Tag로 둘러싸여 문서의 구조를 정의합니다. 문서의 골격에 해당하는 부분을 작성하는데 사용합니다.

    + "MarkDown" 언어는 Markup 언어의 일종으로 읽고 쓰기에 쉽습니다.
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

: Content가 없는 요소

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
