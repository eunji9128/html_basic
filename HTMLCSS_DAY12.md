# html_basic

## shadow DOM
### DOM
![image](https://user-images.githubusercontent.com/80051721/204745859-4149a2c7-bdb6-42d9-a42c-f388d67e95ac.png)
![image](https://user-images.githubusercontent.com/80051721/204746000-1b9ca302-1811-463e-8bca-231c3cb3ab42.png)
- DOM(Document Object Model): 마크업 문서에서 나타나는 여러가지 요소들과 텍스트 문자열을 나타내는 노드들의 트리같은 구조로, 웹 문서의 경우 HTML fragment가 있다
- 위 HTML fragment는 아래 DOM 구조를 생성한다

### shadow DOM
![image](https://user-images.githubusercontent.com/80051721/204746963-701b7de5-bb61-4cdf-83bc-d856233f1dea.png)
- shadow DOM은 숨겨진 HTML 요소 트리를 의미한다

```html
<input type="file">
<input type="placeholder">
<input type="range">
<progress>
```
- 위와 같은 태그들은 생성 시 숨겨진 다중 태그가 하나의 태그로 생성되는 형태이다 = shadow DOM (ex. input type=file은 button + span tag로 이루어져 있다)
- 개발자 도구 설정에서 shadow DOM을 표시할 수 있도록 변경할 수 있다 (show user agent shadow DOM)

### shadow DOM 스타일 변경
![image](https://user-images.githubusercontent.com/80051721/204747629-49532a37-76d9-4c5a-a0b8-5967240d2659.png)
```css
input::-webkit-file-upload-button {
    background: skyblue;
    border: none;
    padding: 5px;
    color: white;
}
```
- 스타일을 변경하기 위해서는 해당 개체의 id, class 등의 정보가 필요한데, 이 역할을 해주는 게 pseudo 라벨이다
- 태그의 pseudo 라벨 값을 찾아 css에서 pseudo-element 문법으로 스타일링 해줄 수 있다
![image](https://user-images.githubusercontent.com/80051721/204748195-30946a4e-bf61-45ba-bc97-bc95b43550fc.png)
- pseudo 라벨이 따로 없는 태그의 경우 개발자 도구를 이용해 user agent stylesheet 셀렉터를 그대로 복사해 css 파일에 넣고 덮어씌울 수 있다

### range, progress bar
```css
input[type=range] {
    appearance: none;
}

input[type=range]::-webkit-slider-thumb {
    appearance: none;
    background: skyblue;
    width: 20px;
    height: 20px;
}
```
- user agent stylesheet 셀렉터를 가져와 스타일링을 해주어도 기본 브라우저 스타일이 적용되어 있는 경우에는 변경된 스타일이 적용되지 않는다
- 변경을 위해서는 appearance: none 속성으로 디폴트 브라우저 스타일을 보이지 않게 해준다
    - (참고) 이 때 element selector 뿐만 아니라 태그 스타일에도 적용해줘야 하므로, 모든 기본 스타일이 안 보이게 된다
- 직접 스타일 적용하는 것보다 구글링을 통해 스타일을 적용해 보는 것이 도움이 된다 (추후 업데이트)
