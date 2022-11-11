# html_basic

## 반응형 레이아웃
### 크기 단위
```css
.box {
    width: 16px; /* 기본 pixel 단위 */
    width: 50vw; /* 브라우저 viewport width의 50% */
    width: 50vh; /* 브라우저 viewport height의 50% */
    width: 1.5rem; /* html 태그 혹은 기본 폰트 사이즈의 1.5배 */
    width: 2em; /* 내 폰트 사이즈 혹은 상위 요소 폰트 사이즈의 2배 */
}
```
- 예전에는 시스템 설정에서 font size를 변경할 경우 font만 커지고 버튼이나 박스는 그대로 있어 웹페이지 레이아웃이 깨지는 문제가 있어 rem 단위를 사용했었다 > 지금은 대부분 ctrl + mouse wheel 로 zoom in/out을 하기 때문에 사용할 일이 없다
- typography 할 때 폰트를 px 단위로 외우기 귀찮을 때 em 단위로 외우면 편리할 수 있다

### media query
```html
<head>
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
</head>
```
```css
@media screen and (max-width: 1200px) {
    .box {
        font-size: 40px;
    }
    .box2 {
        font-size: 20px;
        width: 50%;
    }
}

@media screen and (max-width: 768px) {
    .box {
        font-size: 20px;
    }
}
```
- viewport size에 따라 클래스 스타일을 유동적으로 변경하기 위해서는 1) head tag 에 viewport meta data 선언을 해주고, 2) media query를 사용하면 된다
- media query는 각 조건에 따라 (여기서는 max-width) 여러 개 만들 수 있으며, query문 안에서도 여러 클래스를 변경할 수 있다
    - (참고) 클래스 스타일의 변경은 아니고 추가해주는 개념(가장 하단 스타일을 최종 적용하므로)

### 권장 breakpoint
- max-width 를 1200, 768px가 기준 breakpoint인데, 이는 권장하는 숫자를 기준으로 삼는 것이 좋다
    - Bootstrap Lib recommendation: 1200px / 992px / 768px / 576px
    - 1200px은 태블릿 기준, 나머지는 모바일 기준
- breakpoint 4개 이상 만들면 복잡성이 올라가므로, 3개 정도를 권장한다


## CSS debugging
### Chrome
- 웹 브라우저에서 우클릭 > 검사(inspect) or F12 > 상단 왼쪽 검사 아이콘 눌러 원하는 영역 html, 스타일 요소를 확인할 수 있다
- Elements 탭에서는 html, 아래 Styles 탭에서는 적용된 css 스타일을 확인할 수 있다
    - Styles 탭에서 상단에 위치한 스타일이 우선 순위가 높은 스타일이다
    - Styles 탭의 element.style 은 html에서 style 속성을 부여한 것을 의미한다
    - Styles 탭에서 밑줄 쳐진 스타일은 적용되지 않았다는 걸 의미한다

### IE
- 마찬가지로 우클릭 > 검사를 통해 확인할 수 있다
- 에뮬레이터(Emulator) 탭에서 IE 버전을 변경해볼 수 있다

### IE 호환성
```html
<head>
    <link href="css/main.css" rel="stylesheet">
    <!--[if lt IE 10]>
    <link href="css/ie.css" type="text/css"
    rel="stylesheet"/>
    <![endif]-->
</head>
<body>
    <div class="nav-bar ie-nav">
</body>
```
- IE 구버전에서 스타일 호환이 잘 되는 웹페이지를 만들기 위해서는 IE 구버전 CSS 파일을 따로 만들어서 조건문 안에 넣어주면 된다
- 구버전 CSS class를 적용시켜 줄 때 ie-nav 등 유틸리티로 만들어 적용 시켜주면 다른 스타일에 영향을 주지 않고 호환성을 높일 수 있다
