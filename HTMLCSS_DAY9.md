# html_basic

## Font Awesome
### Font Awesome cdnjs
```html
<head>
    <link href="https://cdnjs.cloudflare.com/ajax/libs/font-awesome/6.2.0/css/all.min.css" rel="stylesheet">
</head>
```
- Font Awesome cdnjs 구글링 후 font awesome library cdnjs 페이지 접속하면 all.min.css 의 경로가 있는데 이걸 복붙해서 사용하면 된다
- font-awesome에서 호스팅 해오는 것이기 때문에 속도는 빠르지만, 해당 사이트가 다운되면 사용할 수 없다

### Font Awesome import
```html
<head>
    <link href="fontawesome/css/all.min.css" rel="stylesheet">
</head>
```
- https://fontawesome.com/v5.15/how-to-use/on-the-web/setup/hosting-font-awesome-yourself
- 위와 같이 font awesome 사이트에서 직접 all.min.css file을 다운로드해 import 해주어 사용해도 된다
    - (참고) 다운로드 한 폴더 중 CSS, Webfonts 폴더만 있어도 되며, CSS 폴더 내에서 all.css, all.min.css 이외의 파일은 필요하지 않다

### Font Awesome Icon
```html
<body>
    <i class="fas fa-book fa-2x"></i>
</body>
```
- font awesome x버전 홈페이지의 icon 메뉴로 가서 검색하면 해당 아이콘의 코드를 제공한다
- 여기서 fa-2x 클래스는 사이즈 배율을 변경해준다(2x 는 2배)
- 사이즈나 색 수정은 폰트와 동일하게 할 수 있다


## CSS Animation
### how to create one-way animation
1. 시작 스타일 정하기
2. 최종 스타일 정하기
3. 언제 최종 스타일로 변할지 트리거 설정
4. transition으로 변화 시간 적용
### 시작 / 최종 스타일
```html
<body>
    <div class="container">
        <div class="box">
            <div style="position: relative">
                <div class="overlay"></div>
                <img src="img/product1.jpg">
            </div>
        </div>
        <div class="box">
            <div style="position: relative">
                <div class="overlay"></div>
                <img src="img/product2.jpg">
            </div>
        </div>
    </div>
</body>
```
```css
.container {
    display: flex;
    margin: auto;
}

.box {
    width: 50%;
    margin: 5px;
}

.box img {
    width: 100%;
    display: block;
}

.overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    opacity: 0; /* 시작 스타일: 0, 최종 스타일: 1 */
}
```
- 상품 이미지에 마우스를 올려놓았을 때 반투명 검은색 색상으로 바뀌도록 하기 위해서는 overlay box를 추가해야 한다
    - 가로 정렬을 위해 flex container 안에 2개의 box를 넣어놓았다
    - overlay box를 이미지와 같은 위치에 겹치기 위해 position: relative div로 overlay box + img를 감싸고, overlay에 position: absolute 속성을 추가했다(absolute는 relative 좌표가 기준점임을 이용) 
    - overlay에 rgba(0,0,0,0.5) 로 opacity 50%인 검은색 색상을 적용한다
    - (참고) overlay box와 상품 이미지 하단이 완벽하게 맞지 않는데, 이는 이미지 하단에 자동 여백이 있기 때문이다(?) > display: block을 적용해주면 해결된다
- 시작은 opacity: 0(overlay 안보임), 최종은 opacity: 1 이 된다

### 변화 트리거 설정
```css
.overlay:hover {
    opacity: 1;
}
```
- pseudo-class를 이용해 overlay:hover 시에 opacity: 1(최종 스타일)이 되도록 설정해준다
- 클릭 등의 트리거는 JavaScript를 통해서만 구현할 수 있다

### transition 적용
```css
.overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    opacity: 0; /* 시작 스타일: 0, 최종 스타일: 1 */
    transition: 0.5s; /* 0.5초 동안 변함 */
}
```
- transition에 원하는 변화 소요 시간을 적용한다

### 응용 예제
```css
.box {
    width: 50%;
    margin: 5px;
    overflow: hidden;
}

.overlay {
    position: absolute;
    width: 100%;
    height: 100%;
    background: rgba(0,0,0,0.5);
    top: 100%; /* 시작 스타일: 100%, 최종 스타일: 50% */
    transition: 0.5s; /* 0.5초 동안 변함 */
}

.box:hover .overlay {
    top: 50%;
}
```
- position 위치를 조정해 상품 이미지에 마우스오버 시 overlay box가 아래에서 위로 반절 올라오게도 만들 수 있다
    - 시작 스타일은 overlay top: 100%(이미지 맨 아래), 최종 스타일은 overlay top: 50%(이미지 중간 지점)으로 설정하면 된다
- 여기서 overlay:hover 를 설정하면 "overlay box에 마우스오버 시" 가 트리거 조건이 되므로 상품 이미지 마우스 오버 시에는 동작하지 않는다 > 트리거는 .box:hover 로 "이미지를 감싸는 box 영역에 마우스오버 시"로 설정하되 스타일 변경은 selector를 이용해 .overlay 에 적용되도록 하면 해결할 수 있다
- 마지막으로 이미지 아래로 내려간 overlay box가 보이지 않도록 하기 위해서 overflow: hidden(영역 밖으로 넘어간 부분은 보이지 않게 해주는 속성)를 box 영역에 적용해준다

### 타사이트 애니메이션 확인
- 개발자 툴 > 상단 오른쪽 점 세개 > animation 누르고 사이트에서 animation 요소를 동작시켜 보면 animations 탭에 동작 기록이 남기 때문에 이를 통해 어떤 속성이 몇 초에 걸쳐 변화 되는 지 등에 대한 정보를 알 수 있다
