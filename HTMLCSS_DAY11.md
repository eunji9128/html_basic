# html_basic

## Pseudo Element
### Pseudo Class vs. Element
```css
/* Pseudo-class */
.text:hover {
    color: red; 
}

/* Pseudo-element */
.text::first-letter {
    color: blue;
}

.text::first-line {
    color: blue;
}

.text::after {
    content: '';
    display: block;
    clear: both;
}

.text::before {
    content: 'Hi';
    color: blue;
}
```
- Pseudo class: 특정 요소가 다른 상태일 때 지정 스타일 적용해줌
- Pseudo element: 특정 html 요소의 안쪽 일부만 지정 스타일 적용해줌
    1. Pseudo-element를 선택하려면 콜론 2개를 붙여준다
    2. ::first-letter 는 안에 있는 글자 중 첫번째 글자만 스타일 적용
    3. ::first-line 은 안에 있는 글자 중 첫 줄만 스타일 적용
    4. ::after 는 내부의 맨 마지막 부분에 내용을 추가 + 스타일 적용
        - (참고) 위와 같이 clear block으로 활용할 수 있다
    5. ::before 는 내부의 맨 첫 부분에 내용을 추가 + 스타일 적용

### 숨겨진 스타일 변경
```html
<input type="file" class="input-file">
```
```css
.input-file::file-selector-button {
    background: skyblue;
    border: none;
    padding: 20px;
}

.input-file::file-selector-button:hover {
    background: blue;
}
```
- file selector button(input type="file")은 자동으로 버튼+문자 개체가 생성되는데, 이는 자동 생성되어 숨겨져 있는 개체이다. 
- 이런 개체에도 Pseudo-element 를 이용해 스타일을 지정해줄 수 있다
- 위와 같이 요소가 숨겨진 개체들은 shadow-DOM 에서 추가로 학습 예정