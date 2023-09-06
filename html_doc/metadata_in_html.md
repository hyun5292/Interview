※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

# head 태그에는 무엇이 있을까? HTML의 MetaData

> HTML의 head는 page를 열 때 web browser에 표시되지 않습니다. head는 `<title>` 같은 page나 CSS의 링크, favicon, 다른 metadata 포함합니다. <b>이 글에서는 위 내용들과 그 이상에 대해 다룰 것입니다.</b>

## HTML head란?

page를 열 때 browser에 표시되는 `<body>` 요소와 다르게, head의 내용은 page에 표시되지 않습니다. 대신에 head의 내용이 하는 일은 page에 대한 metadata를 포함하는 것입니다.

<br/>

## 제목 달기

문서의 title을 추가하기 위해 사용됩니다. head는 body에서 최상위 부분에 들어가는 `<h1>` 요소와 헷갈릴 수 있습니다. `<h1>` 요소는 가끔 title을 가리키기도 하지만 이것은 엄연히 다릅니다.

- `<h1>` 요소는 일반적으로 page당 한 번씩 사용되는데, page content의 제목이나 뉴스의 헤드라인을 표시하기 위해서 page를 열 때 browser에 표시됩니다.
