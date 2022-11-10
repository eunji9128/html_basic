# html_basic

## Font 설정
### font-family
```css
@font-face {
    font-family: 'nanumsquare'; /* font name 작명 */
    src: url(../font/NanumSquareR.ttf);
}

@font-face {
    font-family: 'nanumsquare';
    font-weight: 800;
    src: url(../font/NanumSquareB.ttf)
}

body {
    font-family: 'nanumsquare', 'gulim', 'dotum'; /* nanumsquare Regular 적용 */
}

h4, h3, h2, h1 {
    font-weight: 800;
    font-family: 'nanumsquare'; /* nanumsquare bold 적용 */
}
```
- font-family 속성을 통해 font 변경을 할 수 있으며, font의 영문 이름을 사용해야 버그 없이 적용할 수 있다
- font-family 적용 시에 여러 font를 적용하면 첫번째 font에서 에러가 나도, 두번째 세번째 폰트가 적용되어 안정성을 높일 수 있다
- custom font 적용을 위해서는 @font-face 명령어를 사용할 수 있다
    - 폴더 내에 font file을 저장해주어야 한다
- regular font에 직접 font-weight를 크게 주어 bold체로 사용할 수도 있지만, 그것보다 bold font를 font-face로 등록해 사용하는 것이 더 매끄러운 bold font를 출력해준다
    - font-face에서 같은 이름으로 regular, bold font를 등록하고, tag 스타일에서 font-face에서 등록한 조건을 같게 적어주면 각각 맞는 font가 적용된다(위에서는 font-weight: 800, font-family: nanumsquare 스타일 적용 시 NanumSquareB 가 적용)
- 한글 font는 용량이 크기 때문에 1~2개 정도만 사용하는 것이 좋다

### woff for web
```css
@font-face {
    font-family: 'nanumsquare';
    src: url(../font/NanumSquareR.woff)
}

/* IE 호환성 */
@font-face {
    font-family: 'nanumsquare';
    src: url(NanumSquareR.eot);
    src: url(NanumSquareR.eot?#iefix) format('embedded-opentype'),
        url(NanumSquareR.woff) format('woff'),
        url(NanumSquareR.ttf) format('truetype');
}
```
- tff는 용량이 커 랜더링 속도에 영향을 미칠 수 있으므로, web에 사용할 폰트는 woff 타입을 사용하는 것이 좋다
- IE7,8 등 오래된 버전에서도 호환성을 지키기 위해서는 아래 명시된 것처럼 eot, woff, ttf 타입을 모두 구해 font-face 등록을 해주면 된다

### Google-Font
- 구글폰트에서는 다양한 font를 호스팅 해주어 font 저장 없이 사용할 수 있다
- HTML에 첨부하고 싶다면 구글 폰트 사이트에서 제공해주는 link tag를 CSS에 첨부하고 싶다면 @import 코드를 복사해서 각 파일에 맞게 복붙해서 사용하면 된다
- 구글이 호스팅해주는 font가 미리 정의된 css 파일을 가져다 쓰는 것이라 내 사이트의 트래픽을 절약할 수 있고(왜?), 크롬 브라우저는 이미 방문한 사이트는 캐싱해주기 때문에 많은 사람들이 이용할 수록 더 빠르게 폰트를 이용할 수 있다

### font anti-aliasing
![image](https://user-images.githubusercontent.com/80051721/201001492-cd5a5cba-8bc7-4ece-b583-37e452ce840f.png)
```css
body {
    transform: rotate(0.04deg);
}
```
- anti-alising 은 픽셀의 각진 부분을 부드럽게 바꿔주는 기능이라고 볼 수 있는데, 맥에서는 기본적으로 font anti-aliasing이 적용되어 있지만 윈도우는 그렇지 않다
- transform 속성으로 적은 값의 rotation을 적용하면 anti-aliasing과 비슷한 효과를 줄 수 있다


## Flexbox
### flexbox 레이아웃
``` html
<body>
    <div class="flex-container">
        <div class="flex-item">1</div>
        <div style="flex-grow: 1;"></div> <!-- 가운데 공백 만들기 -->
        <div class="flex-item">2</div>
        <div class="flex-item">3</div>
    </div>
</body>
```
```css
.flex-container {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    flex-wrap: wrap;
}

.flex-item {
    width: 100%;
    height: 60px;
}
```
- 개체를 정렬하기 위한 방법 중 flexbox 가 있는데, 개체를 감싸는 부모 개체에 display: flex 속성을 적용하면 된다(IE11 이상부터 가용 가능)
    - justify-content: 자식 개체의 가로 정렬 옵션
    - align-items: 자식 개체의 세로 정렬 옵션
    - flex-direction: 정렬 방향
    - flex-wrap: 자식 개체 크기가 브라우저보다 클 경우 아래로 내려서 정렬할 지 여부(excel text-wrap과 같은 개념)
- flex-item 의 width: 100% 일 경우 각 개체가 균등한 너비로 브라우저를 가득 채운다
- flex-grow 는 가로 비율을 배수로 자동 조정해주는 속성인데, flex-grow를 가진 다른 개체와의 상대적 비율로 조정되며 위와 같이 혼자만 flex-grow를 가지고 있는 경우에는 나머지 개체의 너비를 제외한 남은 부분을 채우게 된다 > nav bar의 가운데 공백으로 사용 가능
- align-items의 옵션 개념
    - ![image](https://user-images.githubusercontent.com/80051721/201009725-e9081d16-9846-4126-8041-dda6966d60ad.png)


