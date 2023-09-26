※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- []()<br/>

<br/>

# HTML table 기초

> [목표] HTML에서 매우 일반적인 작업으로, 표 형식의 데이터를 구조화하는 것이며, 이 목적을 위해 여러 요소와 속성을 가지고 있습니다. styling을 위해 약간의 CSS와 HTML을 함께 사용하면 web 테이블 정보를 쉽게 표시할 수 있습니다. <b>이 글은 HTML을 사용하여 표 형식의 데이터를 구성하는데 필요한 모든 정보를 제공합니다.</b>

> [목표] <b>이 문서에서는 행, 셀, 제목, 여러 열과 행에 걸쳐 셀을 만드는 방법, 스타일 지정 목적으로 열의 모든 셀을 그룹화하는 방법과 같은 기본 사항을 다루며, HTML 테이블을 시작하는 방법을 안내합니다.</b>

## 언제 HTML table을 사용하지 말아야 하나요?

HTML table은 표 형식의 데이터에 사용해야 합니다. 예전에는 browser 전반의 CSS 지원이 형편없었기 때문에 table layout이 일반적으로 사용되었습니다.

CSS 레이아웃 기법 대신 table을 layout에 사용하는 것은 좋지 않습니다. 주된 이유는 다음과 같습니다.

1. layout table은 시각 장애가 있는 사용자의 접근성을 떨어트립니다.
2. table에서 태그 수프 생성
   : table layout은 일반적으로 적절한 layout 기술보다 더 복잡한 markup 구조를 포함합니다. 이로 인해 코드 작성, 유지 관리 및 디버깅이 어려워질 수 있습니다.
3. table이 자동으로 반응하지 않습니다.
   : 적절한 layout container를 사용하는 경우 너비는 기본적으로 상위 요소의 100%가 됩니다. 반면에 table은 기본적으로 content에 따라 크기가 조정되므로 다양한 기기에서 효과적으로 작동하는 table layout 스타일을 얻으려면 추가 조치가 필요합니다.

<br/>

## `<th>` 요소로 header 추가하기

행이나 열의 시작 부분에 위치하여 해당 행이나 열에 포함된 데이터 유형을 정의하는 특수 cell인 table header에 대해 살펴보겠습니다.

```html
<table>
  <tr>
    <td>&nbsp;</td>
    <td>Knocky</td>
    <td>Flor</td>
    <td>Ella</td>
    <td>Juan</td>
  </tr>
  <tr>
    <td>Breed</td>
    <td>Jack Russell</td>
    <td>Poodle</td>
    <td>Streetdog</td>
    <td>Cocker Spaniel</td>
  </tr>
  <tr>
    <td>Age</td>
    <td>16</td>
    <td>9</td>
    <td>10</td>
    <td>5</td>
  </tr>
  <tr>
    <td>Owner</td>
    <td>Mother-in-law</td>
    <td>Me</td>
    <td>Me</td>
    <td>Sister-in-law</td>
  </tr>
  <tr>
    <td>Eating Habits</td>
    <td>Eats everyone's leftovers</td>
    <td>Nibbles at food</td>
    <td>Hearty eater</td>
    <td>Will eat till he explodes</td>
  </tr>
</table>
```

결과

<table>
  <tr>
    <td>&nbsp;</td>
    <td>Knocky</td>
    <td>Flor</td>
    <td>Ella</td>
    <td>Juan</td>
  </tr>
  <tr>
    <td>Breed</td>
    <td>Jack Russell</td>
    <td>Poodle</td>
    <td>Streetdog</td>
    <td>Cocker Spaniel</td>
  </tr>
  <tr>
    <td>Age</td>
    <td>16</td>
    <td>9</td>
    <td>10</td>
    <td>5</td>
  </tr>
  <tr>
    <td>Owner</td>
    <td>Mother-in-law</td>
    <td>Me</td>
    <td>Me</td>
    <td>Sister-in-law</td>
  </tr>
  <tr>
    <td>Eating Habits</td>
    <td>Eats everyone's leftovers</td>
    <td>Nibbles at food</td>
    <td>Hearty eater</td>
    <td>Will eat till he explodes</td>
  </tr>
</table>

### header가 유용한 이유는 무엇인가요?

header가 명확하게 눈에 띄고 디자인이 일반적으로 더 보기 좋으면 원하는 데이터를 더 쉽게 찾을 수 있습니다.

table header에는 다음과 같은 추가 이점도 있습니다. scope 특성과 함께 사용하면 각 header를 동일한 행 또는 열의 모든 데이터와 연결하여 테이블에 대한 접근성을 높일 수 있습니다. 그러면 screen reader가 데이터의 전체 행이나 열을 한 번에 읽을 수 있으므로 매우 유용합니다.

<br/>

## Cell이 여러 행과 열에 걸쳐 있도록 허용하기

cell이 여러 행이나 열에 걸쳐 있어야 할 때가 있습니다.

```html
<table>
  <tr>
    <th>Animals</th>
  </tr>
  <tr>
    <th>Hippopotamus</th>
  </tr>
  <tr>
    <th>Horse</th>
    <td>Mare</td>
  </tr>
  <tr>
    <td>Stallion</td>
  </tr>
  <tr>
    <th>Crocodile</th>
  </tr>
  <tr>
    <th>Chicken</th>
    <td>Hen</td>
  </tr>
  <tr>
    <td>Rooster</td>
  </tr>
</table>
```

결과

<table>
  <tr>
    <th>Animals</th>
  </tr>
  <tr>
    <th>Hippopotamus</th>
  </tr>
  <tr>
    <th>Horse</th>
    <td>Mare</td>
  </tr>
  <tr>
    <td>Stallion</td>
  </tr>
  <tr>
    <th>Crocodile</th>
  </tr>
  <tr>
    <th>Chicken</th>
    <td>Hen</td>
  </tr>
  <tr>
    <td>Rooster</td>
  </tr>
</table>

하지만 결과물은 우리가 원하는 대로 나오지 않습니다.

"Animals", "Hippopotamus", "Crocodile"은 두 열에 걸쳐, "Horse"와 "Chicken"은 두 행에 걸쳐 아래로 내려가도록 하는 방법이 필요합니다. 다행히 table header와 cell에는 이러한 작업을 수행할 수 있는 <b style="color: #F2B705;">colspan</b> 및 <b style="color: #F2B705;">rowspan</b> 특성이 있습니다. 두 특성 모두 span 하려는 행 또는 열의 수와 같은 단위가 없는 숫자 값을 허용합니다.

<br />

## 열에 공통 스타일 제공

### `<col>` 없이 styling 하기

HTML에는 데이터 열 전체에 대한 스타일 정보를 한 곳에서 정의하는 방법, 즉 `<col>` 및 `<colgroup>` 요소가 있습니다. 열에 스타일을 지정하는 것이 다소 번거롭고 비효율적일 수 있기 때문에 이러한 기능이 존재합니다. 일반적으로 열의 모든 `<td>` 또는 `<th>`에 styling 정보를 지정하거나 <b style="color: #F2B705;">:nth-child</b>와 같은 복잡한 선택기를 사용해야 합니다.

```html
<table>
  <tr>
    <th>Data 1</th>
    <th style="background-color: yellow">Data 2</th>
  </tr>
  <tr>
    <td>Calcutta</td>
    <td style="background-color: yellow">Orange</td>
  </tr>
  <tr>
    <td>Robots</td>
    <td style="background-color: yellow">Jazz</td>
  </tr>
</table>
```

결과

<table>
  <tr>
    <th>Data 1</th>
    <th style="background-color: yellow">Data 2</th>
  </tr>
  <tr>
    <td>Calcutta</td>
    <td style="background-color: yellow">Orange</td>
  </tr>
  <tr>
    <td>Robots</td>
    <td style="background-color: yellow">Jazz</td>
  </tr>
</table>

열의 세 셀 모두에 styling 정보를 반복해야 하므로 이상적이지 않습니다.

### `<col>`을 사용한 styling

`<col>` 요소에 정보를 한 번에 지정할 수 있습니다. `<col>` 요소는 여는 `<table>` 태그 바로 아래의 `<colgroup>` container 안에 지정됩니다.

```html
<table>
  <colgroup>
    <col />
    <col style="background-color: yellow" />
  </colgroup>
  <tr>
    <th>Data 1</th>
    <th>Data 2</th>
  </tr>
  <tr>
    <td>Calcutta</td>
    <td>Orange</td>
  </tr>
  <tr>
    <td>Robots</td>
    <td>Jazz</td>
  </tr>
</table>
```

결과

<table>
  <colgroup>
    <col />
    <col style="background-color: yellow" />
  </colgroup>
  <tr>
    <th>Data 1</th>
    <th>Data 2</th>
  </tr>
  <tr>
    <td>Calcutta</td>
    <td>Orange</td>
  </tr>
  <tr>
    <td>Robots</td>
    <td>Jazz</td>
  </tr>
</table>

사실상 두 개의 스타일 열을 정의하고 있는데, 하나는 각 열에 대한 스타일 정보를 제공합니다. 첫 번째 스타일을 지정하지 않지만 `<col>` 요소를 포함해야 합니다. 두 열 모두에 styling 정보를 적용하려면 `<col>` 요소를 하나만 포함하면 됩니다.

<b style="color: #F2B705;">colspan</b> 및 <b style="color: #F2B705;">rowspan</b>과 마찬가지로 span은 스타일을 적용할 열의 개수를 지정하는 단위가 없는 숫자 값을 받습니다.
