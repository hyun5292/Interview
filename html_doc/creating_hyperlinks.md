※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [하이퍼링크란?](#하이퍼링크란)<br/>
- [Link의 구조](#link의-구조)<br/>
  - [Block Level Links](#block-level-links)<br/>
  - [Image Links](#image-links)<br/>
  - [title 속성에 부가적인 정보를 더하기](#title-속성에-부가적인-정보를-더하기)<br/>
- [URL과 path에 대한 기본 지침](#url과-path에-대한-기본-지침)<br/>
  - [문서 조각](#문서-조각)<br/>
  - [절대 URL과 상대 URL](#절대-url과-상대-url)<br/>
  - [좋은 관습](#좋은-관습)<br/>
- [Email Link](#email-link)<br/>
  - [세부 사항 지정하기](#세부-사항-지정하기)<br/>

<br/>

# 하이퍼링크 만들기

> [목표] web을 web 답게 만든다는 점에서 하이퍼링크는 중요합니다. <b>이 글에서는 link를 만드는 데 필요한 구문을 보여주고 link의 모범 사례를 설명합니다.</b>

## 하이퍼링크란?

문서를 다른 문서나 resource에 연결하거나, 문서의 특정 부분에 연결하거나, web 주소에서 app을 사용할 수 있습니다. 클릭하거나 다른 방법으로 활성화된 web browser가 다른 web 주소로 이동하도록 거의 모든 web content를 link로 변환할 수 있습니다.

> [참고] URL은 web 상에서 존재할 수 있는 어느 것이든 연결할 수 있습니다. web browser가 파일을 표시하거나 처리하는 방법을 모르는 경우 파일을 열 것인가 또는 파일을 다운로드할 것인지 묻는 메시지가 표시됩니다.

<br/>

## Link의 구조

기본 link는 텍스트 또는 기타 내용을 `<a>` 요소 안에 감싸고 web 주소를 포함하는 href 속성을 사용하여 생성됩니다.

```html
<p>
  나는 <a href="https://www.naver.com/">Naver 홈페이지</a>로 향하는 링크를
  만들었습니다.
</p>
```

결과

<p>
  나는 <a href="https://www.naver.com/">Naver 홈페이지</a>로 향하는 링크를
  만들었습니다.
</p>

### Block Level Links

Block Level 요소들도 link로 바꿀 수 있습니다.

```html
<a href="https://www.naver.com/">
  <h1>Naver</h1>
</a>
<p>한국 최고의 검색 사이트.</p>
```

결과
<a href="https://www.naver.com/">

  <h1>Naver</h1>
</a>
<p>
  한국 최고의 검색 사이트.
</p>

### Image Links

```html
<a href="https://www.naver.com/">
  <img
    width="50%"
    src="https://res.cloudinary.com/sudol5292/image/upload/v1694452590/01_NAVER_Logo_Green_yktcbw.png"
    alt="Naver Page"
  />
</a>
```

결과<br/>
<a href="https://www.naver.com/">
<img width="50%" src="https://res.cloudinary.com/sudol5292/image/upload/v1694452590/01_NAVER_Logo_Green_yktcbw.png" alt="Naver Page" />
</a>

### title 속성에 부가적인 정보를 더하기

link에 추가할 수 있는 또 다른 속성은 title 입니다. title은 page에 포함된 정보 또는 website에 주의해야 할 사항 등 link에 대한 추가 정보를 포함하고 있습니다.

```html
<p>
  I'm creating a link to
  <a href="https://www.naver.com/" title="The best place to search something">
    Naver Page</a
  >.
</p>
```

결과

<p>
	I'm creating a link to
	<a
		href="https://www.naver.com/"
		title="The best place to search something">
	Naver Page</a>.
</p>

> [참고] link 제목은 hover에만 표시되므로 키보드 컨트롤이나 터치 스크린을 사용하여 webpage를 탐색하는 사용자는 제목 정보에 액세스하는 데 어려움을 겪습니다. title의 정보가 page의 사용헤 있어서 정말로 중요하다면, 해당하는 정보를 일반 텍스트로 넣어줌으로써 모든 사용자가 접근할 수 있는 방식으로 표시해야 합니다.

<br/>

## URL과 path에 대한 기본 지침

URL은 단순히 무언가가 web 상의 어디에 위치하는지 결정하는 하나의 텍스트 문자열입니다. URL은 파일들을 찾기 위해 path에 이용합니다. path는 당신이 관심 있어하는 파일이 파일 시스템 어디에 있는지 구체적으로 명시합니다.

<img src="https://developer.mozilla.org/ko/docs/Learn/HTML/Introduction_to_HTML/Creating_hyperlinks/simple-directory.png" alt="디렉토리 구조" />

- 이 directory 구조의 Root를 <b style="color: orange;">creating-hyperlinks</b>라고 부릅니다. website를 Local 단에서 다룰 때에는 전체 website가 모두 들어갈 수 있는 directory를 가져야 합니다. Root 안에서 우리는 <span style="color: black; background: #E7F3F8;">index.html</span> 파일과 <span style="color: black; background: #E7F3F8;">contacts.html</span> 파일을 갖습니다. 실제 website에서 <span style="color: black; background: #E7F3F8;">index.html</span>은 우리의 homepage 또는 랜딩 page(website의 접속 포인트 또는 website 특정 부분이 되는 page)가 될 것입니다.

- Root 안에는 pdfs와 projects라는 두 개의 directory가 있습니다. 이들은 각각 PDF(project-brief.pdf)와 <span style="color: black; background: #E7F3F8;">index.html</span> 파일을 내부에 가지고 있습니다. 두 개의 <span style="color: black; background: #E7F3F8;">index.html</span> 파일이 서로 다른 파일 시스템 위치에 있는 한, 하나의 프로젝트에 두 개의 <span style="color: black; background: #E7F3F8;">index.html</span> 파일을 포함할 수 있습니다. 두 번째 <span style="color: black; background: #E7F3F8;">index.html</span> 파일은 아마 프로젝트와 관련된 정보의 메인 랜딩 page가 될 것입니다.

  - 같은 directory(폴더)
    : <span style="color: black; background: #E7F3F8;">contacts.html</span>을 가리키는 하이퍼링크를 <span style="color: black; background: #E7F3F8;">index.html</span>(최상위 레벨) 안에 포함하려면 현재 파일과 동일한 directory에 있으므로 연결하려는 파일의 이름만 지정하면 됩니다. 따라서 사용할 URL은 <span style="color: black; background: #E7F3F8;">contacts.html</span>입니다.

    ````html
    - Root 안에는 pdfs와 projects라는 두 개의 directory가 있습니다. 이들은 각각
    PDF(project-brief.pdf)와 index.html 파일을 내부에 가지고 있습니다. 두 개의
    index.html 파일이 서로 다른 파일 시스템 위치에 있는 한, 하나의 프로젝트에 두
    개의 index.html 파일을 포함할 수 있습니다. 두 번째 index.html은 아마
    프로젝트와 관련된 정보의 메인 랜딩 page가 될 것입니다. - 같은
    directory(폴더) : contacts.html을 가리키는 하이퍼링크를 index.html(최상위
    레벨) 안에 포함하려면 현재 파일과 동일한 directory에 있으므로 연결하려는
    파일의 이름만 지정하면 됩니다. 따라서 사용할 URL은 contacts.html 입니다.
    ```jsx
    <p>
      Want to contact a specific staff member? Find details on our
      <a href="contacts.html">contacts page</a>.
    </p>
    ````

    - 부모 directory로 상향 이동
      : pdfs/project-brief.pdf를 가리키는 하이퍼링크를 projects/index.html 안에 포함하려면 directory 레벨을 올린 다음 다시 pdf directory로 내려가야 합니다. “상위 directory 이동”은 두 개의 점(..)을 사용하여 표시합니다.

    ```html
    <p>
      나의 <a href="../pdfs/project-brief.pdf">프로젝트 개요</a> 링크입니다.
    </p>
    ```

### 문서 조각

문서 상단이 아닌 HTML 문서 내부의 특정 부분(document fragments)에 연결할 수 있습니다. 그러기 위해 먼저 여러분은 연결하고 싶은 태그에 id 속성을 넣어주어야 합니다. 일반적으로 아래와 같이 특정 헤드라인에 연결하는 것이 타당합니다.

```html
<h2 id="Mailing_address">Mailing 주소</h2>
```

그런 다음 해당 ID에 연결하려면 아래 예시와 같이 URL 끝에 해시(#) 기호를 포함하면 됩니다.

```html
<p>
  우리에게 메일을 보내고 싶나요? 그럼
  <a href="contacts.html#Mailing_address">메일 주소</a>를 확인해주세요.
</p>
```

문서 조각을 참조하여 현재 문서의 다른 부분에 연결할 수도 있습니다.

```html
<p>
  <a href="#Mailing_address">회사 메일 주소</a>는 페이지의 하단에서 찾을 수
  있습니다.
</p>
```

### 절대 URL과 상대 URL

- 절대 URL
  : protocol과 domain name을 포함한, web에서 정의된 절대적인 위치를 가리킵니다.

  - 어디에 사용되든 항상 같은 장소를 가리킵니다.

- 상대 URL
  : 연결되어 있는 파일로부터 상대적인 위치를 가리킵니다.
  - 파일의 실제 위치가 어디냐에 따라 다른 장소를 가리킵니다.

### 좋은 관습

- 링크 명을 명확하게

  - 검색 엔진은 link 텍스트를 사용하여 대상 파일을 undexing하므로 link 텍스트에 keyword를 포함하여 link되는 내용을 효과적으로 설명하는 것이 좋습니다.

  - 시각적 독자들은 모든 단어를 읽는 것보다 page를 훑어보고, link와 같이 눈에 띄는 page 특징에 끌릴 것입니다.

  - URL을 link 텍스트의 일부로 반복하지 마십시오. URL이 보기 흉하며, 화면을 보는 사람들이 글자로 URL을 볼 때 이상하게 보입니다.

  - link 텍스트에 "link"나 "links to"라고 쓰지 마십시오. 잡음이 될 뿐입니다. screen reader는 사용자에게 링크가 있다고 말합니다.

  - link 텍스트를 가능한 짧게 유지하십시오. screen reader는 전체 link 텍스트를 해석해야 하므로 유용합니다.

  - 동일한 텍스트의 여러 복사본이 서로 다른 장소에 연결되는 경우를 최소화합니다. "여기 클릭"이라는 label이 붙어있는 link 목록이 있는 경우, screen reader 사용자에게 문제가 발생할 수 있습니다.

- 비 HTML resource 연결 시 명확한 표식 남기기
  : 다운로드 될 resource, 스트리밍 될 resource 또는 다른 잠재적으로 예기치 않은 효과에 연결할 경우, 혼동을 줄이기 위해 명확한 문구를 추가해야 합니다.

- 다운로드 연결 시 download 속성 사용
  : browser에서 열지 않고 다운로드할 resource에 연결하는 경우 download 속성을 사용하여 기본 저장 파일 이동을 제공할 수 있습니다.

<br/>

## Email Link

클릭하면 resource 또는 page에 연결하는 대신 새 발신 전자 메일 메시지를 여는 링크 또는 단추를 만들 수 있습니다. 이것은 `<a>` 태그 안에 mailto: URL Schema를 사용하여 구현할 수 있습니다.

```html
<a href="mailto:nowhere@mozilla.org">아무데나 전자 메일 보내기</a>
```

결과
<a href="mailto:nowhere@mozilla.org">아무데나 전자 메일 보내기</a>

- 이메일 주소는 선택입니다. 생략하면 새로운 발신 이메일 창이 열립니다. 이것은 종종 사용자가 선택한 주소로 이메일을 보내기 위해 클릭할 수 있는 "공유" link로써 유용합니다.

### 세부 사항 지정하기

이메일 주소 외에도 다른 정보를 제공할 수 있습니다. 이 중 가장 일반적으로 사용되는 것은 "subject", "cc", "body"입니다.

```html
<a
  href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&subject=The%20subject%20of%20the%20email&body=The%20body%20of%20the%20email"
>
  Send mail with cc, bcc, subject and body
</a>
```

결과
<a
  href="mailto:nowhere@mozilla.org?cc=name2@rapidtables.com&bcc=name3@rapidtables.com&subject=The%20subject%20of%20the%20email&body=The%20body%20of%20the%20email">
Send mail with cc, bcc, subject and body
</a>
