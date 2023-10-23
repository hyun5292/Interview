※ 모든 기본 내용은 mdn web docs 사이트에서 참고했습니다 ※

[목차]<br/>

- [의사 Class란?](#의사-class란)<br/>
  - [사용자 행동 유사 Class](#사용자-행동-유사-class)<br/>
- [의사 요소란?](#의사-요소란)<br/>
- [의사 Class와 의사 요소들의 혼합](#의사-class와-의사-요소들의-혼합)<br/>

<br/>

# 의사 Class와 의사 요소

<br/>

> [목표] 의사 class와 의사 요소는 여러 개가 있으며, 종종 매우 특정한 목적을 위해 사용됩니다. 사용 방법을 알게 되면 목록을 보고 달성하려는 작업에 적합한 것이 있는지 확인할 수 있습니다.

<br/>

## 의사 Class란?

<b style="color: orange;">의사 Class</b>는 특정 상태에 있는 요소를 선택하는 선택자입니다. 해당 유형의 첫 번쨰 요소이거나 마우스 포인터로 기리키고 있습니다. 마치 문서의 class를 적용한 것처럼 행동하는 경향이 있으며, 종종 markup에서 과도한 class를 줄이는 데 도움이 되고, 더 유연하고 유지관리 가능한 코드를 만들어 줄 수 있습니다.

ex) `:last-child`, `:only-child`, `:invalid`

### 사용자 행동 유사 Class

일부 의사 Class는 사용자가 어떤 방식으로든 문서와 상호 작용할 때만 적용됩니다. <b style="color: orange;">동적 의사 Class</b>라고도 하는 이러한 <b style="color: orange;">사용자 행동 의사 Class</b>는 사용자가 요소와 상호 작용할 때 class가 요소에 추가된 것처럼 작동합니다.

ex) `:hover`, `:focus`

<br/>

## 의사 요소란?

<b style="color: orange;">의사 요소</b>는 유사한 방식으로 동작합니다. 그러나 기존 요소에 class를 적용하는 것이 아니라 완전히 새로운 HTML 요소를 markup에 추가한 것처럼 작동합니다.

의사 요소는 <b>이중 콜론 ::</b>으로 시작합니다.

ex) `::before`

<br/>

## 의사 Class와 의사 요소들의 혼합

첫 번째 단락의 첫 줄을 굵게 만들고 싶다면 `:fist-child`와 `::fist-line` 선택자를 함께 연결할 수 있습니다.

```css
article p:fist-child::first-line {
}
```
