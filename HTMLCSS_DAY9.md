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


