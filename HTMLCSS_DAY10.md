# html_basic

## Bootstrap
### How to use BS
- Bootstrap: Front-end Component Library로 웹페이지에 필요한 Components 들을 모아 놓은 일종의 CSS 파일
- BS 홈페이지에 접속하여 start template 의 예제 코드를 새로운 HTML에 복붙하면 사용할 수 있다(head, body>script tag 정도가 필요하다)
    - (참고) bootstrap.min.css 와 js 파일을 같이 다운 받아 html 파일에 첨부해서 사용할 수도 있다(CSS 200kb 용량 차지)
- 이후 getbootstrap.com 사이트에 방문하여 원하는 UI components를 검색 후 코드 복붙하여 사용하면 된다

### BS Utility class
```html
<div class="container">정렬된 여백을 가진 박스</div>
<div class="mt-5">margin-top 5 level</div>
<div class="pb-5">padding-botton 5 level</div>
<div class="fs-3">font size 3 level</div>
<div class="text-center">text-align: center</div>
<div class="fw-bold">font weight bold</div>
```
- bootstrap에서 기 정의한 class 명을 이용해 디자인을 쉽게 할 수 있다 (기능/용도 별로 나누어 class 를 정의한 것을 utility class라고 한다)
- bootstrap에서는 margin, padding, font-size 등을 임의의 레벨로 나누어 적용하도록 되어 있다(pixel 단위 아님, 자세한 건 사이트에서 참조)
- 더 많은 정보는 사이트 utility tab에서 확인할 수 있다

## BS Responsive Web
### grid layout
```html
<div class="row">
    <div class="col-6">안녕</div>
    <div class="col-3">안녕</div>
    <div class="col-3">안녕</div>
</div>
```
- BS의 row, col component를 이용하면 쉽게 그리드 레이아웃을 만들 수 있다
- row 는 12 column을 기본 유닛으로 사용하고 있다(웹 디자인의 기본 가이드라인) > col-6은 6 columns 만큼의 크기를 차지하게 된다

### conditional prefix
```html
<div class="row">
  <div class="col-md-4"> 안녕 </div>
  <div class="col-md-4"> 안녕 </div>
  <div class="col-md-4"> 안녕 </div>
</div>
```
- BS에서는 조건을 달아주는 prefix를 붙여줄 수 있는데, 이를 이용해 반응형 웹페이지를 쉽게 만들 수 있다
    - col-md-4: medium container width(>=768px) 이상에서는 col-4 적용
    - text-lg-end: large container width(>=992px) 이상에서는 text-end 적용 등으로 사용할 수 있다
- 사이즈 정보는 사이트에서 참고할 수 있다
- 대규모 웹페이지/회사에서는 조건부 클래스를 직접 만들어 사용하는 경우가 많다

