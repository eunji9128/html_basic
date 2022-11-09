# html_basic

## Pseudo-class
### interactive button
```css
.btn:hover {
    background: chocolate;
}

.btn:focus {
    background: red;
}

.btn:active {
    background: brown;
}
```
- pseudo-class selector를 적용하면 여러 상태에 따른 스타일을 지정해줄 수 있다
    - hover: 마우스를 올려 놓았을 때
    - focus: 클릭 후 계속 포커스 상태 일 때(다른 곳을 클릭하면 focus 상태 해제)
    - active: 클릭 중 일 때
- 위 상태에 스타일을 넣을 때는 hover > focus > active 순서대로 css에 선언해줘야 잘 동작한다

### 다양한 pseudo-class
```css
input:focus {
    border: 2px solid red;
}

a:link {
    color: red; /* 방문 전 링크 색상 */
}

a:visited {
    color: black; /* 방문 후 링크 색상 */
}
```
```css
:any-link /* 방문 전, 방문 후 링크 한 번에 선택할 때 */
:playing /* 동영상, 음성이 재생 중 일 때 */
:paused /* 동영상, 음성이 정지 시 */
:autofill /* input의 자동채우기 스타일 */
:disabled /* disable된 요소 스타일 */
:checked /* 체크박스나 라디오버튼 체크되었을 때 */
:blank /* input이 비었을 때 */
:valid /* 이메일 input 등이 이메일 형식에 맞을 경우 */
:invalid /* 이메일 input 등이 이메일 형식에 맞지 않을 경우 */
:required /* 필수로 입력해야 할 input의 스타일 */
:nth-child(n) /* n번째 자식 선택 */
:first-child /* 첫번째 자식 선택 */
:last-child /* 마지막 자식 선택 */
```
- 더 많은 pseudo-class: https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes


## CSS 작성 방식
### OOCSS(Object Oriented CSS)
```css
/* Non-OOCSS */
.main-btn-red {
    font-size: 20px;
    padding: 15px;
    border: none;
    cursor: pointer;
    background: red;
}

.main-btn-blue {
    font-size: 20px;
    padding: 15px;
    border: none;
    cursor: pointer;
    background: blue;
}

/* OOCSS */
.main-btn {
    font-size: 20px;
    padding: 15px;
    border: none;
    cursor: pointer;
}

.bg-red {
    background: red;
}

.bg-blue {
    background: blue;
}
```
```html
<!-- OOCSS -->
<button class="main-btn bg-red">빨간 버튼</button>
<button class="main-btn bg-blue">파란 버튼</button>
```
- OOCSS는 뼈대 스타일과 살을 붙이는 스타일을 각 class로 분리하는 방식을 의미한다
- OOCSS의 장점은
    1. 중복된 스타일을 재사용 할 수 있다
    2. 유지보수가 편리해진다(같은 스타일을 변경할 때 하나의 class만 수정하면 되므로)
    3. 코드 작성 효율이 증가한다(자주 사용하는 class를 미리 만들어두면(=utility class) html에서 붙여 사용만 하면 되므로)

### BEM(Block__Element--Modifier)
```html
<body>
    <div class="profile">
        <img class="profile__img">
        <h4 class="profile__h4">이름</h4>
        <p class="profile__content">소개글</p>
        <button class="profile__button--red">빨간 버튼</button>
        <button class="profile__button--blue">파란 버튼</button>
</body>
```
- class 작명을 도와주는 방법으로 Block, Element, Modifier 을 활용한 네이밍 룰이다
    - Block > 큰 컴포넌트의 기능/특징
    - Element > HTML의 요소(element)
    - Modifier > 수식어, 세부 특징
- OOCSS나 BEM은 전통적인 html, css를 사용할 때 유용하며, React, Vue 등을 이용할 때는 크게 사용하진 않는다 > React 에서는 html 단위가 아닌 component 단위로 개발하며 component 간 class가 중복되어도 간섭되지 않도록 해줄 수 있다(styled-components)

