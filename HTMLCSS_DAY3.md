# html_basic

## 글 목록 만들기 예제
### 레이아웃 구축
```html
    <body>
        <div class="container">
            <div class="blog-content">
                <img class="user-img" src="lion.png" width="50px">
                <div class="user-name">
                    <h4 style="margin: 8px;">name</h4>
                    <p style="margin: 8px;">timeframe</p>
                </div>
                <div class="user-content">
                    <h4 style="margin: 8px;">여기는 제목이에요</h4>
                    <p style="margin: 8px;">여기는 내용이에요</p>
                </div>
            </div>
            <div class="blog-img">
                <img src="food.jpg" width="100%">
            </div>
        </div>
    </body>
```
```css
.container {
    width: 800px;
    font-family: sans-serif;
    margin-left: auto;
    margin-right: auto;
}

.blog-img {
    width: 20%;
    height: 200px;
    float: left;
}

.blog-content {
    width: 80%;
    height: 200px;
    float: left;
}

.user-img {
    float: left;
}

.user-name {
    float: left;
}

.user-content {
    clear: both;
}
```
- h4, p 태그는 자동으로 위, 아래 16px margin이 적용되어 있어 필요에 따라 변경해주어야 한다
- user-content 만들 때 바로 위 user-img, user-name class가 floating 상태이므로, user-content clear: both 속성을 적용해주어야 한다
    - (참고) user-content 내의 h4 margin-top 을 적용 시 바로 위 div들이 floating 상태라 floating div 기준으로 margin이 적용되지 않는다 > 더 위 쪽 떠 있지 않은 div 기준으로 margin-top 값을 늘리거나, clear 속성 적용한 dummy div를 하나 더 추가해 해결할 수 있다


### CSS 셀렉터 기초
```html
    <body>
        
        <nav>
            <ul class="navbar">
                <li>영화</li>
                <li>맛집</li>
                <li>IT</li>
                <li>컴퓨터</li>
            </ul>
        </nav>
    </body>
```
```css
.navbar li {
    display: inline-block;
}

.navbar>li {
    display: inline-block;
}
```
- 특정 class 내의 동일한 태그들에 속성을 한꺼번에 지정하는 경우 셀렉터 문법을 사용하여 css 작성할 수 있다
- .class tag {} > class 내의 모든 tag 에 같은 속성 적용
- .class>tag {} > class 내의 직계 자식 tag에만 같은 속성 적용

## background image
### background image 속성
```html
    <body>
        <div class="main-background"></div>
    </body>
```
```css
.main-background {
    width: 100%;
    height: 500px;
    background-image: url(../img/shoes.jpg);
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
}
```
- css background-image 속성을 통해 div에 background image를 삽입할 수 있다
- background-size 는 크기 직접 입력, cover, contain 옵션 등을 선택할 수 있다
    - (참고) cover > div 크기에 꽉 차도록 이미지를 크롭, contain > 이미지가 다 보이도록 div 여백을 남김
- 기본적으로는 background image가 div보다 작은 곳은 이미지를 반복해서 보여준다 > 이를 막기 위해서는 background-repeat: no-repeat
- background-position 은 브라우저 크기 조절 시 이미지 사이즈가 유동적으로 바뀔 때 이미지의 어느 위치를 기점으로 조절할 지 선택하는 속성이다 > center일 경우 브라우저 사이즈를 바꿔도 이미지 중심이 계속 유지된다
- background 이미지 보정 속성도 존재한다

### margin collapse
```html
    <body>
        <div class="main-background">
            <h4 class="main-title">Buy Our Shoes!</h4>
        </div>
    </body>
```
```css
.main-background {
    width: 100%;
    height: 500px;
    background-image: url(../img/shoes.jpg);
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    padding: 1px;
}

.main-title {
    font-size: 64px;
    color: #eee;
    margin-top: 30px;
}
```
- 이미지 안에 h4 텍스트를 넣고 해당 class에(여기서는 main-title) margin-top 조정 시 margin collapse bug 때문에 이미지와 텍스트가 모두 같은 margin을 갖게 된다
- margin collapse는 두 요소의 margin boundary가 맞닿으면 margin 값이 같이 적용되는 bug이다
- margin collapse를 방지하기 위해서는 margin boundary 사이에 작은 여백을 주는 것이 좋다(여기서는 main-background에 1px padding을 적용)

## 좌표 레이아웃
### Position 설정
```html
    <body>
        <div class="main-background">
            <button class="test-btn1">button</button>
            <button class="test-btn2">button</button>
            <button class="test-btn3">button</button>
            <button class="test-btn4">button</button>
        </div>
    </body>
```
```css
.test-btn1 {
    position: relative;
    top: 100px;
    left: 100px;
}

.test-btn2 {
    position: static;
    top: 100px;
    left: 100px;
}

.test-btn3 {
    position: fixed;
    top: 100px;
    left: 100px;
}

.test-btn4 {
    position: absolute;
    top: 100px;
    left: 100px;
}
```
- position 속성을 사용하면 top, left, right, bottom 값으로 개체의 위치를 변경할 수 있고, floating 상태가 된다
- position: relative > 내 현재 위치를 기준으로 top~~ 값을 상대적으로 적용, 또한 relative 속성을 가진 개체가 자식 개체의 기준점이 된다
- position: static > top~~ 값을 적용해도 포지션을 변경하지 않도록 해준다
- position: fixed > view port(현재 보여지는 브라우저) 기준으로 절대 위치를 적용, 즉 view port size 변경 혹은 스크롤 시에도 개체가 같은 곳에 위치한다(상단 navbar, 하단 플로팅 버튼 등에 활용)
- position: absolute > relative 속성을 가진 부모 개체의 위치를 기준으로 상대적인 top~~ 값이 적용된다

### position: absolute 적용한 개체 가운데 정렬
```css
.test-btn {
    position: absolute;
    left: 0;
    right: 0;
    margin-left: auto;
    margin-right: auto;
    width: 100px; /* 아무 값이나 적당히 넣어주면 됨 */
}
```
- 5개 속성을 통해 position: absolute 상태에서 개체 가운데 정렬 해줄 수 있다

