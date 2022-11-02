# html_basic

## 글 목록 만들기 예제(추가)
### z-index
```css
.info-background {
    width: 800px;
    margin: auto;
    padding: 20px;
    text-align: center;
    background-color: #eee;
    position: relative;
    top: -100px;
    font-family: sans-serif;
    z-index: 5;
}
```
- floating 되어 있는 개체들의 레이어 순서를 부여해주기 위해 z-index를 사용할 수 있다
- z-index는 클수록 상위 노출이고, 임의의 정수를 사용하면 된다

## 반응형 레이아웃 기초
### 반응형 width, height
```css
.info-background {
    width: 80%;
    max-width: 800px;
    min-width: 600px;
    margin: auto;
    padding: 20px;
    text-align: center;
    background-color: #eee;
    position: relative;
    top: -100px;
    font-family: sans-serif;
    box-sizing: border-box;
}
```
- width 를 부모의 비율로 설정해놓고, max-width/min-width 로 제약을 걸어두면 view port size에 맞게 크기가 조절되는 반응형 개체를 만들 수 있다 > height 도 마찬가지
- width 의 기준은 margin, border, padding을 제외한 content 영역만을 의미한다. 즉, max-width: 600px 이더라도 padding을 주면 눈에 보이는 개체의 크기는 600px 보다 커질 수 있다

### box-sizing
```css
div {
    box-sizing: border-box;
}
```
- width 의 기준을 border line으로 바꾸고 싶을 때는 box-sizing: border-box 를 사용하면 된다
    - (참고) 위 경우는 box-sizing: content-box

## CSS Reset
### 기본 태그 속성 setting
```css
body {
    margin: 0;
}

div {
    box-sizing: border-box;
}

html {
    line-height: 1.15;
}

h1, h2, h3, h4, h5, h6, p {
    margin: 8px;
}

li, a {
    text-decoration: none;
}
```
- default로 적용되어 있는 각 태그의 속성을 css 상단에서 초기화 시켜주고 개발하면 더 편리하게 개발할 수 있다

### CSS normalize
- CSS Normalize 링크 :  https://github.com/necolas/normalize.css/blob/master/normalize.css 
- 크롬, 파이어폭스 등 브라우저마다 호환성 문제로 개체가 다르게 보이는 이슈가 있는데, 이를 해결하기 위해서는 css normalize가 필요하다
- 위 링크의 스타일 시트를 css 상단에 붙여넣거나 새로운 css file로 link 참조해서 사용할 수 있다

## form & input
### form
```html
<body>
    <form action="경로~~" method="post">
        <input>
    </form>
</body>
```
- form tag 안에 input tag를 넣어 입력 개체를 만들 수 있다
    - form action: 작성한 내용이 어떤 서버 경로로 전달될 지 입력
    - form method: 작성한 내용이 어떤 방식으로 서버에 전달될 지 입력

### input type
```html
<body>
    <form>
        <input type="text">
        <input type="email">
        <input type="password">
        <input type="radio">
        <input type="file">
        <input type="checkbox">
        <input type="submit">
        <!-- <button type="submit">전송</button> -->
        <select>
            <option>option 1</option>
            <option>option 2</option>
        </select>
        <textarea rows="10"></textarea>
    </form>
</body>
```
- input type 지정에 따라 용도에 맞는 input box가 자동 생성된다
    - (참고) type="submit" 은 전송 버튼인데, 버튼의 type="submit" 으로도 구현 가능하다
- select 는 dropdown list로 option tab들이 선택지로 보여진다
- textarea는 더 큰 서술형 input box로 default로 보여지는 row 숫자를 지정할 수 있다
    - (참고) 더 많은 type과 속성이 있으므로, 필요할 때마다 찾아서 사용하면 된다

### input 속성들
```html
<body>
    <form>
        <input placeholder="hint text" value="id0000" name="age">
    </form>
</body>
```
- placeholder > input box의 hint text
- value > input box에 미리 입력된 값
- name > 서버 기능 개발에 필요한 input의 이름을 설정

### input 셀렉터 활용
```css
input[type=text] {
    padding: 10px;
}
```
- input tag 중 특정 type만 스타일을 적용하고 싶을 때, html 속성을 css에서 정의하여 지정할 수 있다
