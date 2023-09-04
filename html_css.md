<h1 style="color:orange">
	면접 질문 - HTML & CSS
</h1>

<details>
<summary> 
	<h1>
		px, em, rem 의 차이에 대해 설명해주세요.
	</h1>
</summary>
<div markdown="1">
	[참고] https://rypro.tistory.com/184
	<h2>
		<ul>
			<li>
				대부분 rem을 사용
			</li>
			<li>
				em과 달리 rem을 사용하면 크기의 			예측이 	훨씬 쉬움
			</li>
			<li>
				component의 재사용과 유지보수가 쉬움
			</li>
			<br/>
			<ul>
				<li>
					px<br/>: 모니터에 상대적인 크기
				</li>
				<li>
					em<br/>: 부모 요소의 크기
				</li>
				<li>
					rem<br/>: root 요소의 크기
				</li>
			</ul>
		</ul>
	</h2>
</div>
</details>

<br/>

<details>
<summary>
	<h1>
		반응형 브레이크 포인트는 보통 어떻게 잡으시나요?
	</h1>
</summary>
<div markdown="1">
	[참고] https://mu08.tistory.com/32
	<h2>
		<ul	>
			<li>
				브레이크 포인트<br />: 사용자들의 스크린 가로 사이즈가 몇 px인지에 따라 보여줄 내용을 변경 시키는 지점
			</li>
			<li>
				360px, 768px, 1024px
			</li>
		</ul>
	</h2>
</div>
</details>

<br/>

<details>
<summary>
	<h1>
		CSS 선택자의 우선순위(Cascading)에 대해 설명해주세요.
	</h1>
</summary>
<div markdown="1">
	[참고] https://velog.io/@ewaterbin/02.-CSS-Selector
	<h2>
		<ol>
			<li>
				후자 우선의 원칙<br />: 동일한 선택자가 연속으로 사용되었을 경우 후자가 우선
			</li>
			<br/>
			<li>
				구체성의 원칙<br />: 더 구체적인 속성을 가진 값이 우선
				<br/><br/>
				<div>2.1 가중치</div>
				<ul>
					<li>
						인라인 선언<br/>: 1000점
					</li>
					<li>
						id 선택자<br/>: 100점
					</li>
					<li>
						class 선택자, 가상클래스ex, :hover())<br/>: 10점
					</li>
					<li>
						태그 선택자<br/>: 1점
					</li>
					<li>
						전체 선택자(*), 부정 선택자ex, :not())<br/>: 0점
					</li>
				</ul>
			</li>
			<br/>
			<li>
				중요성의 원칙<br/>
				<ul>
					<li>!important<br/>: 절대적 우선순위</li>
					<ul><li>같은 !important 사이에서는 가중치를 계산해서 적용</li></ul>
				</ul>
			</li>
		</ol>
  </h2>
</div>
</details>

<br/>

<details>
<summary>
	<h1>
		페이지 크기가 변해도 항상 같은 비율을 유지하는 요소를 만들려면 CSS를 어떻게 설정해야될까요?
	</h1>
</summary>
<div markdown="1">
	[참고] https://velog.io/@dnr6054/fe-interview-html-css
	<h2>
		: 고정해야 하는 위치에 따라 margin, padding, width, height 등에 % 단위를 사용할 수 있음.
  </h2>
</div>
</details>

<br />

<details>
<summary>
	<h1>
		Flexbox에 대해 설명해주세요.
	</h1>
</summary>
<div markdown="1">
	[참고] https://developer.mozilla.org/ko/docs/Web/CSS/CSS_flexible_box_layout/Basic_concepts_of_flexbox
	<h2>
		: 인터페이스 내의 아이템 간 공간 배분을 정렬하기 위해 제공된 1차원 레이아웃 모델
		<ul>
			<li>1차원적으로 한 번에 하나의 행 또는 열 만을 다룸
			</li>
			<br/>
			<li>
				Grid와 차이점<br/>: Grid는 	2차원적으로 행과 열을 동시에 다룸
			</li>
		</ul>
  </h2>
</div>
</details>

<br />

<details>
<summary>
	<h1>
		Float의 동작에 대해 설명해주세요.
	</h1>
</summary>
<div markdown="1">
	[참고] https://velog.io/@nalsae/내보정CSS-float-딥-다이브
	<h2>
		: 텍스트와 이미지를 적절하게 배치하는 도구
		<ul>
			<li>
				normal flow < float < position 순서로 위로 붕 뜸
			</li>
			<br/>
			<li>
				float가 적용된 element는 normal flow에서 벗어나기 때문에 예기치 못한 이슈들이 많음
				<ul>
					<li>
						ex, 자식 요소들이 전부 float이면 부모 요소의 크기가 0으로 사라짐
					</li>
					<li>
						해결방법, overflow, flow-root, clear 등 사용하기
					</li>
				</ul>
			</li>
		</ul>
  </h2>
</div>
</details>

<br />

<details>
<summary>
	<h1>
		SCSS에 대해 설명해주세요.
	</h1>
</summary>
<div markdown="1">
	[참고] https://velog.io/@jch9537/CSS-SCSS-SASS
	https://heewon26.tistory.com/360
	<h2>
	: 확장판 CSS 스크립트 언어
		<ul>
			<li>
				프로젝트가 커지면서 복잡해지는 CSS 작업을 쉽게 해주며 가독성과 재사용성을 높여주어 유지보수가 쉬워지도록 도와줌
			</li>
			<li>
				장점
				<ul>
					<li>변수 사용</li>
					<li>조건문과 반복문</li>
					<li>Import</li>
					<li>Nesting</li>
					<li>Mixin</li>
					<li>Extend/Inheritance</li>
				</ul>
			</li>
			<li>SASS보다 SCSS가 뒤에 나왔고 여러가지 문법의 차이가 있지만 SCSS가 더 넓은 범용성과 CSS의 호환성 등의 장점으로 SCSS를 사용하기를 권장함</li>
			<li>
				SASS
				<ul>
					<li>
						{}(중괄호), ;(세미콜론) 비사용
					</li>
					<li>
						mixin을 +으로 정의하고 =로 사용
					</li>
				</ul>
			</li>
			<li>
				SCSS
				<ul>
					<li>
						{}(중괄호), ;(세미콜론) 사용
					</li>
					<li>
						mixin을 @mixing으로 정의하고 @include로 사용
					</li>
				</ul>
			</li>
		</ul>
  </h2>
</div>
</details>

<br />

<details>
<summary>
	<h1>
		Position 속성에 대해 설명해주세요.
	</h1>
</summary>
<div markdown="1">
	[참고] https://www.daleseo.com/css-position/
	<h2>
		: element를 배치하는 방식을 결정, top, bottom, right, left 속성과 함께 사용됨
		<ul>
			<li>
				static<br/>: 기본값 HTML 문서 상에서 원래 있어야 하는 위치에 배치 
			</li>
			<li>
				relative
			</li>
			<li>
				absolute
			</li>
			<li>
				fixed
			</li>
		</ul>
  </h2>
</div>
</details>

<br />

<details>
<summary>
	<h1></h1>
</summary>
<div markdown="1">
	<h2>
		<ul>
			<li></li>
			<li></li>
			<li></li>
		</ul>
  </h2>
</div>
</details>

<br />

<details>
<summary>
	<h1></h1>
</summary>
<div markdown="1">
	<h2>
		<ul>
			<li></li>
			<li></li>
			<li></li>
		</ul>
  </h2>
</div>
</details>

<br />

<details>
<summary>
	<h1></h1>
</summary>
<div markdown="1">
	<h2>
		<ul>
			<li></li>
			<li></li>
			<li></li>
		</ul>
  </h2>
</div>
</details>

<br />

<details>
<summary>
	<h1></h1>
</summary>
<div markdown="1">
	<h2>
		<ul>
			<li></li>
			<li></li>
			<li></li>
		</ul>
  </h2>
</div>
</details>

<br />

[Up](#)
