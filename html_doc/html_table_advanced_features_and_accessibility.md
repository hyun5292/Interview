※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [`<caption>`을 사용하여 Table에 Caption 추가](#caption을-사용하여-table에-caption-추가)<br/>
- [`<thead>`, `<tfoot>`, `<tbody>`를 사용하여 구조 추가](#thead-tfoot-tbody를-사용하여-구조-추가)<br/>
- [중첩 Table](#중첩-table)<br/>
- [시각 장애가 있는 사용자를 위한 Table](#시각-장애가-있는-사용자를-위한-table)<br/>
  - [열 및 행 머리글 사용](#열-및-행-머리글-사용)<br/>
  - [범위 속성](#범위-속성)<br/>
  - [ID 및 Header 속성](#id-및-header-속성)<br/>

<br/>

# `<caption>`을 사용하여 Table에 Caption 추가

> [목표] <b>이 모듈의 두 번째 문서에서는 캡션/요약, 행을 표 머리글, 본문 및 바닥글 섹션으로 그룹화하는 등 HTML 표의 몇 가지 고급 기능을 살펴보고 시각 장애가 있는 사용자를 위한 표 접근성도 살펴봅니다.</b>

## `<caption>`을 사용하여 Table에 Caption 추가

`<caption>` 태그를 넣고 `<table>` 태그로 감싸줌으로써 table에 caption을 줄 수 있습니다. 반드시 여는 `<table>` 태그 바로 밑에 넣어야 합니다.

```html
<table>
  <caption>
    Dinosaurs in the Jurassic period
  </caption>
  ...
</table>
```

결과

<table>
	<caption>
		Dinosaurs in the Jurassic period
	</caption>
	...
</table>

caption은 table 내용에 대한 설명을 포함하기 위한 것입니다. page를 스캔할 때 표가 유용한지 빠르게 확인하려는 모든 독자에게 유용하며, 특히 시각 장애가 있는 사용자에게 유용합니다. table의 내용을 찾기 위해 screen reader가 많은 cell의 내용을 읽게 하는 대신 사용자는 caption에 의존하여 table을 더 자세히 읽을지 여부를 결정할 수 있습니다.

<br/>

## `<thead>`, `<tfoot>`, `<tbody>`를 사용하여 구조 추가

table의 구조가 좀 더 복잡해지면 table에 더 많은 구조적 정의를 제공하는 것이 유용합니다. 이를 수행하는 방법은 table의 머리글, 바닥글, 및 본문 섹션을 markup할 수 있는 `<thead>`, `<tfoot>`, `<tbody>`를 사용하는 것입니다.

이를 사용하려면:

- `<thead>`는 table의 머리글 부분을 wrapping 해야 합니다. 일반적으로 열 머리글을 포함하는 첫 번째 행이지만 그런 것은 아닙니다. `<col>` 요소를 사용하는 경우 `<colgroup>` table header는 해당 요소 바로 아래에 와야 합니다.
- `<tfoot>`은 바닥글인 table 부분을 wrapping 해야 합니다. table 하단 오른쪽 table 바닥글을 포함하거나 table header 바로 아래에 table 바닥글을 포함할 수 있습니다.(browser는 여전히 table 하단에 렌더링합니다.)
- `<tbody>`는 표 머리글이나 바닥글에 없는 표 content의 다른 부분을 wrapping 해야 합니다. 구성 방법에 따라 표 머리글이나 바닥글 아래에 표시됩니다.

<br/>

## 중첩 Table

요소를 포함하여 전체 구조를 포함하는 한 table을 다른 table 안에 중첩할 수 있습니다. 이는 일반적으로 markup을 더 혼란스럽게 만들고 screen reader 사용자가 접근하기 어렵게 만들고 많은 경우 기존 table에 cell/행/열에 삽입할 수도 있게 때문에 실제로 권장되지 않습니다. 그러나 예를 들어 다른 소스에서 content를 쉽게 가져오려는 경우에는 때때로 필요합니다.

```html
<table id="table1">
  <tr>
    <th>title1</th>
    <th>title2</th>
    <th>title3</th>
  </tr>
  <tr>
    <td id="nested">
      <table id="table2">
        <tr>
          <td>cell1</td>
          <td>cell2</td>
          <td>cell3</td>
        </tr>
      </table>
    </td>
    <td>cell2</td>
    <td>cell3</td>
  </tr>
  <tr>
    <td>cell4</td>
    <td>cell5</td>
    <td>cell6</td>
  </tr>
</table>
```

결과

  <tr>
    <th>title1</th>
    <th>title2</th>
    <th>title3</th>
  </tr>
  <tr>
    <td id="nested">
      <table id="table2">
        <tr>
          <td>cell1</td>
          <td>cell2</td>
          <td>cell3</td>
        </tr>
      </table>
    </td>
    <td>cell2</td>
    <td>cell3</td>
  </tr>
  <tr>
    <td>cell4</td>
    <td>cell5</td>
    <td>cell6</td>
  </tr>

<br/>

## 시각 장애가 있는 사용자를 위한 Table

data table을 사용하는 방법을 간략하게 요약해보겠습니다. table은 데이터에 빠르게 접근하고 다양한 값을 조회할 수 있는 편리한 도구가 될 수 있습니다.

### 열 및 행 머리글 사용

screen reader는 모든 header를 식별하고 이를 사용하여 해당 header와 관련 cell을 프로그래밍 방식으로 연결합니다. 열과 행 머리글의 조합은 각 cell의 데이터를 식별하고 해석하므로 screen reader 사용자는 시력이 있는 사용자와 유사하게 테이블을 해석할 수 있습니다.

### 범위 속성

<b style="color: #F2B705;">scope</b>는 요소에 추가하여 header가 어떤 cell에 대한 header인지 정확히 알려주기 위한 속성입니다. header가 포함된 행의 header인지, 열의 header인지 알 수 있습니다.

```html
<thead>
  <tr>
    <th scope="col">Purchase</th>
    <th scope="col">Location</th>
    <th scope="col">Date</th>
    <th scope="col">Evaluation</th>
    <th scope="col">Cost (€)</th>
  </tr>
</thead>
```

그리고 각 행에는 다음과 같이 정의된 header가 있을 수 있습니다.

```html
<tr>
  <th scope="row">Haircut</th>
  <td>Hairdresser</td>
  <td>12/09</td>
  <td>Great idea</td>
  <td>30</td>
</tr>
```

예를 들어 screen reader는 이와 같이 구성된 markup을 인식하고 사용자가 전체 열이나 행을 한 번에 읽을 수 있도록 합니다.

두 가지 가능한 값이 더 있습니다 - colgroup 및 rowgroup. 여러 열이나 여러 행의 맨 위에 있는 제목에 사용됩니다.

### ID 및 header 속성

머리글과 cell을 연결하기 위해 <b style="color: #F2B705;">scope</b> 속성 대신 <b style="color: #F2B705;">id</b>와 <b style="color: #F2B705;">headers</b> 속성을 사용할 수 있습니다.

1. 각 `<th>` 요소에 유니크한 <b style="color: #F2B705;">id</b>를 추가하세요.
2. 각 `<td>` 요소에 <b style="color: #F2B705;">headers</b> 속성을 추가하세요. <b style="color: #F2B705;">headers</b> 속성은 모든 `<th>` 요소에 대한 id 목록을 공백으로 구분하여 포함하고 있습니다.

이는 HTML table에 table의 각 cell 위치에 대한 명시적인 정의를 제공하며, 스프레드시트와 같이 table에 속한 각 열과 행의 header로 정의됩니다. 제대로 작동하려면 테이블에 열과 행, 머리글 모두 필요합니다.

```html
<table>
  <thead>
    <tr>
      <th id="purchase">Purchase</th>
      <th id="location">Location</th>
      <th id="date">Date</th>
      <th id="evaluation">Evaluation</th>
      <th id="cost">Cost (€)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="haircut">Haircut</th>
      <td headers="location haircut">Hairdresser</td>
      <td headers="date haircut">12/09</td>
      <td headers="evaluation haircut">Great idea</td>
      <td headers="cost haircut">30</td>
    </tr>
  </tbody>
</table>
```

결과

<table>
  <thead>
    <tr>
      <th id="purchase">Purchase</th>
      <th id="location">Location</th>
      <th id="date">Date</th>
      <th id="evaluation">Evaluation</th>
      <th id="cost">Cost (€)</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th id="haircut">Haircut</th>
      <td headers="location haircut">Hairdresser</td>
      <td headers="date haircut">12/09</td>
      <td headers="evaluation haircut">Great idea</td>
      <td headers="cost haircut">30</td>
    </tr>
  </tbody>
</table>

> [참고] 이 방법은 header와 데이터 cell 사이에 매우 정확한 연결을 생성하지만 훨씬 더 많은 markup을 사용해서 오류가 발생할 여지가 없습니다. 일반적으로 대부분의 table에는 범위 접근 방식으로 충분합니다.
