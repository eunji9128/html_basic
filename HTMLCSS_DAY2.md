# html_basic

## 웹레이아웃의 기초
### div 박스 디자인
```html
<body>
    <div class="box">
        <p>Hi, I am junior front-end developer</p>
    </div>
</body>
```
```css
.box {
    width: 200px;
    background: cadetblue;
    margin: 10px;
    padding: 40px;
    border: 4px solid black;
    border-radius: 5px;
    /* display: block; */
    margin-left: auto;
    margin-right: auto;
    font-size: 10px;
    box-shadow: 5px 5px 5px black;
}
```
- div 는 기본적으로는 상하 길이가 없는 선을 만들어 준다
- 이미지 가운데 정렬 시 사용했던 속성 중 display: block은 div에 기본적으로 내포되어 있어 적용하지 않아도 된다
    - (참고) div, p, h 태그 모두 display: block 속성을 가지고 있는데, 이 속성은 가로 행을 전부 차지한다는 의미
- div 태그에서 font-size 지정을 해줘도 자식인 p 태그에 적용된다 > 일부 스타일은 inherit(상속) 되기 때문(font-family, font-size, color 등)


### 기초 레이아웃
layout image
```html
<body>
    <div class="container">
        <div class="header"></div>
        <div class="left-menu"></div>
        <div class="right-content"></div>
        <div class="footer"></div>
    </div>
</body>
```
- 전체 레이아웃을 감싸는 contaniner(혹은 wrapper라고 부름)를 만들어 주면 레이아웃 관리가 편하다

```css
.container {
    width: 800px;
}

.header {
    width: 100%;
    height: 50px;
    background-color: aquamarine;
}

.left-menu {
    width: 20%;
    height: 400px;
    background-color: cornflowerblue;
    float: left;
}

.right-content {
    width: 80%;
    height: 400px;
    background-color: coral;
    float: left;
}

.footer {
    width: 100%;
    height: 100px;
    background-color: gray;
    clear: both;
}
```
- width 는 부모(여기서는 container) 사이즈의 비율 %로 적용할 수 있다
- div는 기본적으로 display: block 즉, 가로 행을 전부 차지하고 있는 속성이므로 left-menu와 right-content를 같은 행에 정렬하기 위해서는 float 정렬이 필요하다
    - (참고) float left는 왼쪽 정렬, float right는 오른쪽 정렬
- left-menu 만 float 정렬 시 right-content는 left-menu와 겹쳐 정렬 되므로(left-menu가 떠 있으므로 right-content가 아래로 위치함) 둘 다 적용해주어야 한다
- footer도 마찬가지로 left-menu, right-content가 floating 상태 이므로 두 div의 아래, header의 바로 다음에 붙어 정렬되므로 clear: both 를 통해 float 속성의 영향을 무시할 수 있도록 해주어야 한다
    - (참고) clear: left는 float: left 무시, clear: right 는 float: right 무시


### Inline-block 활용
```css
.container {
    width: 800px;
}

.header {
    width: 100%;
    height: 50px;
    background-color: aquamarine;
}

.left-menu {
    width: 20%;
    height: 400px;
    background-color: cornflowerblue;
    /* float: left; */
    display: inline-block;
}

.right-content {
    width: 80%;
    height: 400px;
    background-color: coral;
    /* float: left; */
    display: inline-block;
}

.footer {
    width: 100%;
    height: 100px;
    background-color: gray;
    /* clear: both; */
}
```
```html
<body>
    <div class="container">
        <div class="header"></div>
        <div class="left-menu"></div><div class="right-content"></div>
        <div class="footer"></div>
    </div>
</body>
```
- display: inline-block 은 박스 사이즈만큼만 가로 행을 차지하게 해주는 속성이다
- inline-block 사용 시에는 left-menu와 right-content 사이에 띄어쓰기가 있을 경우 공간이 모자라 right-content가 아래로 내려오므로, 띄어 쓰기 없이 붙여 코드를 써주어야 한다
    - (참고) font-size를 0px로 하거나 주석을 활용하면 줄바꿈을 할 수도 있지만 불편하다
- right-content or left-menu에 글씨를 적으면 글자의 baseline에 맞추어 옆 박스가 정렬되어 두 박스 간의 정렬이 틀어지므로, 한 쪽에 vertical-align: top 속성을 추가해주어야 한다.
    - (참고) 글자의 baseline은 줄노트의 줄과 같은 위치(글자 하단에 맞추어 위치)


