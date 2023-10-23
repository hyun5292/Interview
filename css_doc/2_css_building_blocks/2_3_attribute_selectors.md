※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [존재 및 값 선택자](#존재-및-값-선택자)<br/>
- [하위 문자열 일치 선택자](#하위-문자열-일치-선택자)<br/>
- [대소문자 구분](#대소문자-구분)<br/>

<br/>

# 속성 선택자

<br/>

> [목표] HTML에 대한 연구에서 알 수 있듯이, 요소에는 markup되는 요소에 대한 자세한 정보를 제공하는 속성이 있을 수 있습니다. <b>CSS에서는 속성 선택자를 사용하여 특정 속성이 있는 요소를 대상으로 지정할 수 있습니다. 이 과정에서는 이러한 매우 유용한 선택자를 사용하는 방법을 보여줍니다.</b>

<br/>

## 존재 및 값 선택자

이러한 선택기는 속성의 존재 여부 또는 속성 값에 대한 다양한 일치 항목을 기준으로 요소를 선택할 수 있습니다.

| 선택자        | 예시                          | 설명                                                                                                                                 |
| ------------- | ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------ | ------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| [attr]        | a[title]                      | <b style="color: F2B705;">attr</b> 속성이 있는 요소와 일치합니다.                                                                    |
| [attr=value]  | a[href="https://example.com"] | 값이 정확히 value인 <b style="color: F2B705;">attr</b> 속성이 있는 요소와 일치합니다.                                                |
| [attr~=value] | p[class~="special"]           | 값이 정확히 value이거나 (공백으로 구분된) 값 목록에 value가 포함된 <b style="color: F2B705;">attr</b> 속성이 있는 요소와 일치합니다. |
| [attr         | =value]                       | div[lang                                                                                                                             | ="zh"] | 값이 정확히 value이거나 바로 뒤에 하이폰이 오는 value로 시작하는 <b style="color: F2B705;">attr</b> 속성이 있는 요소와 일치합니다. |

<br/>

## 하위 문자열 일치 선택자

이러한 선택자는 속성 값 내에서 하위 문자열의 고급 일치를 허용합니다.

| 선택자        | 예시              | 설명                                                                                                  |
| ------------- | ----------------- | ----------------------------------------------------------------------------------------------------- |
| [attr^=value] | li[class^="box-"] | 값이 value로 시작하는 <b style="color: F2B705;">attr</b> 속성이 있는 요소와 일치합니다.               |
| [attr$=value] | li[class$="-box"] | 값이 value로 끝나는 <b style="color: F2B705;">attr</b> 속성이 있는 요소와 일치합니다.                 |
| [attr*=value] | li[class*="box"]  | 값이 문자열 내에서 value를 포함하는 <b style="color: F2B705;">attr</b> 속성이 있는 요소와 일치합니다. |

<br/>

## 대소문자 구분

대소문자를 구분하지 않고 속성 값을 일치 시키려면 닫는 괄호 앞에 <b style="color: F2B705;">i</b> 값을 사용할 수 있습니다. 이 flag는 대소문자를 구분하지 않고 ASCII 문자와 일치하도록 browser에 지시합니다. flag가 없으면 문서 언어의 대소문자 구분에 따라 값이 일치합니다 - HTML의 경우 대소문자를 구분합니다.

```css
li[class^="a"] {
  background-color: yellow;
}

li[class="a", i] {
  color: red;
}
```

```html
<h1>Case-Insensitivity</h1>
<ul>
  <li class="a">Item 1</li>
  <li class="A">Item 2</li>
  <li class="Ab">Item 3</li>
</ul>
```

결과

<!DOCTYPE>
<html>
<head>
	<style>
		li[class^="a"] {
			background-color: yellow;
		}
    li[class^="a" i] {
    	color: red;
    }
  </style>
  <title>선택자 대소문자 구분</title>
</head>
<body>
	<h1>Case-Insensitivity</h1>
	<ul>
		<li class="a">Item 1</li>
		<li class="A">Item 2</li>
		<li class="Ab">Item 3</li>
	</ul>
</body>
</html>
