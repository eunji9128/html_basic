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
