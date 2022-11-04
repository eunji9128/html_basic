# html_basic

## Form Layout 예제
### Layout 구축
- Layout 구축 시에는 박스 단위로 나누어 구성을 시작한다
- ![image](https://user-images.githubusercontent.com/80051721/199921022-c7f88bbe-5a0e-42e9-b9aa-87c3d6dc34ff.png)
- class를 사용할 때는 재활용을 고려하여 작성하는 습관을 들여야 개발의 효율과 가독성이 높아진다
    - div 개체마다 새로운 class name을 부여하기 보다, w-100, w-50, form-input, form-long 등 재활용하여 사용할 수 있는 디자인 요소를 class로 만들어야 한다
    - 재활용 시 필요에 따라 class="form-input form-long" 등 여러 class의 속성을 가져다 쓸 수도 있다
    - 재활용이 가능하려면 비대칭 구조의 디자인보다는 대칭 구조의 디자인을 사용하면 좋다 > first name, last name 개체에 padding or margin 값을 비대칭으로 주려 한다면 같은 class style을 사용할 수 없을 것이다

### Label tag
```html
<body>
    <form>
        <input id="Sub" type="checkbox">
        <label for="Sub">Subscribe</label>
    </form>
</body>
```
- Form Layout 예제에서 check-box input 오른편에 Subscribe 라는 text를 추가해줄 때, span tag 대신 label tag를 사용할 수 있다
- Label tag의 특징은 label for의 값과 input check-box 의 id가 같으면 브라우저에서 'Subscribe' 라는 text를 클릭해도 check-box activate/deactivate 해줄 수 있다

### Table의 활용
## table, tr, td
```html
    <body>
        <div>
            <table>
                <thead>
                    <tr>
                        <th>1</th>
                        <td>2</td>
                        <td>3</td>
                    </tr>
                </thead>
                <tbody>
                    <tr>
                        <th>1</th>
                        <td>2</td>
                        <td>3</td>
                    </tr>
                </tbody>
            </table>
        </div>
    </body>
```
```css
td, th {
    border: 1px solid black;
}

table {
    border-collapse: collapse;
}
```
- table tag 안에 tr(=table row), td(=table data =col) 순서대로 작성하면 table 구조를 만들 수 있다
    - (참고) th 는 td의 bold font
- table 구조는 thead, tbody tag로 나눌 수 있는데 기능적으로 차이는 없고, 가독성 개선을 위한 태그로 사용할 수 있다
- td, th에 border 디자인을 적용하면 td 사이에 공백이 있음을 볼 수 있는데, border-collapse: collapse 속성으로 공백을 없애줄 수 있다(table tag CSS reset으로 지정해놓으면 편함)

### vertical align
```css
td, th {
    vertical-align: middle;
}
```
- table 내 contents 상하 정렬을 할 때 vertical-align 속성을 사용할 수 있다
    - (참고) table 내에서는 top, middle, bottom 만 사용 가능

```html
<body>
    <p>
        <span style="font-size: 50px">Greetings</span>
        <span style="font-size: 20px; vertical-align: top">안녕</span>
</body>
```
- vertical-align은 inline, inline-block 요소들이 나란히 배치되어 있을 때 상하 정렬을 맞추기 위해 사용할 수 있다
    - (참고) span tag는 대표적인 inline 속성을 가진 tag
- inline 요소 정렬 시에는 top, middle, bottom 외에도 super, sub나 px 단위로도 사용할 수 있다

### div table
``` html
<body>
    <div style="display: table">
        <div style="display: table-row">
            <div style="display: table-cell">1</div>
            <div style="display: table-cell">2</div>
            <div style="display: table-cell">3</div>
        </div>
    </div>
</body>
```
- 위처럼 style 속성을 table로 바꾸어주면 div tag로도 table을 만들 수 있다 > 하지만 table tag가 편하므로 거의 안 씀

### td merge & nth-child selector
``` html
<body>
    <div>
        <table class="cart-table">
            <tr>
                <td>1</td>
                <td>1</td>
            </tr>
            <tr>
                <td colspan="2">2</td>
            </tr>
    </div>
</body>
```
```css
.cart-table td:nth-child(2) {
    width: 400px;
}
```
- merged td를 만들기 위해서는 colspan="" 속성을 이용하면 된다
- 특정 td 셀렉터는 td:nth-chile(n) 속성을 이용하면 된다
- n 자리에 숫자는 특정 위치 td, even은 모든 짝수 번째 td, odd는 홀수
- n 자리에 3n+0 이라고 쓰면 3, 6, 9 등 3의 배수 번째 td만 셀렉트, 3n+1 은 4, 7, 10...
