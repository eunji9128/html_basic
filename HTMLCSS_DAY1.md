# html_basic

## HTML 기본 태그 사용
### 기본 태그 목록
```html
<p>Paragraphs</p>
<h1>Heading 1</h1>
<img src="image link address">
<a href="link address">Hyper link</a>
<button>Button</button>
<ul> <!-- Unordered List -->
    <li>List Item</li>
</ul>
<ol> <!-- Ordered List -->
    <li>List Item</li>
</ol>
```

### 태그 활용
1. <tag></tag> 사이에 글, 이미지 등을 삽입할 수 있다
2. 특정 태그는 <tag >안에 속성을 추가할 수 있다
3. <tag1><tag2></tag2></tag1> 처럼 태그 안에 다른 태그를 삽입할 수 있다
> <p></p> 태그를 버튼처럼 만들어도 되지만, 마크업 언어는 자료의 구조를 쉽게 파악하기 위한 언어이기 때문에 용도에 맞는 태그를 사용해 '웹 표준'에 맞는 웹을 만드는 것이 중요하다

### 기본 HTML 스타일링
```html
<body>
    <img src="lion.png" style="width: 100%; display: block; margin-left: auto; margin-right: auto">
    <h3 style="font-size: 16px; font-family: 'gulim'; color: blue; letter-spacing: -1px; text-align: center">Harry</h3>
    <p><span style="font-weight: 900">Front-end</span> <strong>Developer</strong></p>
</body>
```
- 태그에 style="" 속성을 삽입해 스타일링이 가능하다
- width: 100% 의 % 단위는 부모 태그 사이즈(=body)에 비례(감싸고 있는 태그가 부모 태그, 감싸져 있는 태그가 자식 태그)
- display: block; margin-left: auto; margin-right > 이미지 브라우저의 자동 가운데 정렬
- font-size도 px 뿐 아니라 다른 단위도 설정 가능(예를 들어 vw(=현재 브라우저 창의 너비))
- font-family > 글꼴, letter-spacing > 자간 간격, text-align: center > 글자 브라우저의 자동 가운데 정렬
- 특정 글자만 style 변경하고 싶으면 span 태그로 분리, span 태그는 글자를 감쌀 수 있는 특정 용도가 정해지지 않은 태그
    - 참고) span 태그는 display: inline 이라는 속성을 내포하므로 이 속성을 내포한 요소는 폭, 높이 등을 단독으로 결정하지 못한다. 따라서 폭, 높이를 조정하고 싶으면 span을 감싸고 있는 태그(여기서는 p)에 style 추가해야 한다.
- Bold 처리는 두 가지로 가능, font-weight 조정 or strong 태그 사용


## CSS 기본 사용
### CSS 파일 사용
```html
<head>
    <meta charset="UTF-8">
    <title>Document</title>
    <link href="css/main.css" rel="stylesheet">
</head>
```
- CSS 파일을 사용하기 위해서는 head 내에 link 태그로 css 파일을 연결해줘야 한다
- CSS는 Cascading Style Sheet로 스타일 보관 파일

```css
.profile {
    width: 100px;
    display: block;
    margin-left: auto;
    margin-right: auto;
}
```
- CSS 파일 내에 profile 이라는 class 를 위와 같이 만들어 스타일을 지정해줄 수 있다

```html
<body>
    <img src="lion.png" class="profile">
</body>
```
- 지정한 스타일을 적용하려면 html 파일에서 class 속성을 이용해 삽입하면 된다

```css
p {
    text-align: center;
}
```
- . 없이 태그명을 적어 태그에 공통된 스타일을 지정해줄 수 있다

```css
#special {
    text-align: center;
}
```
- html에서 id를 사용한 태그(여기서는 id="special")의 스타일은 #을 붙여 지정할 수 있다
- .profile p #special 은 selector 라고 부른다 > class selector, tag selector, id selector
- 각 selector가 중복될 경우 우선 순위는 style > id > class > tag(예를 들어 모두 color 지정이 되어 있고 한 태그가 모든 selector 중복 사용될 경우, html의 style 속성이 최종적으로 적용)
